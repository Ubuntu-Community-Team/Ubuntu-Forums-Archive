---
title: "Xubuntu 14.10 install cd won't boot."
date: 2015-03-09
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2015-03-09
Hi,

I'm trying to install Xubuntu 14.10 on amd64, on a first-gen i7 desktop.

I downloaded this: [xubuntu-14.10-desktop-amd64.iso]("http://ftp.ussg.iu.edu/linux/xubuntu/14.10/release/xubuntu-14.10-desktop-amd64.iso") and checked the md5sum, it's good.

I burned it on a Mac (no other way right now) and it won't boot.

I also tried mini.iso, it fails with the same error.

Error:


```

GRUB loading.
Welcome to GRUB!

error: file '/grub/i386-pc/normal.mod' not found.
Entering rescue mode...
grub rescue>  _

```

I know I selected the 64-bit iso, I downloaded it several times from different mirrors.

Can somebody get me started?

Thanks.

---

### Post by oldfred on 2015-03-10
Do not know if Mac writes file differently somehow?

But normal not found is usually an install being booted in the wrong boot mode. Or an UEFI install trying to boot in BIOS or vice-versa. But an installer has both modes, and if your system is an i7 it should be UEFI although perhaps an early version. Is UEFI/BIOS the most current version from vendor?

Also:
[http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found](http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found)

---

### Post by 1clue on 2015-03-10
It's an i7 920 on an Asus P6T motherboard.  Nothing mentioned in the docs I see about EUFI, but I have the disk partitioned as GPT.  This box has never booted anything but Linux.  It's had various Ubuntus, Gentoo and a couple other distros.  Never tried Ubuntu 14.x, so this is new.  Earlier I tried arch and decided it was too much work for now, so I need to just get it up and working.

I haven't tried a new BIOS image, will check but it's a pretty old board so I kinda doubt it.

I got it to boot sort-of from a USB stick (had to buy a new one, the one I was using had a bad spot evidently) but the installer still fails.

This box has a new OCZ Vector 150 240g ssd on it, and a bunch of WD green drives which seem to be going bad.  This is the last bunch out of 10 or so I bought not all that long ago and they're down to 4 still spinning, gonna give WD a pass for a few years because of this.

I'm going to try to remove the spinners completely for now so I can just use the SSD.  That won't work for my ultimate plan but if these drives are failing they won't do me any good anyway, and I can't just run out to the store and get drives where I'm at.

I'll look at your links shortly.

Thanks.

---

### Post by 1clue on 2015-03-10
BTW I had to use unetbootin to get a bootable USB drive on Mac.

---

### Post by oldfred on 2015-03-10
Is it perhaps not booting flash drive and then dropping back to an old install of grub in MBR of default hard drive/SSD that is not fully there?

I do not think a grub rescue is normal with a flash drive install. 
And if in BIOS mode, you would boot flash drive with syslinux not grub. 
Only if UEFI mode do you boot flash drive installer with grub.

---

### Post by 1clue on 2015-03-10
Sorry for the confusion.  The original post was from an iso burned onto a dvd.

The semi-working installer which actually gets a gui but with lots of errors is from a usb flash drive containing the same iso.

---

### Post by oldfred on 2015-03-10
The is it a video driver issue?
What video card/chip? Internal Intel or video card?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

 Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by 1clue on 2015-03-10
I don't think it's a video driver issue.  It's an nvidia GeForce 260 card (from memory), *buntu and most other distros have always automatically discovered and properly handled it.

The CDROM boot never got past bios, but the usb stick boot got into a gui, so it found the card.  It appears that the unetbootin image on the usb stick wants to write back to flash and the drive is locked, but in my hurry to get the smallest drive I neglected to make sure it has an LED or a lock.

I'm perfectly happy with a command-line install, but basically right now I just want the @#%@^ thing up and running, I have work to do.

Again, will get back to this later.

Thanks.

---

### Post by 1clue on 2015-03-12
In an effort to get things moving I rewrote my usb stick as xubuntu 14.04 and it's working normally now.

Not exactly what I wanted to do but getting the machine to work is far more important than getting bleeding edge software on it.

Thanks, problem solved for now.

---

