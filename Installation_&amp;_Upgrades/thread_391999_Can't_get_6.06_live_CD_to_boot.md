---
title: "Can't get 6.06 live CD to boot"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by JoshMock on 2007-03-24
I'm booting from the 6.06 Live CD and when it tries to boot, it gets stuck loading GRUB, with an Error 17.

I looked up Error 17 so I know it's because it can't recognize the partition.  I don't know why the live CD would even care what partitions are on the hard drive, though.  Isn't that the point of a using a live CD?

Anyway, the hard drive is a 40 GB that just has a primary DOS partition that I created using fdisk on a 98 boot floppy.

Help?

---

### Post by dan_linder on 2007-03-24
Just to be sure it isn't complaining about the CD, can you run the Check CD option when you boot and verify it is correct?

---

### Post by JoshMock on 2007-03-24
It's a Live CD that was mailed to me and have used before successfully.  I used to have Windows 2000 on this machine and the Live CD worked then.  The hard drive has since been reformatted using a 98 boot disk.

How would I run the Check CD option anyway?  There's never any place for me to make any options as the boot is failing before even getting to the Ubuntu progress screen.

---

### Post by JoshMock on 2007-03-24
Just an update on symptoms:

The Error 17 thing happens even when the Live CD is not in the drive.  Weird?  Very.

This is after I've deleted all the partitions, recreated one primary DOS partition and formatted it as FAT32.

I'm reformatting again right now.  Will see what happens.

---

### Post by bulldog on 2007-03-24
> **JoshMock said:**
> Just an update on symptoms:

The Error 17 thing happens even when the Live CD is not in the drive.  Weird?  Very.

This is after I've deleted all the partitions, recreated one primary DOS partition and formatted it as FAT32.

I'm reformatting again right now.  Will see what happens.

It seems to me you're not booting the live cd but your hard drive.
GRUB isn't installed when you use the live cd so you shouldn't see it.
Try to boot from the cd and in the menu you see an option to check the cd on errors.

---

### Post by JoshMock on 2007-03-25
Is it possible that, since I've had Ubuntu installed on the drive before (even though I've since reformatted), it's finding some remnants of GRUB somehow?

The boot order in BIOS is currently (1) Floppy, (2) CD-ROM, (3) HDD.  Maybe I'll disable boot from HDD completely to see what that does.

---

### Post by bulldog on 2007-03-25
Only formatting doesn't affect the MBR,so it's possible there are left overs from a previous GRUB.

But if you boot from the live cd,you shouldn't see this because it's written to the hard disk.

So basically,if you boot the cd-rom,your hard disk isn't used at all and you shouldn't see anything of this.

---

### Post by JoshMock on 2007-03-25
A friend suggested using *fdisk /mbr* (DOS fdisk), which rewrites the MBR.  I tried that and it still gave me an error

Removing HDD from the boot order list completely seems to have worked.  Thanks for your pointer.  It helped the light bulb go on in my head about how stupid my BIOS must be.

---

