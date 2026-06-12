---
title: "Cannot boot from hard drive on former Windows 10 machine after installing Ubuntu"
date: 2016-09-09
forum: Installation &amp; Upgrades
---

### Post by thegeo on 2016-09-09
Hi,

I got a crappy little Dell Inspiron a few months ago that only has < 25gb of hard drive space. Windows 10 was taking up most of the hard drive. It was ok until I decided to install Android Studio and learn app development. Then it was not so ok.

I downloaded Ubuntu GNOME v16 and used Netbootin to make a bootable flash drive, because this thing doesn't have a CD-ROM drive. I then killed Windows 10 entirely (I'm a *nix fan for many years and hated Win 10) and installed Ubuntu on the hard drive. No need for imaging. It's practically brand new and didn't have much on it anyway.

I noticed in the BIOS that I have 2 options for booting: UEFI or legacy. If I want it to boot to a flash drive, I have to set it to legacy and specify the boot order. You get the idea.

Now when I try to boot the machine from the hard drive from the Netbootin menu, I get a message telling me that there are no bootable devices. 

At this point, I'm more than a little annoyed. I've been doing a lot of research, and I can't find any answers that seem to apply to my particular situation. Was Netbootin the wrong choice? Is there something else out there (that, at this point, runs on Linux) that's better suited to making a bootable flash drive for this laptop? 

Again, we're not talking about dual boot. This is now strictly a Linux machine, which is what I want. And I specifically need something with GNOME for Android Studio. Ubuntu GNOME should be a great choice because of the small size. 

Thanks for any light you all can shed on this. Sorry I'm a bit rusty with all things *nix. It's been years. I am SO impressed with Ubuntu, though! I love it and want to use the full install, not just taking it for a test drive from the flash drive!

Sincerely,

The Geo

---

### Post by RobGoss on 2016-09-09
Hello and welcome to the forum, When you tried installing Ubuntu what setting did you have it set to Legacy or UEFI? You should be able to install Ubuntu it both Legacy or UEFI if you only intend to have Ubuntu on this machine. I have Ubuntu installed on one of my machines in Legacy as well it would matter if you're are dual booting 

Is there a operating system on that machine now or is the drive empty? You can try Pendrive to make your bootable USB if you're using Windows [http://www.pendrivelinux.com/linux-live-usb-creator/](http://www.pendrivelinux.com/linux-live-usb-creator/)

If you're using a Linux desktop environment there are a number to tools to create a USB bootable flash drive one that comes to mind is **startup disk creator **[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu) it can be downloaded from the Ubuntu software center [https://apps.ubuntu.com/cat/applications/precise/usb-creator-gtk/](https://apps.ubuntu.com/cat/applications/precise/usb-creator-gtk/)

---

### Post by yancek on 2016-09-09
If you see 'unetbootin' on the boot menu, that means you did a frugal install which is explained at the link below.  I doubt that's what you wanted.

[https://sourceforge.net/p/unetbootin/wiki/installmodes/](https://sourceforge.net/p/unetbootin/wiki/installmodes/)

Might be best to get and run boot repair from the link below and select the option to Create BootInfo Summary and post a link to the output here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by thegeo on 2016-09-11
OK. I had been eyeballing boot repair as an option. It looks like that is probably the way for me to go. 

I had the BIOS set for legacy boot when I installed although UEFI is on the machine. I did use unetbootin to make my bootable USB drive cuz some site said it would get me there. *sigh*

The installation of Ubuntu is there. I can see it when I boot from USB. 

I had zero doubt I wanted a Ubuntu machine. No Windblow$. Besides, there isn't room on the HD anyway.

I will update this post soon. Thanks again!

---

### Post by mörgæs on 2016-09-11
One more computer entering the free world. 
Please mark the thread solved and yes, updates are welcome.

---

