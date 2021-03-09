# Generating TOTP codes in Postman

I love postman for all sorts of things and have extensively used Postman for generating JWTs, and thought there must be a pure javascript implementation of TOTP for automating the signing to pages that have 2FA as part of a login journey.
So I found this page:
https://gist.github.com/ptrstpp950/42660823675f6bf2f2d2f1503663553a

And minified it to reduce space.

## Download 
To download it to global variables:


### GET: https://raw.githubusercontent.com/plambrechtsen/postman-totp/TOTP.js
### Tests:
```
pm.test("Status code is 200", function () {
  pm.response.to.have.status(200);
});

// Set the Global TOTP variable
pm.globals.set("TOTP", responseBody);
```

## Main TOTP Pre-request script.

```
eval(pm.globals.get("TOTP"));
var totpObj = new TOTP();
var otp = totpObj.getOTP("YOUR_PASSWORD_HERE");
pm.environment.set("OTP", otp);
```
 