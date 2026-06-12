---
title: "Install issues io?"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by comintern on 2008-03-30
Apparently I have a knack for putting together systems that Ubuntu doesn't want to play nice with (had to run Gentoo on the last box I put together).  I've been trying to get 7.10/64 to install on my system for days now.  Specs:

Gigabyte P35C-DS3R motherboard
Intel Core 2 Quad 6600
2GB Crucial DDR2 @1066
Nvidia 8600GT
500GB WD SATA
LiteOn DVD burner (also SATA)

The problem seems to be something to do with the SATA controller.  I can get into a live CD session without problems (have to boot without quiet or splash, but that's probably the Nvidia talking).  The install starts fine, but never gets past about 50% of installing the system.  I found a couple threads about problems in the guided partitioning, so I've been attempting manual partitioning in the alternative text installer with no joy.  I thought it might be the media I'm using, but gave up after my 5th new CD passed checksum.  I tried the alternative installation, no luck there either -- I still get io errors.  The strange thing is that with a bad burn, I would expect the installer to stop at the same files, but it seems to be all over the map.

Memory test checks out fine (I let it run overnight with no errors).
The HD worked flawlessly under XP, as did the DVD drive.
I did have to change the BIOS setting out of AHCI mode and into IDE mode to get the live CD to boot.
The ACPI also gave me issues until I changed it to 64 bit HPET mode (duh).
I flashed the BIOS to the lastest revision sometime yesterday, didn't notice any changes.

I saw a lot of people were having problems with the P35 chipset, but also others that had similar setups without issues.  Anyone have ideas?  I running out of them.

---

### Post by Pumalite on 2008-03-30
If you can afford it, take Ubuntu Hardy Heron Beta for a spin (64 bit)

---

### Post by comintern on 2008-03-30
> **Pumalite said:**
> If you can afford it, take Ubuntu Hardy Heron Beta for a spin (64 bit)

Hardy Heron presents a different issue.  I get:

```
SQUASHFS Error:  Unable to read page block...
```

---

### Post by Pumalite on 2008-03-30
Too bad. I can't help you there.

---

### Post by comintern on 2008-03-30
> **Pumalite said:**
> Too bad. I can't help you there.

Thanks, you've been a tremendous help.

---

### Post by Maintech on 2008-03-30
My issue is similar to yours. I run the IP35 chipset. I have been  unable to get it to boot at all. It tries to load the 2-port ICHR-9 driver instead of the 4 port first and then the 2-port. I can run SuSE and Mandriva and other RPM based linux and when I watch the boot sequence that is how they load the Hard Drive drivers, 4-port first then 2-port. Ubuntu doesn't even try to load the 4-port. I have 4 SATA drives so I have no choice in which driver is loaded. So far, I have had no replies in Ubuntu as to how to make it work. Too bad. Guess I'll stay with SuSE 10.3 whether I like it or not.

---

### Post by comintern on 2008-03-30
> **Maintech said:**
> My issue is similar to yours. I run the IP35 chipset. I have been  unable to get it to boot at all. It tries to load the 2-port ICHR-9 driver instead of the 4 port first and then the 2-port. I can run SuSE and Mandriva and other RPM based linux and when I watch the boot sequence that is how they load the Hard Drive drivers, 4-port first then 2-port. Ubuntu doesn't even try to load the 4-port. I have 4 SATA drives so I have no choice in which driver is loaded. So far, I have had no replies in Ubuntu as to how to make it work. Too bad. Guess I'll stay with SuSE 10.3 whether I like it or not.

Well, I finally got an install onto a hard drive.  I pulled all the SATA stuff out, switched to legacy IDE mode, removed the card reader, and installed to an old Maxtor IDE drive from a 5 year old CDROM drive.  It seems to run OK, so I may try to image the drive over to the SATA one on my other system and try turning the SATA on again.  If that doesn't work, I'll probably give Fedora a shot (they usually have the more bleeding edge hardware support).

---

