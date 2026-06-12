---
title: "Dual boot, install 2000/ XP after Ubuntu"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by b0bby on 2007-08-04
Hello..

My laptop is running Ubuntu 7.04, but I kinda need to install Windows (For Photoshop etc) on it too, 2000 or XP, and of course, I don't want to loose weeks of work with my Ubuntu-system, so is it possible to install Windows after I've installed Ubuntu.

If I'm not mistaken the Windows setup overwrites the MBR w/o asking before.. 

So my thoughts are; 
* boot up with Gparted Live-CD, make a new partition for Windows
* Install Windows on that new partition.
* Boot up with Ubuntu setup, choose Expert Install
* install GRUB again, and hope it finds both Operating Systems.


Please help me out =)

---

### Post by forestpixie on 2007-08-04
That sounds logical - however I've never done it myself.

Don't know if you've read these - they might help

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://ubuntuforums.org/search.php?searchid=24839894](http://ubuntuforums.org/search.php?searchid=24839894)

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by pyrodrake on 2007-08-04
I actually had to reinstall Windows last week (always a pain), but I use the Feisty Alternate install CD (for a RAID)...  Maybe I can offer a bit of assistance:

> * boot up with Gparted Live-CD, make a new partition for Windows
* Install Windows on that new partition.

Definitely.  Want to create the Windows partitions first, install Windows, and let it boot for its first time.

> * Boot up with Ubuntu setup, choose Expert Install
* install GRUB again, and hope it finds both Operating Systems.

Kind of what I did, but slightly different, mostly because I use the ALT CD and with RAID.  After the Windows install, I booted the Feisty Alt CD, and selected "Recover a broken system" from the boot menu.  From there, I just went through the settings until it got to the partitioner.  From there, I selected "Go back" and chose the option to "Execute a shell"

From there, I pretty much did the following:
```
mkdir /target
mount /dev/hda /target    #Make sure you substitute hda for your hard drive
mount --bin /dev /target/dev
mount -t proc proc /target/proc
mount -t sysfs sys /target/sys
chroot /target
bash     #I know, not necessary, but I like it to look nice...  :)
```

Next, I set up and updated GRUB:
```
grub --no-curses     #not sure if the --no-curses is really necessary, but its the way I do things
*grub> *device (hd0) /dev/hda     #Again, replace hda with appropriate hard drive
*grub> *root (hd0,0)     #assuming your Ubuntu partition is the first partition on the drive
*grub> *setup (hd0)
*grub> *quit
update-grub
exit     #to exit the chroot
```

Finally, I did *nano /target/boot/grub/menu.lst*, verified that the *# groot=* pointed to my Ubuntu partition (  *(hd0,0)*  in this example), and added the following lines at the end:
```
title WindowsXP
root (hd0,1)     #make sure you replace with the appropriate number for your windows partition
                         #keep in mind that GRUB counts from 0
chainloader +1
```
**CTRL-X** to exit, "**y**" save changes.  Type *exit* at the shell, then select "**Abort Installation**" at the menu.  Take CD out, let system reboot...

That should pretty much do it.  I know there is probably an easier way, but over the past 3 weeks, I've had to go through a process similar to this at least 6 or 7 times due to issues I've been having with Windows, and this process worked every time to get GRUB back.  Hope this helps, or can at least point you in the right direction!  :)

---

### Post by n.aggel on 2007-08-04
man let us know how it turns out, becasuse i have a simular problem:)

---

### Post by b0bby on 2007-08-04
pyrodrake; Thanx alot for that input, I'll think I'll install ubuntu in vmware, then try to install win after that. 

n.aggel; I sure will..

---

