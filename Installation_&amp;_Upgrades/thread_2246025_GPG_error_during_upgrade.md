---
title: "GPG error during upgrade"
date: 2014-09-27
forum: Installation &amp; Upgrades
---

### Post by sridhar4 on 2014-09-27
Hi,

I have some broken packages and so did a 
apt-get update.
However, it gives me the following error:
```
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E07F5B89A690089
```

I checked further and looks like that that particular key comes from an MIT site, that is blocked here (I am in China).  Can I get the key in some other way?  Or is there any other work around other than using proxy / VPN servers etc?

Thanks and please let me know if you need any additional details.

---

### Post by oldos2er on 2014-09-28
You can get the key from keyserver.ubuntu.com with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E07F5B89A690089
``` Hope this works for you.

---

### Post by Old_Grey_Wolf on 2014-09-28
Try entering these commands one at a time in the terminal to get the key ```
gpg --keyserver keyserver.ubuntu.com --recv 3E07F5B89A690089
gpg --export --armor 3E07F5B89A690089 | sudo apt-key add -
```

---

