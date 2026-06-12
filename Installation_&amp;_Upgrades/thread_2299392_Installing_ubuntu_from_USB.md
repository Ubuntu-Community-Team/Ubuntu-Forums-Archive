---
title: "Installing ubuntu from USB"
date: 2015-10-18
forum: Installation &amp; Upgrades
---

### Post by AJ_Wasek on 2015-10-18
First time trying to install ubuntu! yay me!

So anyways I've been reading the documentation on installing from a USB stick.  I downloaded Ubuntu 10 just so I could temporarily get an OS running on my laptop and upgrade later.  Plus, my stick is only 1gb and the newest Ubuntu iso is 1.1 GB.

So I used Rufus to put the iso on the usb and made it a drive to boot from.  I take it out, it in my other computer (Which still has a corrupted ArchLinux on it) and reboot my computer. (Configured to boot from USB).  It just pops up to the Grub string asking to boot Archlinux but since it is corrupted it takes me to a terminal and it just says grub>

Please any help so I can get ubuntu installed on my other laptop with just USB drive.  Thank you so much in advance.

---

### Post by Bucky Ball on 2015-10-18
Just a tip: You won't be upgrading anywhere from 10.**. It reached end of life some time ago. I suggest you [download the 14.04 LTS ISO]("http://www.ubuntu.com/download/desktop") and start again.

Here's a couple of links for creating USB install media, the second with pics:

UNetbootin:
unetbootin.sourceforge.net

Universal USB Installer:
[www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

... and a 1Gb stick won't cut it. :|

If your machine is low spec or old you would be better going with another flavour, Xubuntu, Lubuntu or Mate, perhaps. 

[http://xubuntu.org/](http://xubuntu.org/)

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by AJ_Wasek on 2015-10-18
What about if I download the ubuntu minimum iso?  Would I be able to boot that up, get on the net, and download the necessary packages to make it into the newest Ubuntu?

---

### Post by Bucky Ball on 2015-10-18
Possibly, if it fits on the 1Gb USB. The mini.iso is the Ubuntu kernel only, nothing else. Once installed you will boot to a terminal where you can log in and install ubuntu-desktop and that will get you to a full version of the latest release, probably 15.04 which reaches end-of-life in January 2016. Not idea and there is no option to 'downgrade' in Ubuntu. 

There is a tool in the mini install called tasksel which allows you to install a machine profile. You could select a profile when you get to that part of the install, say lubuntu-core or xubuntu-core, and that will give you a very basic set-up, but that will be installed to the hard drive.

The mini install has **_no_** function to 'Try Ubuntu' and boot to a live desktop, no. It is a different kettle of fish to a regular *buntu install ... wholly. There are no wireless drivers included and the majority of the install comes down the line via a cable connection. You will need a cable connection for a mini install, in other words.

Bottom line: if you can fit the mini.iso on the USB, give it a go. But read up on it first. Good luck.

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by AJ_Wasek on 2015-10-18
I see.  Thanks for the help and guidance.  I really want Ubuntu so I guess I will just go out and buy a bigger USB stick so I can put the newest iso to it and boot from it.  Either that or just burn it to a CD.  I'm concerned though, even though my 1gb stick was sufficient to hold the ubunto 10 (700mb fully extracted) it still did not give me the option to load Ubuntu.  Instead, it shows up as the grub screen with my old linux distro on the selection menu.  However, my partition is corrupted and when I choose my linux distro, it takes me to the prompt grub>  Is it going to do this even if I get the ubuntu15 and put it on the USB stick?  Boot to USB is enabled


EDIT I'm inserting the USB stick into my other laptop that has the grub as mentioned above
.

---

### Post by Bucky Ball on 2015-10-18
I misunderstood your last post and have edited my last post. Please re-read. Yes, if you can get another USB, go for it. 

I just had a look and the mini.iso will probably fit on that 1Gb USB, though. You will need a cable connection to get online. Give it a try and use the mini.iso for 14.04 from [here]("https://help.ubuntu.com/community/Installation/MinimalCD").

Once installed, reboot and:

```
sudo apt-get install ubuntu-desktop
```

... but before you do the last command, tell us how much RAM and other specs of your machine. Ubuntu might not be ideal.

---

### Post by AJ_Wasek on 2015-10-18
Oh the laptop I'm installing on meets the requirements. The problem I am having is that I am using Rufus to make a Bootable usb with the mini iso for 14. However, when I plug it into the laptop and reboot it goes back to the old grub screen with my old linux distro on  I tried to use that pendrivelinux app and it spit out the error and it said USB WILL NOT BE BOOTABLE

---

### Post by Bucky Ball on 2015-10-18
Are you booting from the USB??? Are you booting into the BIOS and changing the boot device to USB rather than hard drive??? Best to give us as much info as possible as early as possible. :)

---

### Post by AJ_Wasek on 2015-10-18
Yes, my bios is enabled to boot from usb. I use Rufus to install the mini to the USB port, I stick that stick into my other laptop, restart and it goes to grub and waits for me to choose my old linux distro. It doesn't even say anything about Ubuntu when I start up


The Linux distro I use to run was installed by using Rufus and a USB stick so I know it can be done. However, it seems now grub has taken over and doesn't even give the USB a chance to boot. Grub just stops it

---

### Post by sudodus on 2015-10-18
Are you running in UEFI mode or BIOS mode?

You can only boot into BIOS mode from the Ubuntu mini.iso. You need a desktop iso file to boot in UEFI mode. The current Lubuntu desktop iso files are smaller than 1 GB, so they can be used with a 1 GB USB pendrive.

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier to give relevant help. Otherwise we can only give general advice or guess what you need.

---

### Post by AJ_Wasek on 2015-10-18
It's UEFI. If I install Lubuntu or another Ubuntu for right now, is there a way I can change to the newest ubuntu from that?

Either way like I said before, I put an old version of Ubuntu that did fit on the USB stick, and when I plugged it in and rebooted, it did NOT try to install. It went straight to my old grub screen.

---

### Post by sudodus on 2015-10-18
It is possible, but not really a good idea. It is better to install the system that you want directly. So the easiest option would be to get a cheap but reliable USB pendrive. I would suggest that you get a pendrive with at least 4 GB. See this link and links from it for more details

[FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by AJ_Wasek on 2015-10-18
Thank you very much. I'm still concerned that Ubuntu didn't try to install even when I used Rufus to make a Bootable usb drive with an older version of Ubuntu. Shouldn't it had went to an install screen? Instead my OLD grub is just popping up. SECURE BOOT disabled in bios. Also, booting from USB enabled.

---

### Post by sudodus on 2015-10-18
Ubuntu 10 is too old for UEFI.

---

### Post by AJ_Wasek on 2015-10-18
Thank you guys both very much. I will go and buy a bigger storage device, or I just might go and support Ubuntu and buy a CD. :)

---

### Post by sudodus on 2015-10-18
A USB pendrive can be re-used many times. If it is easy for you to download iso files, it is a better option. You can support Ubuntu anyway if you wish (via a donation).

---

