---
title: "Newbie install problem"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by josephmo on 2008-06-30
I started out with a Vista 32 system, 2 SATA drives (500GB each), one is primary and the second for backup (AHCI mode, non-RAID).

I installed a spare 250GB SATA disk I had as drive 3, and wanted to install Linux on it. I bought a special magazine supplement that came with the install DVD. Being a newbie, I ended up with a GRUB on the Vista disk. Next I added a fourth SATA drive, this one was 100GB. I could not boot, something about GRUB and error code 15 (I think). OK, so I find my Vista install CD, boot into a command prompt, bootrec.exe /fixmbr later, no more GRUB bootup sequence and I go straight into Vista.

Vista no longer sees the third drive. Booting up from the UBUNTU 8.04 CD (I made one), I can see it, but when I try to mount it, UBUNTU tells me that it cannot do it. It does not tell me why. I reformatted it to NFS. When I'm in Vista, it does not see it at all. When I'm in the BIOS it clearly sees it.

What's going on? I want to go back and install UBUNTU on drive 3, but I want to disable the two other drives, install UBUNTU on drive 3, and then select which OS to boot into through a BIOS option (F8 allows me to select which drive to boot from). I think that's less of a headache in the long run. In the short term, what happened to drive 3?

---

### Post by logos34 on 2008-06-30
> **josephmo said:**
> ... ended up with a GRUB on the Vista disk. Next I added a fourth SATA drive, this one was 100GB. I could not boot, something about GRUB and error code 15 (I think). 

Grub installs by default to the boot drive (i.e. 'hd0')--in this case, vista.

I think what happened is that as soon as you connected the last sata, it jumped ahead of the linux drive in the boot order, throwing off the Bios address as listed in grub menu.lst.  Try swapping the sata ports each drive is connected to on the motherboard, and recheck the Bios hard disk boot order afterward to make sure the linux drive is 3rd.

>  Vista no longer sees the third drive. Booting up from the UBUNTU 8.04 CD (I made one), I can see it, but when I try to mount it, UBUNTU tells me that it cannot do it. It does not tell me why. I reformatted it to NFS. When I'm in Vista, it does not see it at all. When I'm in the BIOS it clearly sees it.

Actually, vista (windows) cannot natively read linux filesystems (all it should have shown is 'unknown' space in disk storage mgmt.).  That's normal. You can fix that by installing fs-driver to give you access to ext3 linux partition. But you should be able to mount your linux partition from the live cd.  Not sure what the problem is, since it clearly is working/shows up in fdisk. Maybe run 

sudo fsck /dev/sdc1 

(or whatever root is)

>  What's going on? I want to go back and install UBUNTU on drive 3, but I want to disable the two other drives, install UBUNTU on drive 3, and then select which OS to boot into through a BIOS option (F8 allows me to select which drive to boot from). I think that's less of a headache in the long run. In the short term, what happened to drive 3?

I'd try this:

-unplug the other drives except for the vista disk and ubuntu. 

-plug ubuntu into sata channel 1 port/connector on the mobo and vista into channel 2.

-set the ubuntu drive **first** in the Bios hard disk boot order.

-reinstall ubuntu.  Hopefully it will see that the ubuntu drive is the boot drive (hd0), and install grub bootloader on that drive's MBR.  Also, it should detect vista and add the appropriate boot entry in menu.lst so you have a choice of either OS at startup.

-if it works and you can boot either OS, then connect the other drives.

---

### Post by josephmo on 2008-07-01
"I think what happened is that as soon as you connected the last sata, it jumped ahead of the linux drive in the boot order, throwing off the Bios address as listed in grub menu.lst."

No, I did check for that. When I booted from the CD, the order remained the same, and in the BIOS, the order remained th same.

"Actually, vista (windows) cannot natively read linux filesystems (all it should have shown is 'unknown' space in disk storage mgmt.). That's normal. You can fix that by installing fs-driver to give you access to ext3 linux partition. But you should be able to mount your linux partition from the live cd. Not sure what the problem is, since it clearly is working/shows up in fdisk. Maybe run 

sudo fsck /dev/sdc1"

I was using a freeware disk utility (does not ship with Vista), and that's capable of recognizing ext3 partitions. I will try your suggestion and see what happens.

I've already tried some of your other suggestions, but I will do a few more things. This is a bit frustrating. One thing for sure, I am getting more information in Linux than I am in Vista, but Linux seems to be real fragile when you do something extra (like adding another SATA drive, and I'm talking about the fourth SATA drive)

---

### Post by logos34 on 2008-07-01
maybe AHCI is part of the problem.  You might look into switching back to IDE emulation mode (but then you won't have hot-swapping and NCQ features, not usually a big deal on average desktop).

> I reformatted it to NFS. When I'm in Vista, it does not see it at all. When I'm in the BIOS it clearly sees it.

I wonder why.  You couldn't mount it from the live cd when it was ext3, and after reformtting to ntfs vista doesn't see it.  Use gparted on the live cd to delete the ntfs partition, so that the whole disk is unallocated space.  Maybe vista will see it then. dunno

---

### Post by upchucky on 2008-07-01
the first hint was error code 15, grub simply did not get told where the new drive was installed and is using the old drive order which was changed by adding the new drive. put everything back the way it was physically. use partimage to see the drives, write down their order hda1, hda2,sdb, or what ever you have in the sys.

once you know where everything is, edit /boot/grub/menu.lst to tell grub where the drives are.

if grub changed the windows bootloader and win or ubuntu will not boot supergrub can fix it.

---

### Post by josephmo on 2008-07-01
I already tried gparted and it's telling me that "error occurred while carrying out the operations", when I try to delete the partition. It sees all three disks fine, and it's telling me that the current partition is NTFS.

---

### Post by josephmo on 2008-07-01
> **upchucky said:**
> the first hint was error code 15, grub simply did not get told where the new drive was installed and is using the old drive order which was changed by adding the new drive. put everything back the way it was physically. use partimage to see the drives, write down their order hda1, hda2,sdb, or what ever you have in the sys.

once you know where everything is, edit /boot/grub/menu.lst to tell grub where the drives are.

if grub changed the windows bootloader and win or ubuntu will not boot supergrub can fix it.

There is no new drive. I'm at the original three drives, and they're in the same exact order. The original boot disk does not have a GRUB on it as far as I can tell (I ran the Vista install CD and did a fixmbr). The third drive that had Linux on it was successfully formated at one point by gparted as an NTFS drive, so it has no data on it (although gparted is telling me it has some 80MB of data on it, which I assume is the NTFS formatting footprint).

---

### Post by logos34 on 2008-07-01
I'd try reinstalling ubuntu, either like it's arranged now (same as originally but maybe put grub on floppy to prevent overwriting vista mbr), or as I suggested above--linux drive first with bootloader there.  But that still leaves the problem of adding the fourth drive...Upchucky's way is better--just edit menu.lst to reflect the new disk boot order and reinstall grub.

---

