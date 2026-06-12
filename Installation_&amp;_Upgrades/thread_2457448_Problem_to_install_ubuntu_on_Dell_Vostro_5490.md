---
title: "Problem to install ubuntu on Dell Vostro 5490"
date: 2021-02-02
forum: Installation &amp; Upgrades
---

### Post by josefran on 2021-02-02
well I got a new computer (Dell Vostro 5490) and a simple can't install the Ubuntu on it.


Only one time the usb stick was recognized by te boot system. And on that time the ubuntu asked me to unable the rst system. I went to my configuration on windows and the "Intel optane memory" says that the computer doestn't have an compatible disk to this, which is weird since on the bios setup you can find a reference to it. 


What I have tried until now create the usb stick using:
 - belenaEtcher
 - rufus - gparted and mms
 - disck creater on ubuntu
 - this tutorial (on ubuntu and windows) [https://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](https://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)


All these tries I tested on all possible combinations of unable and able of the options bellow on bios
 - "Secure Boot" 
 - "Audit Mode" or "Deployed Mode"
 - All intel technologes that I could find on bios system
 - Raid or Ahci




I'm also sending some prints from my bios system. 


Please, 
If someone could help me. 
Best
J.






[IMG]https://i.stack.imgur.com/D0vKY.jpg[/IMG]
[IMG]https://i.stack.imgur.com/98VCZ.jpg[/IMG]
[IMG]https://i.stack.imgur.com/29RoK.jpg[/IMG]
[IMG]https://i.stack.imgur.com/wZ3Ry.jpg[/IMG]

---

### Post by CelticWarrior on 2021-02-02
Also posted and answered here: [https://ubuntuforum-pt.org/index.php?topic=124827.msg681630#msg681630](https://ubuntuforum-pt.org/index.php?topic=124827.msg681630#msg681630)

In summary,

UEFY only
AHCI
Secure Boot and Fast Boot OFF

Before anything else update UEFI.

---

### Post by oldfred on 2021-02-02
Please Attach screen shots. Do not post in line. 
Easy to do with Forum's Go Advanced editor & paperclip icon.

If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

This user used Rufus but originally created installer in BIOS/MBR mode, not UEFI/gpt mode.
Dell Latitude 5490 M.2 PCIe SSD
[https://ubuntuforums.org/showthread.php?t=2405822](https://ubuntuforums.org/showthread.php?t=2405822)

---

