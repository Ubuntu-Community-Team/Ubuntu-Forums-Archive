---
title: "no first boot"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by kenji-san on 2007-09-06
Greetings all.  First post!  :)

I am encountering a problem with a new Ubuntu feisty i386 install.  The system will not boot after installation.  This system is single boot only.

Here is my relevant hardware:
ASUS M2N motherboard
AMD X2 AM2 3800+ proc
1GB DDR2
NVIDIA 7300GS
Western Digital SATA drive (system drive)
Maxtor ATA drive on PCI add-on EIO RAID controller used as an ATA controller (data drive)

I installed Ubuntu to the SATA system drive with this config per instructions I found here about XFS:
/boot - ext3
swap
/ - XFS
EXTENDED PARTITION
  /home - XFS
  extra space

This drive had previously been formated as a UFS slice for freeBSD.  When I had installed the system, the data drive was sda and the system drive was sdb.

Installation created no errors and when I rebooted I got a message stating that I needed to insert the boot medium.  I rebooted into the liveCD and checked my partitions.  I noticed that /boot was not set with the 'boot' flag, so I set it with the partition editor.

Upon reboot, I got the message "missing operating system"

I reinstalled with this config:
/ - ext3
swap
EXTENDED PARTITION
  /home - XFS
  extra space

I got the same errors and had to set the boot flag again.  What was strange was that when I rebooted the liveCD, the data drive was now sdb and the system drive was sda.  Somehow it swapped priority or something.  The bios is set to boot the SATA drive.

The only solution I can think of is to physically disconnect my data drive and reinstall the system, reboot to verify and then reconnect my data drive.

Any suggestions?  Thank you!

---

### Post by kenji-san on 2007-09-10
The problem was that** Ubuntu installed GRUB to my data drive** and not the install drive.  That was a slap in the face.  Why would the installer do this?  My motherboard is not set to boot that drive.

I unplugged my data drive and then reinstalled.  That fixed it.  I resolved my drive recognition issues with UUID.

Now my problem is that I have a partition that I use very infrequently and I like to have it set to 'noauto' in my fstab.  When I do that, I get a link to the partition on the desktop.  Is there any way to get it off my desktop?  My temporary solution is to remove the 'noauto' option and have it mounted all the time.

---

### Post by Herman on 2007-09-10
Hello kenji-san,
You shouldn't need to worry about setting the boot flag if you are using GRUB, because GRUB will normally do that for you automatically with it's 'makeactive' command. :)

If you want a partition to be mounted, but you don't like having an icon for it showing on your Desktop, then a simple solution would be to mount it in /mnt instead of in /media. That should solve your problem. Just make a new directory for it in /mnt, and edit /etc/fstab to mount it there instead.

Regards, Herman :)

---

### Post by Herman on 2007-09-10
Another idea you might like to consider is to not even have it mounted in /etc/fstab at all, (hash out the entry for it). You can make a script for mounting it just when you want to, all you need to do is click on the script and click 'run in terminal', and your file system will be mounted. Here's a link for more info on that, [COLOR=#666666][COLOR=#000000][Making a script for mounting your other filesystems instantly]("http://users.bigpond.net.au/hermanzone/p10.htm#Make_a_mounting_script") [/COLOR][/COLOR]

---

### Post by kenji-san on 2007-09-10
> **Herman said:**
> Hello kenji-san,
You shouldn't need to worry about setting the boot flag if you are using GRUB, because GRUB will normally do that for you automatically with it's 'makeactive' command. :)

If you want a partition to be mounted, but you don't like having an icon for it showing on your Desktop, then a simple solution would be to mount it in /mnt instead of in /media. That should solve your problem. Just make a new directory for it in /mnt, and edit /etc/fstab to mount it there instead.

Regards, Herman :)
The partition is mounted in /mnt already.  Here is what the fstab entry looks like (from memory):

```
UUID=******  /mnt/archive   xfs     rw,user,noauto   0    2
```

But with that it shows on my desktop as 'mnt/archive'.  I just deleted the 'noauto' and then it stays off my desktop.  I really like a clean (empty) desktop when possible.  It's really just an annoyance not a serious issue.

This partition is used only for old, archived files that I very rarely need access to.  I don't want it mounted all the time so if the system crashes, the file system can't be corrupted and files can't be lost.  It's a safety thing! ;)

Thank you for your suggestions!

---

