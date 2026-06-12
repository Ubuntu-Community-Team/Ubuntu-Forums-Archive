---
title: "Help with ubuntu studio 7.10  installation"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by knife_party on 2008-01-10
hi there, i'm totally new on ubuntu, so i decided to just give Ubuntu Studio 7.10 a go. 

The installation runs smoothly, but after i restart the computer, the GRUB won't showed up, so the computer will boot into windows automatically. Strangely, if i inserted the CD, and choose the option "Boot From first hardisk, the grub would showed up.

So i reinstalled it, and i had noticed that the bootable flag in the root partition is not set to yes, so i set it. Again the installation runs smoothly, but after i restart it, it kepps on showing the message "No Boot Disk Found..." like that, and cannot boot at all even when i set up to boot from the hardisk rather than the CD drivel.

Can anybody help me? 

thanks in advance

---

### Post by forestpixie on 2008-01-10
asssuming that the install has gone properly and the only problem is that grub didn't install, you can use the livecd to install grub or download supergrub, burn it as an iso and boot with it

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by knife_party on 2008-01-10
so does it mean i have to always boot with the supergrub inserted on the cd drive?

---

### Post by forestpixie on 2008-01-10
no - if supergrub does it's job it will write the grub for you and you should be ok 

that said never had anything to do with studio myself

---

### Post by knife_party on 2008-01-13
now the grub problem has solved..thanks mate..

but one more problem.. there's a message about "x cannot configure" and the desktop won't showed up..  i don't know what this means.. Can u help?

---

### Post by windeguy on 2008-02-26
I am new to Linux, I have tried several distributions and currently have Xubuntu loaded in my Pentium 4 system and would like to install Ubuntu Studio. 

I have tried several times to burn an Ubuntu Studio installation DVD (using both windows and Xubuntu) and cannot get a good burn of the DVD.  The checksum of the .iso file I am using to burn with (md5sum) is good.  

Is there any way to install Ubuntu Studio directly from the same or different  hard disk where I have Xubuntu now?

---

### Post by forestpixie on 2008-02-26
you can do a 

sudo ubuntustudio-desktop

from a terminal and you'll have choice a login, go to sessions in login window

---

### Post by Drunky on 2008-02-26
> **windeguy said:**
> I am new to Linux, I have tried several distributions and currently have Xubuntu loaded in my Pentium 4 system and would like to install Ubuntu Studio. 

I have tried several times to burn an Ubuntu Studio installation DVD (using both windows and Xubuntu) and cannot get a good burn of the DVD.  The checksum of the .iso file I am using to burn with (md5sum) is good.  

Is there any way to install Ubuntu Studio directly from the same or different  hard disk where I have Xubuntu now?

Yes, open a terminal and cut/paste...
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

This is is from [Ubuntu Help Wiki:UpgradingFromGutsy]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy")

This is a full install of Ubuntu Studio including the real-time kernel.

---

