# Agora-access-token-generator
Simple laravel package to generate access token for RTC agora
## Installation, and Usage Instructions

This package allows you to generate Agora access token using laravel.

```cli
composer require yasserbelhimer/agora-access-token-generator
```
First at all generate your APP_ID and APP_CERTIFICATE from agora dashboard

Set  AGORA_APP_ID and AGORA_APP_CERTIFICATE in the .env  
```env
AGORA_APP_ID= your agora app id
AGORA_APP_CERTIFICATE= your agora certificate token
```
Once installed you can do stuff like this:

## To know more about arguments and parametres check Agora documentation.

## Generate RTC token:

To generate rtc token use the static methode buildTokenWithUserAccount() in RtcTokenBuilder class.
```php
    $appID = env('AGORA_APP_ID');
    $appCertificate = env('AGORA_APP_CERTIFICATE');

    $channelName = $request->channelName;
    $user = Auth::user()->name;
    $role = RtcTokenBuilder::RoleAttendee;
    $expireTimeInSeconds = 3600;
    $currentTimestamp = now()->getTimestamp();
    $privilegeExpiredTs = $currentTimestamp + $expireTimeInSeconds;

    $rtcToken = RtcTokenBuilder::buildTokenWithUserAccount($appID, $appCertificate, $channelName, $user, $role, $privilegeExpiredTs);

```
