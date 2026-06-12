---
title: "[SOLVED] UNetbootin destroyed my Hardy boot"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by meganox on 2008-10-31
I was attempting to make a usb stick installer for Intrepid since I cannot burn cds under Hardy.

usb-creator was unable to create a bootable stick after manually partitioning and using install-mbr.

unetbootin was even worse, it has hosed the grub on my laptop HD.

supergrubdisk was unable to fix it.

Currently running puppy linux.  I have a Hardy livecd, how do I rescue grub from it?

Thanks in advance.

---

### Post by Partyboi2 on 2008-10-31
If you are trying to restore grub try [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by meganox on 2008-10-31
Thanks, but it's worse than that, I cannot mount the drive from puppy linux or Hardy live-cd.

How do I find out what damage unetbootin has done to my disk?

---

### Post by meganox on 2008-10-31
Update:

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5259fcb1

   Device Boot      Start         End      Blocks   Id  System


```

It's completely destroyed my partition table.  I'd backed up all my data but I've lost my configuration & customisations, applications in /opt, custom launcher scripts, and my Intrepid iso.

Guess I'm installing Hardy from CD and dist-upgrading.

I seriously recommend anyone NOT use UNetbootin to make a USB installer for Intrepid.

---

### Post by meganox on 2008-10-31
double post

---

### Post by meganox on 2008-10-31
dist-upgrade to Intrepid on a clean install of Hardy with all updates applied FAILED.


REALLY getting sick of this.

Back to Hardy and looking for a distro that knows how to install itself.

---

### Post by snowpine on 2008-10-31
I had no problems creating an Intrepid install USB using Unetbootin. Very important, though: At the bottom left, it asks you which drive to use. You have to make sure you choose your USB stick and not your hard drive!!!

Thanks for starting this thread; it is a good warning and hopefully will save someone from a similar mishap.

---

### Post by meganox on 2008-10-31
It only offered me one choice of drive - the USB stick.  "Show all drives" was unchecked.

Just tried it again on a clean Hardy install, it failed to make my stick bootable but didn't hose my partition table this time.

---

