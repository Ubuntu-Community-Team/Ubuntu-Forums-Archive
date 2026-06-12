---
title: "Installing via pcmcia cdrom drive?"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by galning on 2008-06-10
I need some help installing Ubuntu (8.04) on my thinkpad X21.

It doesn't have an internal cdrom drive, so its not as easy as normally.  I have a pcmcia cdrom drive, but my laptop doesn't have an option to boot from it (it might have something to do with how it draws power from the pcmcia slot, instead of an adapter)  And no, i don't have access to a usb cd rom drive.

I have a usb floppy drive, that i've used before, and it works fine.  But i can't seem to find a way to make a boot disk that will allow me to boot the cdrom drive.  (I've used Boot manager, but it doesn't detect the cdrom)

I'm a little skeptical about attempting to install via flash drive, because i'm honestly not too sure if syslinux will reformat my flashdrive.  And i can't exactly do a net install, due to my computer's lack of internal Ethernet port.

If anyone has any suggestions, I'm all ears.

---

### Post by wolfen69 on 2008-06-10
what are the computer's specs? my guess is that it's old. i would not try to run 8.04 if you have less than 384 MB.

---

### Post by galning on 2008-06-10
192mb ram, 700mhz PIII moble, 20gb hard drive.

---

### Post by galning on 2008-06-11
anyone have any ideas?

---

### Post by galning on 2008-06-11
well, i've managed to get the disk to boot, using instlux.  I've jumped to installing Ubuntu 6.06, because thats the version that matched the instlux that i have.

Its running alright, but it can't read data from the cdrom.  I keep getting errors, and i've checked the intgrity of it (it was fine).  Anyone have any suggestions?

---

### Post by peakshysteria on 2008-06-11
What about giving [Xubuntu]("http://www.xubuntu.org/") a shot?

Minimum system requirements:

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.

6.06. doesn't seem right in 2008. At least not in my end.

---

### Post by galning on 2008-06-11
> **peakshysteria said:**
> What about giving [Xubuntu]("http://www.xubuntu.org/") a shot?

Minimum system requirements:

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.

6.06. doesn't seem right in 2008. At least not in my end.I wouldn't mind that.  Its just the whole installation thing that i'm having a problem with.  I need something with a boot disk.  Or a way to get it to load off of the cd, like instlux.

---

### Post by galning on 2008-06-12
Alright, i've gotten Xubuntu to start installation via unetbootin, but i keep getting a read error from my cd.  Its the same one i encountered before, and the disk's intregdy is fine.

Does anyone know how to fix this? (At this point, i'm tempted to just say "forget it" and go with Debian, which actually has boot disks.)

---

