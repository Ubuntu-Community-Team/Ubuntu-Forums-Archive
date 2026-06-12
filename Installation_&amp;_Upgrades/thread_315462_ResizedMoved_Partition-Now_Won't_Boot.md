---
title: "Resized/Moved Partition-Now Won't Boot"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by gng4life on 2006-12-09
Hello All,

I have a Intel based system I built and have Ubuntu and WinXP on it.  The WinXP is on my HDA and my Ubuntu 6.10 is on my HDB.  I had moved the IDE cable on my second HDD and then I booted with a Live CD to get to GParted to resize my main partition.  I did that and to complete it, I had to push my swap partition in front of the available space.  This all went well.  Then I tried to boot, it just hangs on the splash screen.  

I booted back up on the Live CD and noticed that it is showing my second HDD is at HDC now, not HDB.  Of course I went to the menu.lst and it was blank, I think because it was the GRUB for the CD.  I tried to boot again and then when GRUB came up, I edited there by pressing "e" and changed the root to "hdc" instead of "hdb".  I thought that would fix it but still, it hangs on boot.  

Did I miss something here?  If GRUB is pointing to HDC1 and that's the partition with my Ubuntu install, shouldn't it boot?  I have searched Google and the forums for answers but nothing works.  Any help is greatly appreciated, thanks in advance!

---

### Post by wgscott on 2006-12-09
If you are using edgy, /etc/fstab now uses UUID instead of device names, and every time you repartition, UUID changes.

Probably the easiest fix is to move /etc/fstab out of the way and replace it with /etc/fstab.pre-edgy or whatever the backup the edgy upgrade made is called.  If you can't reboot, you might have to boot from the demo disk, mount the root partition to a temporary mount point

eg

sudo mount -t ext3 /dev/hdc1  /mnt/temp

and then move the files around.

Whomever thought to put the UUID in /etc/fstab deserves a Nobel Prize.  Not.

---

### Post by gng4life on 2006-12-09
Thanks!  I'll try that now...

---

