---
title: "Adding Windows XP to a second disk"
date: 2006-03-31
forum: Installation &amp; Upgrades
---

### Post by v-gudmk on 2006-03-31
I have ubuntu running on /dev/hda, and I already have an NTFS partition on /dev/hdb where I want to install windows XP.

I'm following this howto: [http://www.tldp.org/HOWTO/Linux+Win9x+Grub-HOWTO/proc.html]("http://www.tldp.org/HOWTO/Linux+Win9x+Grub-HOWTO/proc.html")

Everything fits my situation exactly except I don't have a floppy drive, so I can't use this grub entry:
title DOS Boot Disk
	map (hd0,0) (hd0,2)
	map (hd0,2) (hd0,0)
	chainloader (fd0)+1

So instead I need to use the CDROM drive too jump to the windows XP installation CD.  The howto says: 

"If your Windows install CD is bootable, you'll need to have a "Windows boot disk" section which chainloads to whatever your CDROM device is called."

But I can't figure out how to do this.  I've tried to edit device.map and put
(hd2) /dev/hdc
in there, but this doesn't work, I get an error that the disk (cdrom) doesn't exist.

Can anyone tell me how to make grub chainload to the cdrom drive?

---

### Post by Stealth on 2006-03-31
Mmmm...what exactly are you trying to do? WinXP should automatically boot the CD, and after you install it in your NTFS partition, you would [need to reinstall GRUB]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows") so you can boot back into either OS's...it shouldn't take you much more than that.

---

### Post by v-gudmk on 2006-03-31
When I boot directly to the windows XP installation CD and try to install XP on the NTFS filesystem on disk 2 (/dev/hdb) it complains that it has to write installation files to disk1 and that there is no windows partition to do that on disk1.  I have only the ubuntu filesystem and swap on disk1.  I was hoping to use grub as described in the howto to "fool" the windows installer into thinking disk2 is the C: drive.

---

### Post by v-gudmk on 2006-03-31
I have fixed my own problem.  Without a floppy drive, the HOWTO just doesn't work.
So I swapped the master/slave modes of the physical disks.
After that I was able to install Windows XP on the C: drive (the disk which used to be /dev/hdb).
But now I had to restore grub to the /dev/hda disk.  So I followed the instructions of the page that Stealth pointed me to ([https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows") ) - thank you.

I used the "Using the LiveCD and Overwriting the Windows bootloader" section.
Except it took me a while to figure out two things:
 1. You have to use "sudo grub", otherwise it'll tell you the disk(s) don't exist.
 2. I used root (hd1,0) and at first I thought I should use setup (hd1), but that was wrong, it should be setup (hd0) because that's the disk that is first in the boot order, so grub should be installed there - over the windows bootloader.

Then I used the LiveCD and mounted /dev/hdb1 on /mnt/disk2 like this:

sudo mkdir /mnt/disk2
sudo mount /dev/hdb1 /mnt/disk2

After I changed the /mnt/disk2/boot/grub/menu.lst file and changed all occurrences of /dev/hda to /dev/hdb and changed hd0 to hd1 for linux and hd0 to hd1 for Windows XP, I can now dual boot to either system !!  
Whew.

---

