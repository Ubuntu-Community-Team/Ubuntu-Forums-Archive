---
title: "Unable to install ubuntu,i cant see my HDD!"
date: 2016-11-27
forum: Installation &amp; Upgrades
---

### Post by ankeras on 2016-11-27
Hi guys i just trying to install ubuntu on my new laptop Acer Aspire One  Cloudbook , first of all i lose like 3 hr traying to get to the  instaler due to facpi=off :(
well when i m on ubuntu and rdy to install , ubuntu say that there is no  enough space to install it, i checked and it compares to my USB but  there is no HDD option
i go to terminal and see there is no HDD mounted or detected just my USB  , then click on Gparted and same there is nothing just my USB.
what can i do ? i want to delete my w10 :/
Thx for your time i apreciated it !

---

### Post by oldfred on 2016-11-27
From terminal in live installer post this:
sudo parted -l

Is Windows fast start up on? That prevents the Linux NTFS driver from mounting it, so drive is not seen.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

### Post by ankeras on 2016-11-27
Yes i disabled before the Fast start by unchecked the option in Energy Options Menu.
There is the image from sudo parted -l , i cant copy just the code bcs i havnt internet conection on the laptop yet.
[https://postimg.org/image/ipvww7mkj/](https://postimg.org/image/ipvww7mkj/)

---

### Post by oldfred on 2016-11-27
That also only shows USB drive.

Does BIOS show hard drive correctly?

---

### Post by ankeras on 2016-11-27
Bios 
MAIN
**EMMC model name : HBG4e 32 G ***
This is all the "information" u have about the SSD from bios , is just a simple one u can set Boot options ,security paswrod  and Boot Mode .
Maybe is that i need to change SATA to AHCI? if is this i have no option in BIOS.

---

### Post by oldfred on 2016-11-27
Link I posted above on Cloudbook discusses exactly your issue.
Did you follow its procedures?

---

### Post by ankeras on 2016-11-27
well , i disable w10 fast start , enbled UEFI , disabled Secure boot,touchpad is basic ,LID open resume enabled,D2D recovery enabled,TPM disabled,password set.

---

### Post by oldfred on 2016-11-27
Do not have a Cloudbook. So other than general help, cannot add much.

---

