---
title: "Getting error during apt-get update in edgy"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by nbhaskar on 2007-03-03
When I run sudo apt-get update I get the following error in Edgy, can somebody help me rectify the error?, please check my signature for my machine configuration if you think it is relevant.

```
W: GPG error: http://easyubuntu.cafuego.net main Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 580E2519969F3F57
W: You may want to run apt-get update to correct these problems

```

thanks in advance.
B :confused:

---

### Post by ffxr on 2007-03-03
run this in Terminal

```
wget http://easyubuntu.cafuego.net/969F3F57.gpg -O- | sudo apt-key add -
```

if you go the address of the repo e.g in this case : [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) , it will tell u how to authenicate the package

---

### Post by nbhaskar on 2007-03-03
thanks lot for the info ffxr.

B.

---

