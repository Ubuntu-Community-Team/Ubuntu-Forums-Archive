---
title: "[SOLVED] How do I migrate to a new partition?"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by bouncingmolar on 2008-08-10
I'm trying to migrate my entire installation to a bigger partition on my drive. I've searched for and read many threads, but I'm still stuck!

After reading many instructions I concluded I only need to: 
[I]1. copy information from old partition to new. 
2. Edit Fstab
3. Edit Grub. [/I]



MY problem is that I can copy the drive but after that i'm stuck. My edited grub attempts loading the new partition but it just gets stuck at the loading screen. I can still load my old partition ok.

Also which Fstab and grub do I edit (the one in my new partition I assumed?) 


*What I tried: *
I used Knoppix + Gparted to copy old partition to new
I've tried editing Fstab (I just switched sda3's for sda1's) which didn't seem to do squat. 
I've tried editing grub I added [see below] *(my old partition has (hd0,2) and a different UUID): *

```
title		New Ubuntu partition
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=44840425-c323-4301-9c1f-63d9225dca70 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
``` 




I've only just read and was hoping to use [GUI Fstab Editing with PySDM]("http://ubuntuforums.org/showthread.php?t=872197&highlight=switch+partitions")

I've tried using these steps to reset grub ([HOWTO: Restore GRUB (if your MBR is messed up)]("http://ubuntuforums.org/showthread.php?t=24113&highlight=switch+hdd"))

I've looked at [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

I also read [Migrating Ubuntu to a new hard drive]("http://ubuntuforums.org/showthread.php?t=235133") but I couldn't understand the last post about editing grub ( I couldn't find anywhere where to change the kernel line for boot options)

---

### Post by bouncingmolar on 2008-08-10
I just found this thread [help backing up system to load on new hard drive]("http://ubuntuforums.org/showthread.php?p=5564014#post5564014") But I can't see how it applies to me as they are cloning a drive rather than a partition?

---

### Post by Pumalite on 2008-08-10
Maybe all you need is a separate /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by bouncingmolar on 2008-08-10
> **Pumalite said:**
> Maybe all you need is a separate /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Hi Pumalite, thanks for the link. I read it before and am planning to do that too. 

*Current partition setup*
sda1 = clone of my linux installation
sda2 = an old unused linux installation
sda3 = current linux installation (partition too small)
sda5 = Vista ... blurrrgh!

I wanted to tidy up a bit so I thought i'd
1. migrate my linux install to sda1
2. move old installation from sda2 to sda3. (so i can delete it eventually)
3. follow the link you mentioned to separate /home from new sda1 into sda2 

I've already cloned sda3 to sda1. Now I just need to be able to boot it from sda1. I am trying to edit fstab but i'm having trouble with UUID's it appears that the UUID for sda3 is identical to sda1... how does the fstab tell them apart?..

... or are my partitions just mounted wrong with the same partion mounted twice.

---

### Post by bouncingmolar on 2008-08-11
I Changed the UUID of the copied partition using advise from logos34 (from [help backing up system to load on new hard drive]("http://ubuntuforums.org/newreply.php?do=newreply&p=5564389")) > **logos34 said:**
> if you do you'd need to change the UUID on one of them: sudo tune2fs -U random /dev/sd??

I now have it working

**Mini Howto** for anyone else who wants to migrate partitions using this method. 

1. Make partition using whatever tools you decide. 
2. boot with live CD (so that partitions aren't mounted) I used Knoppix (which I had to fiddle with before I had the right refresh rate for my monitor. 
2a. Use Gparted to copy old partition to new partition. 
3. reboot into old partition and sudo tune2fs -U random /dev/sd??   (where ?? = the new partition sda1 in my case)
4. sudo blkid gives the new UUID for sda1. 
5. copy this UUID into the new partitions fstab and grub.
6. reinstall grub into the MBR of the new partition: (follow the instructions from the link below or the grub link in my first post. 

I found this thread useful (its similar to the ubuntu thread i mentioned in my first post [Fedora forum: How to install GRUB on the MBR]("http://fedoraforum.org/forum/showthread.php?t=975")

---

