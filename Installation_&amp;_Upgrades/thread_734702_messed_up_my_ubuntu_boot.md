---
title: "messed up my ubuntu boot"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by walter_j on 2008-03-25
i installed ubuntu 7.10, and it ran great. i added a 2nd hd and tried to install mandriva on it, but now i can't boot ubuntu. mandriva never installed corrrectly too, but thats another problem. is it possible to easily fix this, or should i back up and reinstall ubuntu?

i booted using ubuntu live cd, and my home folder with all data is still there. i just can't boot to it


walter

---

### Post by walter_j on 2008-03-25
mandriva modified menu.lst and backed up the old menu.lst. i renamed the backup to menu.lst, but now i get a message asking if i want to run e2fsck, but it may cause severe damage. what do i do?

---

### Post by confused57 on 2008-03-25
You can reinstall Ubuntu's grub, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You might be able to add an entry to Ubuntu's menu.lst to boot Mandriva:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by AdamWill on 2008-03-25
mandriva from 2008 Spring onwards will detect and configure other distros rather than just, er, ignoring them, as it has up till 2008. :)

---

### Post by walter_j on 2008-03-25
ubuntu tries to boot now, but i get the errors
/etc/rc.d/rc.sysinit: line 839 command not found
and
fsck.ext3: no such file while trying to open /dev/hdb5 /dev/hdb5

e2fsck is started and asks if i really want to run it, since severe file system damage may occur. i won't allow it to run, and now have a command prompt
1#

i'm sure hdb is the second hd. maybe the same error messed up mandriva too.

perhaps a swap file partition is messed up? it seems the system is looking for a file that doesn't exis?

---

### Post by confused57 on 2008-03-25
> **walter_j said:**
> ubuntu tries to boot now, but i get the errors
/etc/rc.d/rc.sysinit: line 839 command not found
and
fsck.ext3: no such file while trying to open /dev/hdb5 /dev/hdb5

e2fsck is started and asks if i really want to run it, since severe file system damage may occur. i won't allow it to run, and now have a command prompt
1#

i'm sure hdb is the second hd. maybe the same error messed up mandriva too.

perhaps a swap file partition is messed up? it seems the system is looking for a file that doesn't exis?
You may want to boot the Ubuntu live cd and post the output of:
```
sudo fdisk -l
```
-l is a small "L"

