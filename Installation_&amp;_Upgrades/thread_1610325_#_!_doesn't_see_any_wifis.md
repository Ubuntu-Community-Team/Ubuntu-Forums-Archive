---
title: "# ! doesn't see any wifis"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by Irene89 on 2010-10-31
Hi, I am new. Yesterday I installed Crunchbang, the installation seems to work well. When I reboot the system it doesn't see any wifis ( and I know there are more than one in my zone). In the bottom right I see a cross on the network's icon. My boyfriend ran 'ifconfig -a' and there were only two devices "lo" and "pan0" and next to pan0 there was written "ethernet". He tried connecting with an ethernet cable so that I could copy/paste some output of commands but wasn't able to. He did:


$ sudo ifconfig pan0 up
$ sudo dhclient pan0

but it wouldn't connect.

Also, regarding wifi, he told me it was strange that running
$ sudo modprobe wlan0
gave an error like "FATAL: module wlan0 not found". Though he could
modprobe a module which seemed specific to my atheros card (ath9k), no
wifi device would appear in ifconfig.

We did an md5 check on the .iso file which resulted ok and also a test
on the usb-pen (on boot, selected from the menu "Check" or something
similar) and said it was ok also.

BTW *all* of the above happened both with the Lite and Standard #!,
32-bit.

My netbook is an Eeepc, I forget the number at the moment, but it's
recent (few months). I had lubuntu on it till yesterday and never had a
problem.

Any ideas?

thanks,
Irene

---

### Post by goinglinux on 2010-10-31
I have not used crunchbang (other than to try it once) but it is quite possible that it does not have the right driver for the atheros card in your eeePC. 

If you don't mind me asking, why did you switch from Ubuntu?

---

### Post by uRock on 2010-10-31
Are you using the Ubuntu or Debian version?

---

### Post by Irene89 on 2010-10-31
> **goinglinux said:**
> 
If you don't mind me asking, why did you switch from Ubuntu?

I would like to try #! because I want to use a distribution a bit less userfriendly than the others I have tried and I want to see if #! is faster than lubuntu. Perhaps also because I'm a newbie of linux and I like change distros only for the graphic aspect.



> **uRock said:**
> Are you using the Ubuntu or Debian version?
The ubuntu version.

---

### Post by uRock on 2010-10-31
I have only ever used Crunchbang in a VM. Do you have this same problem with ubuntu 10.04?

---

### Post by Irene89 on 2010-10-31
I have controlled the number of my eeepc and it is the 1005PE. On it I have only tried the last version of lubuntu and there was no problem.

---

### Post by snowpine on 2010-11-02
> **Irene89 said:**
> I have controlled the number of my eeepc and it is the 1005PE. On it I have only tried the last version of lubuntu and there was no problem.

Latest version of Lubuntu is 18 months newer than #! 9.04 and will have better support for newer hardware released during that time. The EEE 1005PE hit the market in Dec. 2009 (3 months *after* the 9.04 release).

---

