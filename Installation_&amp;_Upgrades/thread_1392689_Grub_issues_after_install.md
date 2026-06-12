---
title: "Grub issues after install"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by R3M3 on 2010-01-28
I "upgraded" to 9.10 (karmic) by doing a clean install with the main install CD. Unfortunately, my system is not wanting to boot, dumping me to the grub rescue prompt.

My disk setup is slightly off, with three hard drives, two IDE and one SATA. 

Under the liveCD, here's how my drives are set up

hda - SATA
 hda1 - ext3 /media/storage
hdb - IDE
 hdb1 - fat32 /dos
 hdb2 - ext4 /home
 hdb3 - ext3 /aux
 hdb4 - ext4 /
hdc - IDE
 hdc1 - swap

(ext4 and swap partitions were reformatted during installation)

However, under the Grub rescue prompt, I get the following correspondence (confirmed by using ls):

(hd0) -> hdb
(hd1) -> hdc
(hd2) -> hda

I have tried reinstalling grub using both
grub-install /dev/hda
grub-install /dev/hdb

Neither seems to help.

The real stumper is that when I do a 
grub rescue>ls (hd0,4)/  #This should be the root partition
I get an "Error: unknown filesystem"

However, booting into the LiveCD and running "fsck /dev/hdb4" does not report any issues.

Any thoughts?

---

### Post by oldfred on 2010-01-28
I do not know if I have an answer for you, other may have seen your exact issue.  Some BIOS seem to promote IDE drives to first in the drive order. Grub2, old grub, windows and Ubuntu do not always identify drives in the same order which of course leads us to confusion. I would suggest because of these issues you make sure all your install is one one drive. Grub2 should be in the MBR, all system partitions should be on that drive including swap. While the use of UUID's is supposed to eliminate drive/partition confusion, there still seem to be many places where drives are identified by drive number & partition number. Can you choose boot drive in BIOS? We have also seen where the settings on the IDE chain (master/slave) can make a difference. Since that is a physical setting you have to verify that inside you system. The rest should be controlled by the BIOS.

So we can see your entire configuration:

Follow these instruction to run the boot info script and post the RESULTS.txt.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by R3M3 on 2010-01-29
Well, the issue wasn't with the boot order, as I was able to go into the BIOS* and set it so that the boot order matched the order of harddrives that linux reported, but this had no effect on my booting issue, even when grub or Ubuntu itself was reinstalled. (* Although I think this might not be strictly speaking necessary - I've run across some hints that by altering the file /boot/grub/devices.map and re-running grub-install you can tell grub how the grub-disk-order/linux-disk-order match up.)

I think the issue comes back to grub not recognizing the filesystem on /dev/sdb4 (the location of the kernel image), despite it checking out fine with fsck. On a whim, I redid the Ubuntu installation, flipping /home and / (so the partition with the kernel image is now /dev/sdb2). This time everything worked fine, and I was able to boot and login.

My only lingering concern, now that I can boot, is why grub was having an issue recognizing the filesystem on /dev/sdb4, and if I will have any problems having my /home partition there.

---

### Post by oldfred on 2010-01-29
If it is an older system, there are BIOS limits. You then cannot boot from files that are beyond the limit.

In old grub it was error 18 and it could be BIOS settings or hardware configuration with IDE drives.

See Herman's explanation:
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

---

