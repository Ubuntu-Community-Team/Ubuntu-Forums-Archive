---
title: "Uninstall 10.10 for 10.04"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by MrLeprechawn on 2010-12-21
I dual booted my Dell Laptop with Windows 7 today using a usb stick. I installed it but I'm having problems connecting to the wireless network so I want to install 10.04 instead. I have never used any form of Linux before today so I'm a bit clueless. I read there werent wireless problems in the stable 10.04 so I just want to use that instead, unless anyone has any links to drivers that might work. I have tried all the ones suggested in forums/support and downloaded the drivers in the system - download drivers part. There seems to be a lot of errors when I try download them. My laptop is a Dell Inspiron 1564 core i3 in case that helps.
Thanks, Paul.

---

### Post by coffeecat on 2010-12-21
Without finding out which your wireless chipset is, it would be unwise to assume that 10.04 is any better or worse than 10.10. If you have read that there are not wireless problems in 10.04, then you have read something wildly misleading. Again, it all depends on the particular wireless chipset. Some work just fine, some need a little bit of work from the user and some can be downright difficult.

Since you have a Dell it is possible (though not definite) that you have Broadcom wireless. Have a look here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

As suggested there, try the following in a terminal:

```
lspci -vvnn | grep 14e4
```If you get no output, then you do not have Broadcom. If you do get output, simply follow the directions in that link to get it working.

If you do not get any output, post the output of this command:

```
sudo lshw -C network
```That will tell us about your wireless device.

---

### Post by MrLeprechawn on 2010-12-21
When I enter  
```
lspci -vvnn | grep 14e4
```I get this
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```Also when I try get the additional drivers in system - administration I get the error
```
SystemError: installArchives() failed
```

---

### Post by MrLeprechawn on 2010-12-21
SOLVED
I messed around with it a bit more and the wireless driver finally worked :D

---

### Post by coffeecat on 2010-12-22
Glad it's working.

---

### Post by sarang on 2010-12-22
> **coffeecat said:**
> Without finding out which your wireless chipset is, it would be unwise to assume that 10.04 is any better or worse than 10.10. 

This is true in general, but just for completeness, I'd like to add that the Intel iwlagn wireless driver has issues in Maverick 10.10 but not in Lucid 10.04. This is a known issue and is mentioned in the Maverick release notes as well. Briefly, network performance over all kinds of wifi (A/B/G/N) degrades to unusable levels over time, unless 'N' is disabled. This is the reason I am not upgrading my Lucid laptop till the bug is resolved.

---

