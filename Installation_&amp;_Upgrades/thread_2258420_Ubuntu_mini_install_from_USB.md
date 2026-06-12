---
title: "Ubuntu mini install from USB"
date: 2014-12-27
forum: Installation &amp; Upgrades
---

### Post by ylafont on 2014-12-27
i have bee trying to install 14.10 from usb to hard drive.   the installation completes but Ubuntu fails to start up on reboot.   Is there a fix for this?

[B]Intel NUC D5425 - i5 - integrated graphics.
[/B]
Ubuntu Mini From [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
ISO written with unetbootin for Windows

Flashing cursor on Reboot.

---

### Post by mörgæs on 2014-12-27
What do you get on reboot?

---

### Post by ylafont on 2014-12-27
Just a blinking dash

---

### Post by MAFoElffen on 2014-12-27
What is the hardware (system and video) that you are installing to? Also, on the Mini install disk, during the install, did you happen to select text install? If not, what desktop suite package did you select to be installed?*

Note-- If you branch to a graphics installation on that disk and fail to "manually" select a desktop package choice... it will reboot to a flashing cursor, hung there, because there would be no graphics desktop installed to continue to boot into. That install disk does not install a graphical desktop automatically, because it gives the user the choice of which desktop they want to install.

---

### Post by ylafont on 2014-12-27
**Intel NUC D5425 - i5  - integrated graphics.**


I have seen this before on other models and though it was fluke. the only method i have been able to install the OS is via PXE.  Which works fine, but no  PXE server today.

Not really sure on the installation option i selected. I think it was just text install. I am formatting the stick now to redo the installation will have more specifics as soon as i redo the installation.

---

### Post by MAFoElffen on 2014-12-27
if you are doing a text install from that disk... and just want a text console, there is a quick-fix work-around: (meaning. you don't have to re-install...)

At boot, as the BIOS messages are ending, start pressing the <left-shift> key... at the Grub boot menu, press <E>. Go down to the line starting with "linux". At the end of that line, add "text". Prees <cntrl><X> to boot. It will boot into a text console multi-user mode.

From there you should be able to log in, then if you want to install a desktop:
```

sudo tasksel

```
That should bring up the same tasksel menu that was on the disk you installed from... if not tell me and I'll give you the command for what you want to install...

If you want it to remain a text console, then:
```

sudo nano /etc/default/grub

```
and go down to that line that starts with:
```

GRUB_CMDLINE_LINUX_DEFAULT=""

```
...and change it to:
```

GRUB_CMDLINE_LINUX_DEFAULT="text"

```
Save and exit--> <cntrl><O>  <Enter>  <cntrl><X>
```

sudo update-grub

```
Reboot.

If that doesn't take care of it, let me know. I have other work-arounds for both those.

If solved with either of those, remember to come back to tell us what helped and to mark the thread as solved.

---

### Post by ylafont on 2014-12-27
Pressing left-shift after bios was not effective for me. not sure if it was a timing issue. But was not able to make it happen. 

re-installed the Ubuntu Mini 64 bit.

Not sure what is the difference between install and Command line install. they both seem to be the same. 


 I noticed the following:
 when installing grub - it was installed to the boot media in this case /dev/sda (which was the USB drive) and not the installation drive which was /dev/sdb

This also explains why the USB Drive failed to boot after the installation. I have to re-apply the ISO.

is there a small Ubuntu iso that will allow me to boot and install grub? or do i have to download the full blown ISO?


By the way [MAFoElffen]("http://ubuntuforums.org/member.php?u=1044547")[COLOR=#000000]  - than you for the assistance.[/COLOR]

---

### Post by MAFoElffen on 2014-12-27
The mini or net install are both small iso images... Have to do some errands and will check back later...

---

### Post by ylafont on 2014-12-27
Update --- 


Booted from mini usb and select rescue mode and install GRUB on /dev/sdb  - no go

modified /etc/default/grub from the rescue command line  up did not allow me to run updated-grub.



Seems to be a bug in the installation script.

---

### Post by MAFoElffen on 2014-12-27
Well... a mis-understanding really. Will that boot a LIveCD Image from USB? If so, you could boot from a LiveCD on USB.... and chroot into the installed system to install Grub to it.

---

### Post by ylafont on 2014-12-27
Sure - just download it and currently writing to USB.   Should be booting to live environment in a few.

---

### Post by MAFoElffen on 2014-12-27
Before you boot that, take a look at the 3rd post in my sticky... It explains how to chroot into an installed sysem from a booted LiveCD image. Once your are chrooted into that system ,then you could install grub to it.

---

### Post by ylafont on 2014-12-27
Not sure if this bios issue with EFI,   as described here. 
[http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/](http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/)

nothing worked, even update BIOS, just in case.  Had to install the full blown OS and then boot to terminal. 

Funny thing thing is i know it works if i install via PXE.

---

### Post by sudodus on 2014-12-28
Just my two cents:

(I don't know if it is your problem, but just in case ...) The Ubuntu mini.iso will not install a system that works in UEFI mode.

Why do you want the version 14.10? Do you need some driver or software, that is available only in that version? Otherwise, version 14.04 LTS is more debugged and polished and will work much longer. Ubuntu version 14.10 has a lifetime of only 9 months, while version 14.04 LTS has a lifetime of 5 years, until April 2019.

---

### Post by ylafont on 2014-12-28
That make a lot of sense to me- let me see if that work!

---

### Post by MAFoElffen on 2014-12-28
> **sudodus said:**
> Just my two cents:

(I don't know if it is your problem, but just in case ...) The Ubuntu mini.iso will not install a system that works in UEFI mode.

Why do you want the version 14.10? Do you need some driver or software, that is available only in that version? Otherwise, version 14.04 LTS is more debugged and polished and will work much longer. Ubuntu version 14.10 has a lifetime of only 9 months, while version 14.04 LTS has a lifetime of 5 years, until April 2019.
+1

I have to admit that the mini Install disk is not polished, nor is it for everyone. IMHO, it is a very flexible install disk, meant for someone who is experienced with Ubuntu installs, Ubunutu branches and Linux commndline. There are things you have to know to be able to understand and make the choices it offers. There are things that you might have to finish or fix "manually." That is why I have so many work-around's for that install disk... I do not recommend it to first-timers.

---

### Post by alexbb2 on 2014-12-28
I wasted a week trying to install desktop[ Ubuntu 14.04]("http://ubuntuforums.org/showthread.php?t=2257805"). It wiped out a lot of my software and I wasted days of my vacation. This is what I finally did. I installed **Ubuntu desktop 12.04.3 version** and got double boot (with Windows 7 as the C:\ OS) and now it is upgrading to 14.04. Hopefully the upgrade will work, I think the .iso file (14.04) I downloaded is defective. So many people have similar problems, just look.

---

### Post by sudodus on 2014-12-29
The newest point version, now ***14.04.1 LTS*** is debugged and polished and better than the original one (***14.04 LTS***).

But particularly for middle-aged and old hardware, the previous long time support version ***12.04 LTS*** is very good. In some cases ***12.04.1*** is the best point version, in other cases ***12.04.5*** (the newest point version) or as in your case [[COLOR=#000000]alexbb2[/COLOR]]("http://ubuntuforums.org/member.php?u=1961329"), ***12.04.3*** is the best point version.

-o-

Please notice that some of the community flavours of Ubuntu 14.04 LTS (Lubuntu and Xubuntu) have shorter long time support (3 years) than standard Ubuntu, Ubuntu Server and Kubuntu (5 years). Lubuntu 12.04 had no long time support at all and has passed end of life. Xubuntu 12.04 will reach end of life in April 2015. See this link and links from it

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

