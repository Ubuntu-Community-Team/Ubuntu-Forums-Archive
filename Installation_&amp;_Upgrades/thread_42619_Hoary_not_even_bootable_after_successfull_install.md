---
title: "Hoary not even bootable after successfull install"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by mrbit on 2005-06-18
could be hardware, it's all brand new, but after a successful hoary install i just can't boot from my hard disk

it's a DFI motherboard (groan, i think that was a mistake) model nF4-DAGF with 
processor AMD64 Athlon 3200+ also, 2GB of ram (do you care what brand?)

and a Maxtor 40GB hdd (which wasn't new...) - it's the master on the first ide bus, i've disabled the SATA bus(es) as i won't be using them for a little while

i booted back up using my other livecd and checked out hda1 (the hdd) and everything seems to be there, fdisk -l says hda1 is bootable... i'm stumped.  i did the install twice, same thing both times, the machine just halts citing no OS available...

yeah this guy knows:  ](*,) 

thanks y'all

=====================================

some replies, and responses to this post when i posted it to another forum:

>Are you getting as far as the grub prompt ?
no.  i get a message that says "DISK BOOT FAILURE.  INSERT SYSTEM DISK" (that's close, but not exact..)

>Have you checked your bios to see if you have write-protected the mbr ?
well, couldn't find that, so can't say for sure

>Check the boot sequence on your bios, also that the IDE cables arent crossed
yep, in livecd i've got it as hda1 - that is evidence enough right...


>best to use ext3 for debian/ubuntu
ext3, check.  using all the "recommended" partitioning ubuntu provides, just hitting enter...


>Stick with Grub bootloader rather than lilo,

>On an old hard drive which has had a previous linux install, check the partition table with cfdisk, 
> to ensure the partition table isnt corrupted. Mandrake is bad for this. I once had a hard 
> drive which reported different conditions depending on whether i used fdisk or cfdisk.

did the chroot grub-install (didn't help) - not sure how to specify "to mbr"  also did this: on first stage of ubuntu install, before it rebooted i hit "go back" and ran the "install grub bootloader" again... just to be sure.  same thing.  then i installed warthog, still same thing.  think maybe that this disk just can't boot for some reason?

Also if you can boot using the live cd, mount your partitions, do a chroot, then grub-install to the mbr, and see if you get any error messages.

---

### Post by blind0wl on 2005-06-19
If your not even getting to grub, Id definately be worried about a hardware issue.  Does your 40Gb (assuming its the only one) say its on the Primary IDE as a Master in bios?  Does the bootup sequence say its detected a hard-drive?

---

### Post by mingus on 2005-06-20
There are other possibilities . . . the error you're getting suggests that the hand-off from the BIOS to stage1 to stage2 of the boot loader is broken.  This sounds like grub wasn't installed to the MBR and/or there is a problem with what was in the MBR and/or the partition table is corrupt and/or the BIOS can't properly access the system partition (i.e, the /boot partition), etc.

* Double-check the BIOS boot sequence.  Put the HDD first.

* Can this BIOS boot beyond the 1024 cyclinder limit?  Have you set the drive to LBA in BIOS setup?
What is your partitioning; specifically, where is /boot?

* What was the Maxtor used for before?  Anything by chance ever written to its MBR?  

* Using the live-cd, try to mount the disk.  (What fdisk sees is immaterial; it's only looking at the partition table.)  Then read a file (cat /somedirectory/sometextfile) and then try to write a file (#nano will open a simple text editor).

---

### Post by mrbit on 2005-06-22
alright - after much frustration i got it.  i hate to admit this but we needed closure here: the issue is not software.    it was in a hard drive "drawer" (plastic thing, cold-swapable) and though it posted in the bios correctly it didn't seem to get "spun up" enough (?) to respond to the bios when it polled for boot records. putting the bootable drive on the ide cable directly solved it, and the drive in the drawer is still usable - just don't boot from the drawer.  keep your boots on the floor.  

sigh.  but thanks!

---

### Post by mingus on 2005-06-22
mrbit -

Thx much for replying back and sharing the problem/resolution.  That is instructive for all and also shows recognition for efforts to assist, which is appreciated.

---

