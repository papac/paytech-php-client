[![Coverage Status](https://coveralls.io/repos/github/PapiHack/paytech-php-client/badge.svg?branch=master)](https://coveralls.io/github/PapiHack/paytech-php-client?branch=master)
![Issues](https://img.shields.io/github/issues/PapiHack/paytech-php-client)
![PR](https://img.shields.io/github/issues-pr/PapiHack/paytech-php-client)
[![Latest Stable Version](https://poser.pugx.org/papiHack/paytech-php-client/v)](//packagist.org/packages/papiHack/paytech-php-client) [![Total Downloads](https://poser.pugx.org/papiHack/paytech-php-client/downloads)](//packagist.org/packages/papiHack/paytech-php-client) [![Latest Unstable Version](https://poser.pugx.org/papiHack/paytech-php-client/v/unstable)](//packagist.org/packages/papiHack/paytech-php-client) [![License](https://poser.pugx.org/papiHack/paytech-php-client/license)](//packagist.org/packages/papiHack/paytech-php-client)
[![Open Source Love png1](https://badges.frapsoft.com/os/v1/open-source.png?v=103)](https://github.com/ellerbrock/open-source-badges/)

# PayTech - PHP API Client (installable with Composer)

This is a simple `SDK Client` or `API Client` for `PayTech Online Payment Gateway`.

Check out [PayTech SN Website](https://paytech.sn).

## How to use it

First of all, install the package or library via composer

- `composer require papihack/paytech-php-client`

After that, setup the API config with your parameters like this :

```php
    \PayTech\Config::setApiKey('your_api_key');
    \PayTech\Config::setApiSecret('your_api_secret');

    /*
     * you can set one of this two following parameters
     * Notice : LiveMode === Production mode
    */

    \PayTech\Config::setTestMode(true);
    \PayTech\Config::setLiveMode(false);

    /*
     * The PayTech\Enums\Currency class defined authorized currencies
     * You can change XOF (in the following example) by USD, CAD, GBP or MAD
    */

    \PayTech\Config::setCurrency(\PayTech\Enums\Currency::XOF);

    /* !!! Note that if you decide to set the ipn_url, it must be in https !!! */

    \PayTech\Config::setIpnUrl('your_ipn_url');
    \PayTech\Config::setSuccessUrl('your_success_url');
    \PayTech\Config::setCanceUrl('your_cancel_url');

    /*
     * if you want the mobile success or cancel page, you can set
     * the following parameter
    */

    \PayTech\Config::setIsMobile(true);
```

Then you can proceed with :

```php
    $article_price = 15000;
    $article = new \PayTech\Invoice\InvoiceItem('article_name', $article_price, 'command_name', 'ref_command');

    /* Make the payment request demand to the API */

    \PayTech\PayTech::send($article);

    /* Get the API Response */

    $response = [
        'success'      => \PayTech\ApiResponse::getSuccess(),
        'errors'       => \PayTech\ApiResponse::getErrors(),
        'token'        => \PayTech\ApiResponse::getToken(),
        'redirect_url' => \PayTech\ApiResponse::getRedirectUrl(),
    ];
```

After that, if you have a success response, you can redirect your user to the `$response['redirect_url']` so that he can make the payment.  
You can process the response as you wish by directly manipulating `\PayTech\ApiResponse`.

## TODO

- tests: cover all use cases
- get the support team at [paytech.sn](https://paytech.sn) to clarify certain points
- use mock instead of hitting real endpoint

## Contributing

Feel free to make a PR or posting an issue 😃

Oh, one more thing, please do not forget to put a description when you make your PR 🙂

## Contributors

- <a href="https://itdev.herokuapp.com" alt="The IT DEV">M.B.C.M</a>
[![](https://img.shields.io/twitter/follow/the_it_dev?style=social)](https://twitter.com/the_it_dev)