Also, mount your Ubuntu root partition:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/xxx /media/ubuntu
```
substitute your Ubuntu root partition in place of /dev/xxx(see results of "fdisk -l"...then post your menu.lst:
```
gedit /media/ubuntu/boot/grub/menu.lst
```
and your /etc/fstab:
```
gedit /media/ubuntu/etc/fstab
```

---

### Post by walter_j on 2008-03-25
fdisk -l

disk /dev/sda
disk device      boot         start        end              blocks       id          system
/dev/sda1  *              1            19080      153260088+  83        linux
/dev/sda2                 19081      19457         3028252+     5       extended
/dev/sda5                 19081      10457         3028221     82        linux swap

disk /dev/sdb
/dev/sdb1  *               1                509            4088511   82     linux swap
/dev/sdb2                510              2495          15952545    5    extended
/dev/sdb5                510              2495          15952513+        linux

ftab to follow

---

### Post by walter_j on 2008-03-25
fstab
/dev/hda1 / ext3 defaults 1 1
/dev/hdb5 /home ext3 defaults 1 2         ## shouldn't /dev/hdb5 be /dev/hda5?  wj
none /proc proc defaults 0 0
/dev/hda5 swap swap defaults 0 0
/dev/hdb1 swap swap defaults 0 0


menu.lst
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ae41e913-b2e5-45a5-a7a8-c82f11e69546 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ae41e913-b2e5-45a5-a7a8-c82f11e69546 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by confused57 on 2008-03-25
You could try commenting out your hdb5 and hdb1 in your fstab, mount your Ubuntu partition, then run:
```
cd /media/ubuntu/etc
sudo cp fstab fstab_backup
gksudo gedit fstab
```

then comment out hdb5 & hdb1:
```
/dev/hda1 / ext3 defaults 1 1
#/dev/hdb5 /home ext3 defaults 1 2 
none /proc proc defaults 0 0
/dev/hda5 swap swap defaults 0 0
#/dev/hdb1 swap swap defaults 0 0
```
You don't need 2 swap partitions for Ubuntu...quit & save.

Did you add these lines to your /etc/fstab or did you have your 2nd hard drive connected when you installed Ubuntu and created a separate /home on your hdb drive?

Also, Gutsy 7.10 uses UUID's in fstab...since you're not using UUID's, you'll need to change your menu.lst kernel line to show /dev/hda1...highlight your Ubuntu entry in your grub boot menu when you boot your pc, press "e", highlight the kernel line, press "e" again, change root to root=/dev/hda1(instead of the UUID), press "enter", then "b" to boot.

Added:  Gutsy on most systems recognizes IDE drives as sda, sdb, etc(see your fdisk -l from the live cd)...if using hda1, etc doesn't work, you might try changing all references of /dev/hda to /dev/sda in your fstab and the root in the menu.lst kernel line.

---

### Post by walter_j on 2008-03-25
it appears that mandriva messed up something. I now get the ubuntu splash screen, then i get the mandriva text login, where it dies.

i tried to install mandriva on the 2nd hd, but it didn't work. i know just enough to get myself in bad trouble. at least i didn't format the first drive, which ubuntu is on.

i disconnected the 2nd drive, but it makes no difference. it still shows the ubuntu progress bar, then goes to mandriva login. 

am i totally screwed

---

### Post by confused57 on 2008-03-25
> **walter_j said:**
> it appears that mandriva messed up something. I now get the ubuntu splash screen, then i get the mandriva text login, where it dies.

i tried to install mandriva on the 2nd hd, but it didn't work. i know just enough to get myself in bad trouble. at least i didn't format the first drive, which ubuntu is on.

i disconnected the 2nd drive, but it makes no difference. it still shows the ubuntu progress bar, then goes to mandriva login. 

am i totally screwed
Unfortunately, it appears that Mandriva installed to your 1st hard drive and probably created a separate /home on your 2nd hard drive.  Since you didn't format your 1st hard drive, you can mount your root partition on the 1st hard drive, then drag & drop files you want to save to a removable media(external drive?)...if it's a large amount of data you need to save, you could create an ext3 partition on your 2nd hard drive large enough to hold your data, if you don't have an external drive.  You may be able to save some of your settings also:
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)

Once you mount your Ubuntu partition(& other media/partition), you can open Nautilus, navigate to the /media/ubuntu folder(using the live cd), then drag & drop.

You may want to wait on someone else who may be able to help you recover Ubuntu without reinstalling.

---

### Post by walter_j on 2008-03-26
i backed up data to the 2nd hd, and am considering opensuse - although hardy is coming soon too. i like kubuntu, but i get into even worse trouble with it. i was so sure i wasn't installing mandriva to the 2nd disk, so i don't know what i did wrong. i had jus enough space on the 2nd disk for my data, so i can reinstall if i can't recover. i'll disconnect it before reinstalling though.

maybe there's good instructions for installing another distro on a 2nd hd somewhere. i want to check out foresight, pclinux, kde 4. thats the trouble with linux. i can't keep my mits off it, and leave a solid system alone.

thanks for your help. i'm learning though. every disaster, i learn something.

Walter

---

### Post by confused57 on 2008-03-26
> **walter_j said:**
> i backed up data to the 2nd hd, and am considering opensuse - although hardy is coming soon too. i like kubuntu, but i get into even worse trouble with it. i was so sure i wasn't installing mandriva to the 2nd disk, so i don't know what i did wrong. i had jus enough space on the 2nd disk for my data, so i can reinstall if i can't recover. i'll disconnect it before reinstalling though.

maybe there's good instructions for installing another distro on a 2nd hd somewhere. i want to check out foresight, pclinux, kde 4. thats the trouble with linux. i can't keep my mits off it, and leave a solid system alone.

thanks for your help. i'm learning though. every disaster, i learn something.

Walter
I'm a recovering distro-holic myself and am down to only 7 distros at the moment...5 of which are different versions of Ubuntu(Dapper, Gutsy, Hardy, Fluxbuntu, & Ubuntulite), the 2 non-Ubuntu installs are SimplyMepis & PCLinuxOS.  I've tried quite a few different distros, such as Gentoo, Linux From Scratch, Sabayon, Slackware, Zenwalk, Puppy, etc, but I keep coming back to Ubuntu.
   I built a new pc about 2 years with a single IDE drive, installed Dapper with just a large primary root partition & an extended(logical) swap at the end of the drive.  When I wanted to try a new distro, I used the [Gparted Live CD](http://gparted-livecd.tuxfamily.org/) to resize the Dapper partition to free up 10-15 Gb...ended up with 8-10 different distros on the 1 hard drive.  You can have as many logical partitions as you want or need on a single hard drive, but only 4 primary partitions, one of which is an extended partition containing the logical partitions(at the end of the hard drive).

  I've since added 2 SATA drives, installing various distros on them; however, they're used mostly now for data storage.  Dapper recognizes the drives as hda, sda, sdb...Gutsy as sda(hda in Dapper), sdb, and sdc.  I've run into problems with a couple of distros(Mepis & Sabayon) recognizing the drives as sda, sdb, sdc(hda in Dapper)...the bios boot order of the drives are hda, sda, & sdb, therefore Mepis & Sabayon mis-identified which drive is hd0, hd1, & hd2.  Relatively easy to correct, but does require some experience with modifying grub settings.  

When I'm installing a new distro I try to look at the partitions on the different hard drives to determine the correct drive & partition where I want to install, rather than just going by sda, sdb, sdc, etc.  It's been easier for me to create the new partition(s) beforehand with the Gparted live cd...then install the new distro.

   Didn't mean to make this so long, but maybe it'll give some ideas for partitioning & trying out new distros...it has been and still is interesting & fun to try them out.  You might want to check out Herman's grub entries for booting different distros:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)
even if you overwrite your main distros grub IPL on the mbr, it's easy to recover with the Ubuntu live cd.

Partitioning guides:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

---

