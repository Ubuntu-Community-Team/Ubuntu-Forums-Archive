---
title: "Impossible for me to install Ubuntu?"
date: 2015-05-02
forum: Installation &amp; Upgrades
---

### Post by ryan155 on 2015-05-02
Okay so as the title suggests i'm wondering if it's physically possible to install ubuntu on my system.

[COLOR=#ff0000]OVERVIEW:[/COLOR] Okay so i've been trying to install ubuntu on my system for about 7 hours now. Yep, 7 hours. [COLOR=#00ff00]I have disabled secure boot and I have disabled fast boot.[/COLOR] But to no avail, it just boots into that virus called Windows 8.

WHAT I'M TRYING TO DO: I'm trying to [COLOR=#00ff00]install Ubuntu via a USB[/COLOR] because [COLOR=#00ff00]my laptop came with a fake optical drive so I can't try a LiveCD.[/COLOR] I have tried changing the Boot order in my BIOS to load the USB first and the HDD last but that doesn't work. I have tried going into the restart menu and selecting boot USB but that didn't work. I tried selecting the USB in my BIOS but that didn't work. I opened MSCONFIG and went to the boot tab but the only thing it shows is the C: drive. I'm booting in UEFI because when I tried CSM it didn't detect my usb and told me to plug one in and try again. TO MAKE MYSELF CLEAR I'M GOING TO INSTALL OVER WINDOWS 8 AND GET RID OF IT ENTIRELY! So if there are any options other than USB thats easier tell me!

---

### Post by grahammechanical on 2015-05-02
You have not told us what machine you have. So, we cannot help you there. Have you read this wiki page?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

That is the best I can offer. Except to add that although my motherboard is BIOS and not UEFI I can only load an OS from a USB memory stick if I change the BIOS hard drive settings. Changing the boot order does not work because the motherboard sees the USB stick as an external USB drive. Changing the boot priority works for DVD disks but not USB memory sticks.

 So, I have to go to a setting that allows me to select which hard drive to boot from. If I do not do that I cannot boot from a USB memory stick. Your system may be similar. Or may not.

Regards.

---

### Post by kc1di on 2015-05-02
Hello ryan155  and Welcome to Ubuntu,

There could be a couple reasons it fails to boot.  but without a little more info on your system it would be hard for us to tell . give us some info on your machine. 
Manufacturer, cpu , ram and especially video card in use.   

Some manufacturers uefi systems will not allow the booting of any O.S. except windows.  That's a said fact of life at this time. 
but let us know what you have and we will try to help.
Cheers ;)

---

### Post by craig10x on 2015-05-02
Couldn't you burn 15.04 to a dvd iso and change the bios setting to boot off the cd/dvd drive?  That should work without any problems...

---

### Post by ryan155 on 2015-05-02
Thank you all for such quick replies I really appreciate it! My system is a Toshiba Satellite C55T-B5109 with an INTEL Core i3 4005U cpu and some version of Intel integrated graphics. It came factory with 4gigs of ram but I have since upgraded it to 8. @Craig I can't use a DVD because the laptop came with a fake disk drive (silly I know) so a DVD is impossible to use. I'm using Universal-USB-Installer to burn Ubuntu v.15.04 to the USB. And yes grammechanical i've read over that wiki around 20 times to see if I was missing anything (sad to say I didn't).

---

### Post by kc1di on 2015-05-02
Unfortunately from what I can find out , I don't own that model Toshiba -- But it seems no one has been able to install ubuntu or other linux on that model. Seems the UEFI boot in that machine - will only boot a windows OS. So you may be out of luck on that one -Sorry to be the bearer of Bad news.  But maybe there is the off chance some one got it working.  From what I can see from Toshiba's forums -- the firmware in that particular model requires a windows O.S. to boot.

---

### Post by ajgreeny on 2015-05-02
I have no idea if this will help or not but it is known that HP, Toshiba and some others will not let you set anything other than Windows as default in UEFI menu. But there are work arounds.
Thanks to oldfred for this info.

UEFI still lets you boot devices and the /efi/Boot folder has bootx64.efi which is the hard drive boot entry. If you rename that and make it be grubx64.efi then booting hard drive boots grub menu.

Other work arounds.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Script that automates the rename. Not tested but looks like it should work.

script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix).

---

### Post by alex375 on 2015-05-02
Fake usb too?
Try extlinux
[URL="http://humpty.drivehq.com/promotes/linux/lubuntu-extlinux.html"]http://humpty.drivehq.com/promotes/linux/lubuntu-extlinux.html

[https://wiki.gentoo.org/wiki/Syslinux/en](https://wiki.gentoo.org/wiki/Syslinux/en)
[/URL]

---

