---
title: "Stuck at GRUB loading, Stage 1.5, Error 2..."
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by TS1 on 2006-07-04
OK, my laptop is a [Toshiba Satellite P25-S5092](http://www.bithaze.com/d/toshiba_satellite_P25-S5092.pdf) (click for PDF spec sheet if it'd be of any help). I previously had a dual boot with Windows XP Professional and Ubuntu Hoary Hedgehog. Since I really didn't use Ubuntu too much, I found my Windows recovery DVD (that originally shipped with the laptop) and used that to revert back to Windows only. Mistake, I know now... :neutral:

Currently when I start the laptop, I'm presented with the following error:

```
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 2
_
```

...and that's as far as I can get. On boot it doesn't read any CD I put in. I've tried with the XP Home (Install, not Upgrade) CD, Dapper Drake CD, and even various methods/tools on an SD memory card or a USB stick. None work *except* for the recovery DVD. When I have that in the drive, it goes through the entire recovery process seemingly normally, but even after that's completed I still get the same error.

What I'd like to do is try installing Dapper Drake. Anything that will make for a functional laptop again. A dual boot would be nice, but I don't know if it'd be possible in my current situation. Obviously though, installing anything becomes a difficult endeavor if my laptop won't exactly start or load from anything other than the recovery DVD... :(

I did a search on Google and have found [this](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html#SEC103), but it doesn't make much sense to me. (And I'm not entirely sure where this thread should belong, so if it be elsewhere then of course please move it.)

Any help would certainly be appreciated. I hate having a four-figure paperweight. :shock:

---

### Post by simonn on 2006-07-04
Try finding a dos boot disk/cd ([http://www.bootdisk.com](http://www.bootdisk.com)) and using fdisk /mbr. This should remove grub and windows should boot.

---

### Post by TS1 on 2006-07-04
[QUOTE=simonn]Try finding a dos boot disk/cd ([http://www.bootdisk.com](http://www.bootdisk.com)) and using fdisk /mbr. This should remove grub and windows should boot.[/QUOTE] Problem with that is the laptop doesn't have a floppy drive, nor I a PayPal account. All the CD tools look like they require the latter to access.

---

### Post by beausimon on 2006-07-04
If you can't boot from CD, perhaps you should check your BIOS to ensure that you select booting from CD as first boot choice.

You can download freedos ISO to make a bootable CD from the this site: [http://freedos.sourceforge.net/freedos/files/](http://freedos.sourceforge.net/freedos/files/)   .  I have used this successfully to restore my MBR before and it's free.

---

### Post by TS1 on 2006-07-04
[QUOTE=beausimon]If you can't boot from CD, perhaps you should check your BIOS to ensure that you select booting from CD as first boot choice.

You can download freedos ISO to make a bootable CD from the this site: [http://freedos.sourceforge.net/freedos/files/](http://freedos.sourceforge.net/freedos/files/)   .  I have used this successfully to restore my MBR before and it's free.[/QUOTE] My boot order is as follows:

```
  CD-ROM/DVD Drive
 -Hard Drive
      TOSHIBA MK6021GAS-(PM)
 -Removable Devices
      Legacy Floppy Drives
! Network Boot
```

...where an exclamation mark represents disabled. And unfortunately, I tried downloading FreeDOS and burning it to a CD, but it's not reading that either, even when I explicitly select CD drive from the boot menu.

---

### Post by xeniter on 2007-08-31
i have had same problem

i have change many bios settings, after that it worked

maybe you must change the lba, normal, or large setting for your hdd

i have changed many settings so i cant say what it was, after that grubs works and it boot the linux

mfg xeniter

---

### Post by brad1138 on 2008-01-08
I had this problem, I googled for it and found a post that said "error 2" means Grub is not seeing the drive/partition Linux is located on properly. I had just been playing around in BIOS before the problem. I had loaded "best performance" option, so I tried going back to "optimal" but that didn't help, What did work was having the BIOS re-detect the HDs (it had defaulted to "auto" after selection best/optimal). After re-detecting the HDs it booted fine.

Brad

---

