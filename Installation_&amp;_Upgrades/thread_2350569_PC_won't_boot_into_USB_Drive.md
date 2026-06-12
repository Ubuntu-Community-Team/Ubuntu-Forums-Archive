---
title: "PC won't boot into USB Drive"
date: 2017-01-25
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2017-01-25
Hi all,

I am about to create a dual boot, with Ubuntu and Win10.
I already had it done, but turned out I need more space in my SSD, hence I will kick Win10 out, and into my HD. In fact, I already formatted the NTFS partition where Win10 was, into an Ext4 partition. 
I am using the [Tux4Ubuntu Boot Loader]("https://tux4ubuntu.blogspot.com/2016/11/tux-boot-loader-theme-for-ubuntu-refind.html"). 
I already went into the PC settings (like BIOS) and chose both Boot priority order & HD priority to use the Win10 USB drive (it does see it). But I land in some Grub page instead. I guess Grub is getting in the way? 

Thanks guys,

---

### Post by tech-j on 2017-01-25
No, Grub is not getting in the way.
Since you formatted the SSD as EXT4 the Windows boot loader is gone.
So the only thing the system sees on Boot is the Linux (Grub) loader.

Depending on your machine you should be able to select F10 or F12 to access the "1 Time Boot Menu" and scroll down to the USB Drive that has the Windows installer on it and perform your Windows install.
You will then have to follow the same process to select the Windows Drive to boot too when you want to run Windows in the future unless you add a boot loader conf to Grub to load Windows if you select it.

Have Fun!

---

### Post by yancek on 2017-01-25
The link you posted for " tux-boot-loader-theme-for-ubuntu-refind" shows that it is basically a GUI interface for Grub which you would install on the Ubuntu system on your hard drive.
Were you using UEFI for your windows 10 and Ubuntu dual-boot?  Are you planning to use UEFI again for both?  How did you create the windows 10 boot usb?  Have you tested the widnows 10 usb on another machine to verify that it boots?  If you have the usb drive with windows 10 set to first boot priority, maybe posting some details on your hardware/manufacturer would give some info that would help you make the change.  Different manufacturers have different settings/options.

---

### Post by javierdl on 2017-01-25
**tech-j,**

> **tech-j said:**
> ...
Since you formatted the SSD as EXT4 the Windows boot loader is gone....


Then, is it safe to assume that the Boot loader file/s were in the Windows partition?
Honestly I do not recall myself. But I do see how that would explain the present situation. 
-----------------------------------------------------------------------------------

> 
...you should be able to select F10 or F12 to access the "1 Time Boot Menu"  and scroll down to the USB Drive that has the Windows installer on it...

> 
I already went into the PC settings (like BIOS) and chose both Boot  priority order & HD priority to use the Win10 USB drive (it does see  it). But I land in some Grub page instead. 

**yancek**,
> Were you using UEFI for your windows 10 and Ubuntu dual-boot?
Yes.

> Are you planning to use UEFI again for both?
Yes

> How did you create the windows 10 boot usb?
With Universal USB installer


> Have you tested the Windows 10 usb on another machine to verify that it boots?
Not per se, But I did use it on this same pc before. That's exactly how I installed Win10 before.


> ...maybe posting some details on your hardware/manufacturer...
Acer Predator 710, Intel® Core&#8482; i5-6400 CPU @ 2.70GHz × 4, 16Gb ram, 1x1Tb HD, 1x128Gb SSD. I got it about 9 months ago.

This is what the GRUB black screen shows:

```
GNU GRUB version 2.02~beta2-9ubuntu1
*Boot-Repair-Disk session
```

Then when I hit Enter, it goes all black, without doing a thing.

---

### Post by javierdl on 2017-01-26
> ...should be able to select F10 or F12 to access the "1 Time Boot Menu"... **UEFI menu**, to be more precise. It was F12 for me.

Thank you so much for reminding me of that tech-j :)
Finally got Win10 installed!

P.S. To bad now I have to deal with the unfortunate fact that Win10 decided to take more than the 300Gb partition I had assigned for it to install itself, and also took an additional partition where I had important back ups :( (hopefully a partition recovery program will do it)

---

### Post by tech-j on 2017-01-26
Javierdl.

Glad that I was able to help you out!
Yes, you have to be cautious with Win-10 since it will automatically create a UEFI and OS-Reserved(Fat32) Partition on top of the partition that you assign for it to install to.
Nice Machine BTW.
You should enjoy the way Linux runs on that machine and if you game, use the OpenGL to really crank up your frame rates. XD

---

### Post by javierdl on 2017-01-27
tech-j,
Thanks, yes, it's fast and quiet. I love both ;)

---

