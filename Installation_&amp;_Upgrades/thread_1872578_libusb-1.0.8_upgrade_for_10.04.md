---
title: "libusb-1.0.8 upgrade for 10.04"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by Gremlyn1 on 2011-10-30
I downloaded .deb's for Heimdall (Samsung mobile device interface program) and the installer tells me I need to have libusb-1.0.8 but from my quick digging it seems that Ubuntu 10.04 LTS has been frozen at 1.0.6 :(

I went to the libusb page and downloaded the source to compile myself, but after doing so it seems that the system still says 1.0.6 is what I am using. I can't remove 1.0.6 without removing a bunch of other packages that I do not want to remove! Is there any way for me to upgrade the libusb version and why doesn't 10.04 get the 1.0.8 upgrade? I thought the LTS meant it got long term support???

---

### Post by thepearson on 2011-11-06
Hey; 

This is how I got around this issue:

Have a look at this PPA here: 
[https://launchpad.net/~modycz/+archive/heimdall](https://launchpad.net/~modycz/+archive/heimdall)

You can install heimdall 1.1.1 on 10.04 by doing the following on the console:

```

sudo add-apt-repository ppa:modycz/heimdall

sudo apt-get update

sudo apt-get install heimdall

```

This will install Heimdall-1.1.1-1~lucid2 and libusb-2:1.0.8-2~lucid1

If you require Heimdall 1.3.1 (like i did) you should be able to just download the .deb package from [https://github.com/Benjamin-Dobell/Heimdall/downloads]("https://github.com/Benjamin-Dobell/Heimdall/downloads") and just do a:

```


sudo dpkg -i heimdall_1.3.1_i386.deb


```

I hope this helps.

---

