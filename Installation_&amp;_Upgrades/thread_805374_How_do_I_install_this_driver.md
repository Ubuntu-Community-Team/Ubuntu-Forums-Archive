---
title: "How do I install this driver?"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by lkarmaz2 on 2008-05-23
Hey everybody, I have fallen in love with Linux and I have been running it no problem, but I want to set up a wireless card. I found the card and checked to make sure it had drivers. Here is a link to the .tar [ftp://66.104.77.130/cn/wlan/rtl8185_linux_26%5B1%5D.1027.0823.2007.tar.gz](ftp://66.104.77.130/cn/wlan/rtl8185_linux_26%5B1%5D.1027.0823.2007.tar.gz)
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)                           I may love linux, but I am a complete noob, so give me EXACT instructions on how to install it. I found a readme with instructions in it, but I can't run the script.
Make sure you list every little step, don't assume I know anything.

---

### Post by Pumalite on 2008-05-23
This might help:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by binary00mind on 2008-05-24
> **lkarmaz2 said:**
> Hey everybody, I have fallen in love with Linux and I have been running it no problem, but I want to set up a wireless card. I found the card and checked to make sure it had drivers. Here is a link to the .tar [ftp://66.104.77.130/cn/wlan/rtl8185_linux_26%5B1%5D.1027.0823.2007.tar.gz](ftp://66.104.77.130/cn/wlan/rtl8185_linux_26%5B1%5D.1027.0823.2007.tar.gz)
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)                           I may love linux, but I am a complete noob, so give me EXACT instructions on how to install it. I found a readme with instructions in it, but I can't run the script.
Make sure you list every little step, don't assume I know anything.
[COLOR="DarkRed"][/COLOR]hi I don't know your driver (or card). I downloaded and will take a peek. But You can try something else. Get Windows version of this driver. From regular Add & Remove software Menu, get package named "Windows Wireless Drivers" (You may have to set the option "All available packages sources" , I am not sure now ) after installation click add "DRIVER" And You Simply navigate or lead to location of the driver and click on it. The extension is [.inf] It will tell You right the way if it is good or acceptable. I use driver installed exactly that way. It is Broadcom driver and works better then the Ubuntu restricted replacment, the bcm43xx plus the firmware. I hope it will work for You, as it did for me.

---

### Post by Cap'n Skyler on 2008-05-24
> **binary00mind said:**
> [COLOR="DarkRed"][/COLOR]hi I don't know your driver (or card). I downloaded and will take a peek. But You can try something else. Get Windows version of this driver. From regular Add & Remove software Menu, get package named "Windows Wireless Drivers" (You may have to set the option "All available packages sources" , I am not sure now ) after installation click add "DRIVER" And You Simply navigate or lead to location of the driver and click on it. The extension is [.inf] It will tell You right the way if it is good or acceptable. I use driver installed exactly that way. It is Broadcom driver and works better then the Ubuntu restricted replacment, the bcm43xx plus the firmware. I hope it will work for You, as it did for me.

i believe you will need ndiswrapper--this is how my set up is :)
for a windows exe file,you may well end up having to open it and burn to cd on a windows computer then to your 'Buntu add the cd and use the XP INF file for the driver .

good luck and welcome to the forums and post up how it went :)

---

### Post by Cap'n Skyler on 2008-05-24
> **lkarmaz2 said:**
> Hey everybody, I have fallen in love with Linux and I have been running it no problem, but I want to set up a wireless card. I found the card and checked to make sure it had drivers. Here is a link to the .tar [ftp://66.104.77.130/cn/wlan/rtl8185_linux_26%5B1%5D.1027.0823.2007.tar.gz](ftp://66.104.77.130/cn/wlan/rtl8185_linux_26%5B1%5D.1027.0823.2007.tar.gz)
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)                           I may love linux, but I am a complete noob, so give me EXACT instructions on how to install it. I found a readme with instructions in it, but I can't run the script.
Make sure you list every little step, don't assume I know anything.

hey !! welcome to the light side...leave the windows world of darkness :guitar:
and welcome to teh forumz

---

### Post by binary00mind on 2008-05-24
> **Cap'n Skyler said:**
> i believe you will need ndiswrapper--this is how my set up is :)
for a windows exe file,you may well end up having to open it and burn to cd on a windows computer then to your 'Buntu add the cd and use the XP INF file for the driver .

good luck and welcome to the forums and post up how it went :)
My Broadcome came as exe also..Just use some imagination..and I Just had the package to deliver...Oh Well

---

### Post by lkarmaz2 on 2008-05-25
Hey, I actually bought this card because it was designed for Linux, and has native Linux drivers available. I currently have a 50ft Ethernet cable hooked into this computer. BTW, I know this has nothing to do with this, but the computer I installed this on has Quad SLI graphics and Windows Vista doesn't support SLI very well, but Linux recognized them right away. I am so happy I switched. I also used Wine and figured out how to run BioShock and I can run it better than in windows. I LOVE UBUNTU!!!

---

### Post by Pumalite on 2008-05-25
Welcome to Ubuntu.

---

### Post by lkarmaz2 on 2008-05-25
Thanks, problem solved. I used Ndiswrapper. I own a Medium-Sized business and I started preparing to move our servers to Linux after I discussed the enhanced stability with our Sys Admin.

---

