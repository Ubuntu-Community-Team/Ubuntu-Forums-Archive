---
title: "[SOLVED] Need help installing ndiswrapper"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by 11zac11 on 2008-09-30
After installing ubuntu 8.04 I thought finely a OS I can life with, I get everything working apart form one thing, my WLAN card.
i have a Atheros 802.11 wireless card (so ubuntu says) and cant get it to work. After hunting for some time i found that by installing 'ndiswrapper' i could then get windows drivers to work. Only thing is im completely new to Linux and I cant work out how to install it :(. If someone can help me i would be very great full. Thank you all very much i hope someone gets back soon. Thanks all :)

---

### Post by Pumalite on 2008-09-30
Maybe these links can help>
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=618596&page=2](http://ubuntuforums.org/showthread.php?t=618596&page=2)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
[http://ubuntuforums.org/showthread.php?t=612065](http://ubuntuforums.org/showthread.php?t=612065)

---

### Post by Pumalite on 2008-09-30
[http://ubuntuforums.org/showthread.php?t=574501&highlight=Kevdog](http://ubuntuforums.org/showthread.php?t=574501&highlight=Kevdog)

---

### Post by 11zac11 on 2008-09-30
thank you very much the last one seemed to be the best but i have got stuck at the "Next create and place your Window's wireless driver into ~/driver:" point i cannot work out how to get it to work, i was woundering if you can help me with this?

---

### Post by 11zac11 on 2008-09-30
ok i got the driver files into the driver directory but when i do the next step "nsuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:
Code:
sudo ndiswrapper -i *****.inf" 
I get s message:
couldn't open net5211.inf: no such file or directory at /usr/sbin/ndiswrapper-1.9 line 219

can anyone help me to fix this and get me onto the next step. thanks all

---

### Post by EdenFuchs on 2008-10-01
I also started using kevdog's wonderful manual. It all went well including copying and un-tar-ing the file I downloaded in another PC, and including distclean. When I typed the "make" command, it said after a few lines:

***CFLAGS was changed in "/home/eden/ndiswrapper-1.48/driver/Makefile". Fix it to use EXTRA_CFLAGS. Stop.

any advice?

---

### Post by tarps87 on 2008-10-01
> **11zac11 said:**
> ok i got the driver files into the driver directory but when i do the next step "nsuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:
Code:
sudo ndiswrapper -i *****.inf" 
I get s message:
couldn't open net5211.inf: no such file or directory at /usr/sbin/ndiswrapper-1.9 line 219

can anyone help me to fix this and get me onto the next step. thanks all

try:
```
sudo ndiswrapper -i ~/driver/*****.inf
```
This will make sure it is looking in the right place for the .inf file

Did this line work?
```
ndiswrapper -v
```

---

### Post by 11zac11 on 2008-10-01
> **tarps87 said:**
> try:
```
sudo ndiswrapper -i ~/driver/*****.inf
```
This will make sure it is looking in the right place for the .inf file

Did this line work?
```
ndiswrapper -v
```

Thank you very much i got that to work, ok next thing i have got stuck on :( i get to "Ensure you dont get any errors when running this command. Then:

Code:
sudo modprobe ndiswrapper"

and do that but then my system frezzes up and i have to switch it off

---

### Post by tarps87 on 2008-10-02
This may be due to using the wrong version of ndiswrapper or the wireless driver.

You can try downloading the .deb install at:
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)
The latest version for 32bit systems is
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb)
You should have all the dependences, so you should be able to open it and click install. The next package is at:
[http://packages.ubuntu.com/hardy/ndisgtk](http://packages.ubuntu.com/hardy/ndisgtk)
This is a gui for setting up ndiswrapper, it should be the same to install as the previous package.
Once installed type:
```
ndis-gtk
```or
```
ndisgtk
```to run it

---

### Post by 11zac11 on 2008-10-04
ok i did all that and in the "wireless network drivers" window it says the drivers have been install and hardware is present but i still cant connect to my wireless network any ideas why?

---

### Post by Pumalite on 2008-10-04
This might help you (not sure):
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by 11zac11 on 2008-10-04
sadly that dosnt seem to have any more help in it either, thank you for trying though

---

### Post by 11zac11 on 2008-10-05
when i get to the "Ok, to insert the ndiswrapper module into the linux kernel:
Code:
sudo depmod -a
Ensure you dont get any errors when running this command. Then:
Code:
sudo modprobe ndiswrapper" 

at the "sudo depmod -a" nothing happens at all then when i do the next code the system crash's

---

