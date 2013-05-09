# MaxMind API #

MaxMind is an online fraud prevention service. Its API allows systems to verify the legitamacy of customer information. This is useful in determining if whether or not to access payment from such a customer.

This API implements the following API commands:

- **ccv2r** minFraud
- **ipauth_http** Proxy Detection
- **phone_id_http** Phone Identification
- **telephone_http** Telephone Verification

## Requirements ##

* PHP 5.1.3 or greater

### Using the API ###

Determine the legitimacy of customer data:

```php
<?php
require_once "maxmind_api.php";
require_once "commands/maxmind_ccv2r.php";

$license_key = "YOUR_MAXMIND_API_KEY";

$api = new MaxmindApi();
$ccv2r = new MaxmindCcv2r($api);

$customer = array(
	'i' => $_SERVER['REMOTE_ADDR'],
	'city' => "Los Angeles",
	'region' => "CA",
	'postal' => "90210",
	'country' => "US",
	'license_key' => $license_key	
);

print_r($ccv2r->request($customer)->response());
?>
```