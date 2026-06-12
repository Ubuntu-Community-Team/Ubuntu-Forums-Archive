---
title: "Moving Intalled Ubuntu from one disk to another."
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by gandalf2000 on 2008-06-04
I have a dual boot system Ubuntu/XP on an 80G HD and I have just about got the Ubuntu system the way I want it.  I recently pulled a 250G HD from a DVD recorder that had seen little use and installed it into the tower and formatted it to NTFS.  Now I would like to transfer Ubuntu to this new HD.  I would hate to have to reinstall as it took me days to get it to where it is (newbie alert).  Is there a way to this?

---

### Post by logos34 on 2008-06-04
use gparted to carve out a space on the 250 gig drive at least as large as your linux root partition.  Then simply [copy it ]("http://gparted.sourceforge.net/larry/move/move.htm")(for this part root cannot be mounted so you'll have to use gparted either on the ubuntu livecd or the gparted livecd). It would probably be easiest to [reinstall grub to the MBR]("http://ubuntuforums.org/showthread.php?t=224351") of the 80 gb hard disk, but pointing to the new drive/partition.  Make sure to edit the 'root' and 'groot' lines in /boot/grub/menu.lst if the partition # changes. 

E.g., if root was sda2 on the 80 gb drive and you copy it to the first partition on the new drive, sdb1, then you'll need to change menu.lst to (hd1,0) 

If you continue to boot grub from the 80 gb drive you won't have to edit windows boot stanza or change the bios boot order.  
 
As long as your using UUIDs in menu.lst and fstab there shouldn't be a trainwreck anywhere. But I'm probably forgetting something!

---

### Post by gandalf2000 on 2008-06-04
"As long as your using UUIDs in menu.lst and fstab there shouldn't be a trainwreck anywhere."

Shouldn't be a trainwreck is not really confidence making, but I'll try it tonight.

"But I'm probably forgetting something!"

Better and better, thanks.  Guess I should ask at this point what UUIDs are and do you fstab with a knife or icepick?  Do you use fstab in frustration?  I could understand that.  
Sorry about all the questions but I,ve been struggling with Linux for about a week and have quite a long way to go.  I only found out a couple days ago how to change to root in the console.

---

### Post by IgnorantGuru on 2008-06-04
One method for doing so...

[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems#Scenario_.238:_Moving_A_System_To_Another_Partition](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems#Scenario_.238:_Moving_A_System_To_Another_Partition)

---

### Post by logos34 on 2008-06-05
> **gandalf2000 said:**
> "As long as your using UUIDs in menu.lst and fstab there shouldn't be a trainwreck anywhere."

I was thinking in particular of this line (in bold):

title           Ubuntu 8.04, kernel 2.6.24-18-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-18-generic **root=UUID=d77656b5-aa1c-4375-8bfa-b517cebff023** ro splash 
initrd          /boot/initrd.img-2.6.24-18-generic
quiet
 
if instead of the UUID it had 'root=/dev/sda2' format, you'd have to change it along with the root line before booting the new partition or else it would fail

Sorry I missed the 'newbie alert'

EDIT: 

Here's some links, but they all seem to use the 'cp -a' from the command line.  Gparted seems to me easier. (You could also use [Partimage]("http://www.psychocats.net/ubuntu/partimage").)

[http://riceball.com/drupal/node/456](http://riceball.com/drupal/node/456)
[http://beans.seartipy.com/2006/09/24/moving-a-gnulinux-installation-to-a-different-partition/](http://beans.seartipy.com/2006/09/24/moving-a-gnulinux-installation-to-a-different-partition/)
[http://gentoo-wiki.com/HOWTO_Move_Gentoo_Installation_to_new_hard_disk](http://gentoo-wiki.com/HOWTO_Move_Gentoo_Installation_to_new_hard_disk)

---

