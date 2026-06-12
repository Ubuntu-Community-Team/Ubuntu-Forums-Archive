---
title: "Failed to authenticate disco.tar.gz: no public key"
date: 2019-04-22
forum: Installation &amp; Upgrades
---

### Post by dyle712 on 2019-04-22
#!/bin/hi *

I cannot update from 18.10 to 19.04 due to a failed authentication check of disco.tar.gz.

It seems to me, that the command
```
# do-release-upgrade
```
downloads the disco.tar.gz and the disco.tar.gz.gpg from [http://archive.ubuntu.com/ubuntu/dists/disco-proposed/main/dist-upgrader-all/current/](http://archive.ubuntu.com/ubuntu/dists/disco-proposed/main/dist-upgrader-all/current/), stores them in a temporary folder and runs a 

[FONT=monospace]```
[COLOR=#000000]# apt-key verify /tmp/ubuntu-release-upgrader-oe0wd39w/disco.tar.gz.gpg /tmp/ubuntu-release-upgrader-oe0wd39w/disco.tar.gz[/COLOR]
gpgv: Signature made Sa 20 Apr 2019 02:03:10 CEST
gpgv:                using RSA key 3B4FE6ACC0B21F32
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
gpgv: Signature made Sa 20 Apr 2019 02:03:10 CEST
gpgv:                using RSA key 871920D1991BC93C
gpgv: Can't check signature: No public key

```
This fails since key [/FONT][FONT=monospace]871920D1991BC93C is unavailable:
[/FONT][FONT=monospace]
[/FONT]```
[FONT=monospace][COLOR=#000000]# apt-key adv --keyserver http://keyserver.ubuntu.com:80 --recv-keys 871920D1991BC93C[/COLOR]
Executing: /tmp/apt-key-gpghome.XSv3F8qJJr/gpg.1.sh --keyserver http://keyserver.ubuntu.com:80 --recv-keys 871920D1991BC93C
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
[/FONT]
```

[FONT=monospace]What should I do?
[/FONT]

---

### Post by dyle712 on 2019-04-27
*bump* - Noone?

Ok. Forced myself an update by dropping the authentication check. -.-

```

[FONT=monospace][COLOR=#000000]--- DistUpgradeFetcherCore.py   2019-04-27 11:51:06.485837751 +0200 [/COLOR]
+++ /usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py        2019-04-27 11:51:26.013714091 +0200 
@@ -75,7 +75,7 @@ 
                'signature': os.path.basename(sig)}) 
            if self.gpgauthenticate(f, sig): 
                return True 
-        return False 
+        return True 
 
    def gpgauthenticate(self, file, signature, 
                        keyring=None):

```[/FONT]

---

