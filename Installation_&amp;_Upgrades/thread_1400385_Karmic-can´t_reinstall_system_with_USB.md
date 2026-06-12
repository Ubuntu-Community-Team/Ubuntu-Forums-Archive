---
title: "Karmic-can´t reinstall system with USB?"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by vickoxy on 2010-02-06
Hi,
i use Fluxbox (Mint 8) in Karmic, but after few tweaks and updates i have to reinstall system-but i couldn´t even make with gparted and usb-creator startup disk, so i used virtual machine in Mac OS to make some older version (Mint 7 XFCE).

BUT, then i discovered that i can not even load the system from USB-although it was all set in bios to startup with USB Stick. 

How can i persuade my dell mini 10v to start up from live USB Stick.

Please if someone can help me-i need that little  computer badly...
:frown::frown::frown:

---

### Post by wilee-nilee on 2010-02-07
Make sure you have a bootable thumb with another computer. Since you don't mention in detail the way you loaded the thumb other then in Apple more info is needed.

---

### Post by vickoxy on 2010-02-07
Ok-i tried unetbootin and usb-creator-nothing in min fluxbox was possible-every time i have been reported of some errors (once when i per gparted tried to format usb-stick and once after making live usb-stick). So i made it in virtual machine machine (on macbook with xubuntu 9.04)-everything works fine, but when i plug it in dell - nothing- it starts fluxbox main system, or if i press f2 to see start partitions and choose usb, it says that no system is available.
I am really in need here, so if someone has any idea....
It won´t recognize any bootable device.

---

### Post by vickoxy on 2010-02-07
"OPeration system missing" is what i get when i plug in usb stick (i made it from xubuntu 9.10)-no metter is it made with unetbootin or usb-creator. 
I have > + before usb devices in boot menu. I tried with>  shift + 1 to mark/unmark it with>  !-but nothing. 

I do not know-maybe my sdhc card reader is the problem-i tried few mini sdhc card-all the same.
I really do not know....

---

### Post by vickoxy on 2010-02-07
UPGRADE_i killed my dell mini 10v. I installed some linux 2.6.31-304-ec2 kernel, after restart i got screen telling me to boot 4 options (approx)

    linux 2.6.31-304-ec2 (/dev/sda1)
    linux 2.6.31-304-ec2 (recovery mode)
    Memory test
    Memory test (serial console


shane:
If i choose first 2 options i got:

    You are the only one ever to get that error?! :shock: You must have done something special to Synaptic :lol:

    I still don't know what it means... and I don't know what you did to get the error. So there is not much I can advise you to do. Please be more specific.

    Again, upgrading the kernel is a fix for the wireless Atheros ath9k driver problem. NOT the rhino one.


Code: Select all
    error: You need to load the kernel first
    Press any key to continue



Of course it brings me back to first option, and i can do nothing. Can not load anything.

Is there way out from this situation? As said i tried to install from usb-stick new ubuntu version (tried few of them with guest machine in macbook, with unetbootin and with usb-creator-but nothing) but dell won´t start from it.

Does anyone has any idea how to make bootable usb stick (or at least to see if something is wrong with it)

Help me someone. Please....

---

### Post by darkod on 2010-02-07
What have you got to work with?
It's best to create the usb stick on ubuntu machine using the standard usb startup disc creator (not usb-creator), or in windows using unetbootin. I don't know about anything else.
You might be able to create it using the ubuntu cd, on any machine that has a cd-rom, it doesn't need to be running ubuntu.
For example, try this:
Download the ISO of ubuntu/xubuntu you want. Make a bootable cd with it.
Boot the computer with that cd, but also have the ISO saved somewhere on that computer. Once you boot into live desktop, go in System-Administration and use usb startup disc creator. Point it to which ISO to use, and which usb stick. It should be able to create it like that.

But if your netbook is not booting correctly from usb, I don't know what to tell you. You're stuck. Or try to borrow usb cd drive, and use a cd.

---

### Post by vickoxy on 2010-02-07
> **darkod said:**
> What have you got to work with?
It's best to create the usb stick on ubuntu machine using the standard usb startup disc creator (not usb-creator), or in windows using unetbootin. I don't know about anything else.
You might be able to create it using the ubuntu cd, on any machine that has a cd-rom, it doesn't need to be running ubuntu.
For example, try this:
Download the ISO of ubuntu/xubuntu you want. Make a bootable cd with it.
Boot the computer with that cd, but also have the ISO saved somewhere on that computer. Once you boot into live desktop, go in System-Administration and use usb startup disc creator. Point it to which ISO to use, and which usb stick. It should be able to create it like that.

But if your netbook is not booting correctly from usb, I don't know what to tell you. You're stuck. Or try to borrow usb cd drive, and use a cd.

Well thanks for answer-i have one macbook with parallels desktop-running windows xp, xubuntu-i tried what you proposed, but it (dell mini 10v) won´t start with usb plugged in. I am just hoping that my usb card reader is broken, because i tried few mini sdhc cards. But i am suspicious, because untill karmic i alwayd did good job with these cards and reader.

Just hoping that maybe someone can tell if something with boot loader on dell mini 10v could go wrong, that i can not run live usb.

---

### Post by vickoxy on 2010-02-07
Ok- i made progress-succeeded to make bootable live usb (mint 7 xfce) stick in virtual windows xp using untebootin, and installing it now on dell mini 10. So, we´ll see what ´ll happen. 

Thanks

---

