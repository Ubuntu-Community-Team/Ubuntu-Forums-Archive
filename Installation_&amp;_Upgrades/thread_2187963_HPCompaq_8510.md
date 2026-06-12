---
title: "HP/Compaq 8510"
date: 2013-11-14
forum: Installation &amp; Upgrades
---

### Post by john-m-ellsworth on 2013-11-14
I am trying to install Ubuntu on an older laptop to give to my son.  The laptop is a HP/Compaq 8510, with Windows XP.  I have downloaded the 13.10 ISO, but it is too big to burn to a CD, and the Laptop will not boot from a USB-stick.  What is the recommended way to proceed?  Should I fall back to the 12.04 ISO and then upgrade, or is there a way to make a smaller 13.10 ISO which will fit on a 800mb CD-ROM.

---

### Post by VMC on 2013-11-14
Have a look at _**[plop]("http://www.plop.at/en/bootmanagers.html")**_ to boot your usb stick. You can install it on either mbr of hard drive or floppy drive.

---

### Post by ian-weisser on 2013-11-14
Or install the base system using the mini .iso, and build from there.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

The mini .iso installs a command-line only system.
After you boot into the command line environment, use the command **sudo apt-get install ubuntu-desktop** to download and install the rest of the Ubuntu environment that is on the too-big .iso.

---

### Post by oldfred on 2013-11-14
If system is so old as to not boot a flash drive it may not be able to run full Ubuntu. 
How much RAM and what video card/chip. Unity needs decent video to run.

You may work with Lubuntu or Xubuntu.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by ibjsb4 on 2013-11-14
Got fast internet?  You could also use the mini iso (only 30MB).

Just do a command line install.  Then run this command after the mini install:
```

sudo apt-get install ubuntu-desktop
```

That will give you a full blown desktop install.  I guess you feel your HP is capable of running Unity.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[https://www.google.com/search?client=ubuntu&channel=fs&q=mini+iso&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=mini+iso&ie=utf-8&oe=utf-8)

The mini iso can also be used to install Lubuntu and Xubuntu.

Edit:  I took too long to post, this has been covered

---

### Post by VMC on 2013-11-14
> **john-m-ellsworth said:**
> I am trying to install Ubuntu on an older laptop to give to my son.  The laptop is a HP/Compaq 8510, with Windows XP.  I have downloaded the 13.10 ISO, but it is too big to burn to a CD, and the Laptop will not boot from a USB-stick.  What is the recommended way to proceed?  Should I fall back to the 12.04 ISO and then upgrade, or is there a way to make a smaller 13.10 ISO which will fit on a 800mb CD-ROM.
I'm a little surprised that you can't boot using the usb port. Is your the 8510P version?

Here is some info about [HP booting USB devices]("http://dfarq.homeip.net/2011/01/how-to-make-hp-and-compaq-computers-boot-off-usb/").

Also the cpu isn't that bad:
[TABLE]
[TR="bgcolor: #FFFFFF"]
[TD]Processor
[/TD]
[TD="width: 401"]Intel® Centrino® with vPro™ technology 
• Intel® Core™2 Duo Processor T7700 
• 2.40 GHz , 4 MB L2 cache, 800 MHz Front Side Bus 
• Intel® Wireless LAN 802.11a/b/g, Bluetooth2.0+[/TD]
[/TR]
[/TABLE]
And then the video:
[TABLE]
[TR="bgcolor: #E7E7E7"]
[TD]Graphic Subsystem Name
[/TD]
[TD="width: 401"]ATI Mobility Radeon™ HD 2600
[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="width: 140"]Graphic Subsystem Video Card Memory
[/TD]
[TD="width: 401"]256 MB of video memory (512 MB HyperMemory)[/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2013-11-14
I have an much older (not HP) T5500 core2 system with only 1.5GB of RAM. It boots from flash drive and does run full Ubuntu althogh I turn Unity off and run fallback or the old menu system like gnome2. I also have the 64 bit version and occasssionally have it use swap if I try to load too much at once. One larger app like Firefox & opening text files& terminal work, but adding anything else I see it stop for a couple of seconds.

Some computers will not show booting from USB, but actually will boot flash drive on USB port as another hard drive. But flash drive has to be seen as bootable to work.

---

