---
title: "SATA problems on an Asus A7N8X2.0"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by thedash on 2006-09-29
I have used Ubuntu for a while now, recently upgraded from 5.10 to 6.06.  My system atm is an Asus A7N8X Deluxe 2.0 with an AMD Athlon XP 3200+, 2GB of PC3200 Samsung DDR, in single-channel, Raden 9800 Pro, etc.  My problem came in the past few days when I tried to add a new hard drive.

Previously, I had a 80GB OS drive [dual-boot], and a 200GB media drive [games, music, etc], both drives IDE.  I have since upgraded to a 400GB SATA and the same 200GB IDE, media and OS, respectively, and again a dual-boot.

However, if I mount the SATA drive in Linux, my PC slows down a lot, will pause for 3-4 seconds about every 10 seconds if the SATA drive is active at all.  If I leave it unmounted, the PC functions normally [which, in my case, means it has an uptime of about 3 hours].  The drive does not show at all in Windows.

I believe I have traced the issue to the Silicon Image SATA controller on my motherboard.  I believe it is a Sil3112A, but I am not entirely sure on this, as I have not been able to find out how to check, other than by trial and error [and apparently everybody on Freenode ignores me].  It appears the version is 0.9.  I have googled this for the past few days, looking through older stuff, and I can't find any recent examples of this [there are thousands of similar questions, but they are all from three or four years ago].

I am no Linux guru by any means, but I can usually stumble my way around the system pretty well, once I get it running.  I would like to be able to use this drive, as its a good drive, and I paid a bit more than I should have for it.

Anybody have any similar experiences, or perhaps know how to remedy this?

---

### Post by morphodone on 2006-09-29
Are there anymore sata ports on that motherboard?

I seem to recall having an asus board that had Silicon Image controller
and a via controller...although yours would probably be an nvidia one.

You could try one of the other sata controllers.
Just be sure to enable it in the bios.


I think I may have that board in one of my pc's.

---

### Post by thedash on 2006-09-29
Yeh, it has another.  I was under the impression that both were run by the Sil3112 [as compared to the Sil3114, which has 4 SATA ports], but I'll check.

---

### Post by pseudonym on 2006-09-30
You should check out the forums at [www.nforcershq.com](www.nforcershq.com) , if you haven't already. Among many other useful tips, you will be able to get hold of a modded BIOS which includes an updated SATA BIOS for the Sil3112A controller. I'm currently running BIOS 1008mod3 with 4.2.76 SATA BIOS and it's very stable. THis could help with your issue (ASUS won't have anything new because it's a previous generation motherboard).

Also, I am assuming your new drive is SATA2? If you haven't done so already, I recommend jumpering it to SATA 150 speed (to match the controller), according to the drive's instructions. The controller is supposed to be able to autonegotiate but I think it's safer just to jumper the drive.

It's also a good idea to disable all unnecessary disk services at bootup (in fact, any unnecessary services) if you don't use them - lvm, mdadm, evms. A guide on this can be found [here]("http://www.ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf").

Once you sort out your disk issues, one other thing which I highly recommend to other owners of this m/b is using the nvidia OSS nvsound driver instead of ALSA for your audio. The (big) advantages are hardware mixing, better sound quality, and use of the Soundstorm APU for Dolby digital. The Ubuntu howto for setting it up is [here]("http://www.ubuntuforums.org/showthread.php?t=253725&highlight=soundstorm").

HTH

---

### Post by BoneKracker on 2006-09-30
In case it might be of use, you can download the manual for the mobo at the Asus web site (same place you get drivers).

---

### Post by morphodone on 2006-09-30
> **pseudonym said:**
> I recommend jumpering it to SATA 150 speed (to match the controller), according to the drive's instructions. The controller is supposed to be able to autonegotiate but I think it's safer just to jumper the drive.

yeah, i had that problem too with and abit board...this is an excellent suggestion

---

### Post by BoneKracker on 2006-10-01
On my A8n board, the silicon image controller is SATA and the nVidia controller is SATA-2.

---

### Post by raphha on 2006-10-01
I had a lot of and quite similar trouble with SATA disks and dapper, too. Only kanotix didn't have any problems...until by chance I switched of ACPI by using the "acpi=off" boot parameter (you know, when grub loads, press "e", then edit the command line and type "b" to boot...)
I don't know the exact reasons and implications, but I never had any problems thereafter...

good luck,
raph

---

### Post by BoneKracker on 2006-10-01
I have had no trouble with SATA in ubuntu (breezy or dapper).

---

### Post by raphha on 2006-10-02
The troubles only occured when I had more than one disk on one sata controller. I wanted to setup a raid5 array during installation... With a single disk, I didn't have any troubles neither. (that was with a nforce 430 chipset)

raph

---

