---
title: "Copy boot drive to SSD"
date: 2019-01-19
forum: Installation &amp; Upgrades
---

### Post by patrick1610 on 2019-01-19
Hi, 

I am pretty new to Ubuntu and have just finished my first setup. I did this on an old HDD since I was still using my SSD in another computer until this setup was ready-to-go. 
Now that I have finished it, I wanted to dd this onto the SSD (256GB). But on the (640GB) HDD there is an LVM partition which has used all the hard-drive space. EDIT: There is only around 70GB really in use.. 
I Installed Gparted on Ubuntu to shrink the partition size, but it won't allow me to make it smaller. 

How can I copy my entire setup onto the SSD? Any things I am missing here?
EDIT: I read that booring Gparted from an USB should allow me to shrink the boot drive, but am I sure it only shrinks unused space when doing that?

Thanks in advance! 

Regards, Patrick

---

### Post by TheFu on 2019-01-20
LVM is flexible, but adds complexities. Gparted can't deal with LVM. Also, it is non-trivial  to move PVs, VGs and LVs to a smaller disk.  OTOH, if you were moving to a larger disk, then you could have used **ddrescue** to move everything over, then resized up.  I use ddrescue over straight, dumb, dd, always.

As it stands, I think the only real option you have is to use normal backup/restore tools that work at the file system layer.  There are many, many, many, threads here about doing that. [https://ubuntuforums.org/showthread.php?t=2406180](https://ubuntuforums.org/showthread.php?t=2406180) is one of those.

On second thought ... let me see if LVM doesn't have some easy method to migrate data .... yep.  LVM to the rescue!

Updated:

[https://askubuntu.com/questions/161279/how-do-i-move-my-lvm-250-gb-root-partition-to-a-new-120gb-hard-disk](https://askubuntu.com/questions/161279/how-do-i-move-my-lvm-250-gb-root-partition-to-a-new-120gb-hard-disk) has a nice answer.  In short (not enough below to follow without manpages):> 
```
pvcreate /dev/sdNEW
vgextend vgX /dev/sdNEW
pvmove /dev/sdOLD
vgreduce vgX /dev/sdOLD

```
Use **update-grub** and **grub-install** to make your new root disk bootable

If you need more help with LVM and help moving: [https://www.tecmint.com/lvm-storage-migration/](https://www.tecmint.com/lvm-storage-migration/)
A solid understanding of LVM will be extremely helpful.  I'm temped to try this on some of my storage because it is so very cool.

---

### Post by patrick1610 on 2019-01-21
Thanks for your reply! Since I am new to Ubuntu, it scares me a little to do the method you write about without any LVM knowledge. 
I guess it is not as simple as typing those 4 commands and voila?


I also found this tutorial: [http://www.taitclarridge.com/techlog/2009/10/lvm-migration-to-smaller-disk.html](http://www.taitclarridge.com/techlog/2009/10/lvm-migration-to-smaller-disk.html)
Should that be a safe road for me to follow step-by-step?

---

### Post by oldfred on 2019-01-21
I recommend the new install, and restore apps list from exported list of apps (I make that part of my normal backup), and restore /home or any data partitions from your backup. It becomes a good test of your backup procedures as you still have old drive to go back to. 

If a new user, LVM may be a bit more complex, but if you need full drive encryption then you have to use LVM.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

If you want LVM, TheFu can help you as he has used it for many years. 
Since SSD, is system newer UEFI or older BIOS hardware. Then are you installing in UEFI or BIOS boot mode? Will you want dual boot with other system(s)?
LVM is better when it has control over entire drive.

If you want the full drive encryption, see also this thread:

 Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627)

---

### Post by TheFu on 2019-01-21
> **patrick1610 said:**
> Thanks for your reply! Since I am new to Ubuntu, it scares me a little to do the method you write about without any LVM knowledge. 
I guess it is not as simple as typing those 4 commands and voila?

I also found this tutorial: [http://www.taitclarridge.com/techlog/2009/10/lvm-migration-to-smaller-disk.html](http://www.taitclarridge.com/techlog/2009/10/lvm-migration-to-smaller-disk.html)
Should that be a safe road for me to follow step-by-step?

I can't recommend a tutorial from some site/person that I've never heard about before and never followed myself.

I think variants of those 4 LVM commands already posted are all that is required, but no, you cannot copy/paste them.  For someone with Linux and LVM intermediate skills, those 4 commands should be sufficient to accomplish the end-goal, but other commands will be necessary to lookup other data to fill in the correct options, devices and disks. And handling of mount and umount will be necessary too.  Standard things for an intermediate admin.

I'm with Oldfred - use your normal backup and restore methods.  Before yesterday, that would be how I did it.

---

