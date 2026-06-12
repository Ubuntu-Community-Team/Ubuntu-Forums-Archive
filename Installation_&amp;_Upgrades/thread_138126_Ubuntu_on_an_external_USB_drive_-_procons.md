---
title: "Ubuntu on an external USB drive - pro/cons?"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by jmmmp on 2006-03-01
Hi all,

I want to install Ubuntu, as it's the most hip distribution now, and I really don't have the time and mood plunge into debian or other hard-core stuff.

My system is a Thinkpad with 80Gb disk, where XP and Suse are installed. I don't use Suse for a while and want to trash it sometime (for sure when Ubuntu is in). That also means that Grub is already installed (I guess it's not a problem).
I was thinking of getting an external usb disk and install Ubuntu in it, leaving the XP distribution alone. The advantages that I can see would be the following:

- Ubuntu would be separate, and I could even take it out and boot it on other computers and continue my work (is this as simple as it sounds?)
- less danger of system problems, which could make any/all partitions unbootable/unusable/etc.


and the possible disadvantages:

- is it possible at all? (I guess so, according to some reports)
- is the speed much different? (I work on sound, and occasionally video, which means sometimes big files)
- is it worth the bother, compared to a normal split hard disk installation?


If possible, I would like to benefit from all your experience. I already saw the thread [http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811), which seems quite ok. I already had some problems with linux installations, and it would be quite catastrophical for me to loose more time restoring - again - a XP partition (and resulting only in delaying even more my transition to linux), so I wanted to do the installation in one step, and with no problems (well, no problems for xp anyway).

Thanks,

Joao

---

### Post by MacV on 2006-03-01
Well, for one, does your system support booting from a USB device?

---

### Post by earobinson on 2006-03-01
> - Ubuntu would be separate, and I could even take it out and boot it on other computers and continue my work (is this as simple as it sounds?)
I dont think so unless the two computer has the exact same HW
> - less danger of system problems, which could make any/all partitions unbootable/unusable/etc.
I would say this is false also because a normal setup would be more simple
> - is it possible at all? (I guess so, according to some reports)
yes it can be done if your system can boot from the usb device
> - is the speed much different? (I work on sound, and occasionally video, which means sometimes big files) 
limited to speed of external HD (could be huge diff could be none at all)
> - is it worth the bother, compared to a normal split hard disk installation?
It realy comes down to your reason for doing this if it is worth it or not.

---

### Post by Rizado on 2006-03-01
[QUOTE=MacV]Well, for one, does your system support booting from a USB device?[/QUOTE]Is it really necessary? Wouldn't it be possible to make one small /boot partition on a regular drive or maybe lilo can boot directly from usb?

---

### Post by MacV on 2006-03-01
[QUOTE=Rizado]Is it really necessary? Wouldn't it be possible to make one small /boot partition on a regular drive or maybe lilo can boot directly from usb?[/QUOTE]

I don't think so. I think grub and lilo come up before the computer even "sees" the rest of the hardware on the machine after boot. Without the BIOS telling the comp to "activate" the usb ports, the computer won't even see it. 

Anyone correct me if I'm wrong.

---

### Post by Rizado on 2006-03-02
[QUOTE=MacV]I don't think so. I think grub and lilo come up before the computer even "sees" the rest of the hardware on the machine after boot. Without the BIOS telling the comp to "activate" the usb ports, the computer won't even see it. 

Anyone correct me if I'm wrong.[/QUOTE]But if you load the kernel on a regular drive and recognizes your usbdrives it should work. I'm thinking a really small stripped kernel without module support that loads the kernel on the usbdrive.

Bootloader > stripped kernel with usb support > real kernel on the usb drive.

That must work right?

---

### Post by MacV on 2006-03-02
Well, the theory is sound, but I'm not sure about it "must".

---

### Post by majikstreet on 2006-03-02
I doubt it will boot if your computer isn't able to boot from USB drive....

Anyway, I don't see any reason why not to do it... I think it'll be a learning experience :D

Be sure to let us know how it goes!

majik

---

