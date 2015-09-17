# credit_card_validator
This is a jquery credit card validator from jqueryscript.net

A simple jQuery plugin to check and display the credit card type as the user types, and to provide Bootstrap validation classes for Luhn check once the correct length has been verified.

How to use it:

1. Include the necessary jQuery library and Bootstrap's CSS in the web page.

<script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
2
<link rel="stylesheet" href="//netdna.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
2. Include the jQuery creditCardValidator plugin after jQuery library.

<script src="jquery.creditCardValidator.js"></script>
3. Create a text field for credit card input.

<input id="checkout_card_number" class="input-text form-control" type="text" size="19" maxlength="19" data-stripe="number" placeholder="1234 5678 9012 3456">
2
<span class="payment-errors required"></span>
4. The CSS to add a default credit card image into the credit card input.

1
#checkout_card_number {
2
  background-image: url(cards.png);
3
  background-position: 3px 3px;
4
  background-size: 40px 252px;
5
  background-repeat: no-repeat;
6
  padding-left: 48px;
7
}
5. The Javascript.

var $cardinput = $('#checkout_card_number');
$('#checkout_card_number').vali<a href="http://www.jqueryscript.net/time-clock/">date</a>CreditCard(function(result)
{
 
if (result.card_type != null)
{

switch (result.card_type.name)
{
case "visa":
$cardinput.css('background-position', '3px -34px');
$cardinput.addClass('card_visa');
break;
 
case "visa_electron":
$cardinput.css('background-position', '3px -72px');
$cardinput.addClass('card_visa_electron');
break;
 
case "mastercard":
$cardinput.css('background-position', '3px -110px');
$cardinput.addClass('card_mastercard');
break;
 
case "maestro":
$cardinput.css('background-position', '3px -148px');
$cardinput.addClass('card_maestro');
break;
 
case "discover":
$cardinput.css('background-position', '3px -186px');
$cardinput.addClass('card_discover');
break;
 
case "amex":
$cardinput.css('background-position', '3px -223px');
$cardinput.addClass('card_amex');
break;
 
default:
$cardinput.css('background-position', '3px 3px');
break;
}
} else {
$cardinput.css('background-position', '3px 3px');
}
 
// Check for valid card numbers - only show validation checks for invalid Luhn when length is correct so as not to confuse user as they type.
if (result.length_valid || $cardinput.val().length > 16)
{
if (result.luhn_valid) {
$cardinput.parent().removeClass('has-error').addClass('has-success');
} else {
$cardinput.parent().removeClass('has-success').addClass('has-error');
}
} else {
$cardinput.parent().removeClass('has-success').removeClass('has-error');
}
});
