---
title: NoProvider2Push
---

In it's own words
> NoProvider2Push is a UnifiedPush distributor able to provide push notifications without a push provider. For this, it needs a static address even with the roaming. It is achievable with a custom network such as a VPN (eg. wireguard) or the yggdrasil network.

* License: Apache2
* Sources: <https://github.com/NoProvider2Push/android>
* Server: -
* Download for Android:
  * [F-Droid](https://f-droid.org/packages/com.flyingpanda.noprovider2push/) ⚠️  **You need to add the** [unifiedpush repo](https://repo.unifiedpush.org) **first!** ⚠️

## Requirements

* A Static IP on your phone. This is achievable by using a VPN (such as wireguard) or a meshing network like Yggdrasil.
* A Proxy to reach your phone from Internet. There is not known public proxy at this moment, see [Self Hosting](#self-hosting) to host your own.

## Setting Up

* Install the application.
* Set you static IP and your proxy in the settings.
* You're ready!

## Self Hosting

If you are self-hosting a proxy, you can use one of the following.

### Nginx

```nginx
location ~ ^/proxy/(?<address>[^:]+):(?<port>[^/]+)/(.*)$ {
    proxy_pass                 http://$address:51515/$3;
    client_max_body_size        50M;
    # Force https
    if ($scheme = http) {
        rewrite ^ https://$server_name$request_uri? permanent;
     }
}
```

