# payment_tracking_instructions
A tutorial put up by Caiwei

# HTML & JS
## Implementation of Google Tag Manager inside html
make sure you have the google tag manager code set up inside your head tag and body tag. 

### Inside Head Tag
<!-- Google Tag Manager -->
```html
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-XXXXXX');</script>
<!-- End Google Tag Manager -->
```
### Inside Body Tag (as high as possible)
```html
<!-- Google Tag Manager (noscript) -->
<noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTM-KMFQDMG"
height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
<!-- End Google Tag Manager (noscript) -->
```
## HTML For Payment Example
1. We will create a input field (dropdown, number box, checkbox all ok), as long as the id of the element that contains the value is "amount". 
2. Then we will create a button that will trigger a function onclick. This function is called submitEvent(). 
3. Inside the function, I added some console calls to test out whether it is working. 
4. We will use the `window.dataLayer` to push event, and other variables to google tag manager. 
5. record your event name (e.g. `registrationComplete` in this case)
6. record the donation amount, and save it as a number instead of a string. (`Number(variable_name)`). Call this variable `donationAmount`
7. Name the `action` variable `donation`

```html
<script> 
function submitEvent(){
console.log("cool")
var amount = document.getElementById('amount').value;
console.log(amount);
  window.dataLayer = window.dataLayer || [];
 window.dataLayer.push({
 'event': 'registrationComplete',
'donationAmount':Number(amount),
 'action': 'donation'
 });
console.log(window.dataLayer)
}
</script>
  <label for="amount">Dollar Amount:</label>
  <input type="number" min="0" id="amount" name="amount"><br><br>
  <button id = "payButton" onclick=submitEvent()>Make Payment</button>
```

# Google Tag Manager
## Setting up variables
We have two variables we want to record: donationAmount and action. 
We will create one variable in Google Tag Manager for each. 

## Setting up custom event trigger
