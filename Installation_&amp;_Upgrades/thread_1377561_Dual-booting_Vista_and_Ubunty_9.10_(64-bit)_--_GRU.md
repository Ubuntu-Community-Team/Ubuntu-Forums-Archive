---
title: "Dual-booting Vista and Ubunty 9.10 (64-bit) -- GRUB, can't boot"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by shuu on 2010-01-10
Ok, so here's the deal. I've got Windows Vista (32-bit) on my primary HD, hd0,1. I've installed, using WUBI, Ubuntu 9.10 (64-bit) to hd1,1. 

When I boot up and choose Ubuntu (after installation, so it worked to boot the installation).. something is not in order and I'm sent into GRUB (I'm sure you guys know what it is, so I won't go into details about that.. the essence is that I need to find the kernel and specify it).

Here is what I do, and (partially) what I get in return
>ls 
Returns these: (loop0) (hd0) (hd0,1) (hd1) (hd1,1) of which (hd0,1) is labelled Windows (for convenience) and (hd1,1) Ubuntu.. so the double-check is in order, it is indeed (hd1,1) which I chose to install Ubuntu onto.

>insmod ntfs 
I'm just following a "tutorial", I have no clue what really is going on here (other than it having to do with NTFS file system).. but there's no return statement

>set root=(hd1,1)

>ls $Boot
Return something like: Device (null) : NTFS file system, label Ubuntu and a UUID

>search --no-floppy --fs-uuid -set <insert the UUID in the last return stament here>

>set root=(loop0)

>linux /boot/vmlinuz-blah-blah-generic root=/dev/[COLOR=Red]PROBLEM1[/COLOR] loop=[COLOR=Red]PROBLEM2[/COLOR] ro quiet splash
This thing returns some cryptic message, but there's no where it says anything about error or no such file etc

Problem 1 : I assume that there's something like sdb1 that should be entered here, but that option does not exist, in fact there are no options that begins with sd (it was sda5 in the tutorial).

Problem 2 : I guess because the root is the root.disk file that it is impossible to get out of that and back into (hd1,1) where the ubuntu folder is, and thus I cannot access the desired file.. unless it should be loop=root?

>initrd /boot/initrd.img-blah-blah-generic

>boot
Lots of text running down the screen and a stop a few lines after a statement saying something like "cannot mount root, tried ext3, ext2, ext4 etc etc.."
Then it just freezes there.

I could use some help with this guys, I'd like to try out running Ubuntu on this machine! I have no previous experience with dual booting (other than booting from USB Flash Drive on my Asus EEE) and I ahve no idea what I am doing wrong and/or if there was something I did wrong during installation.

EDIT: Ok, so I solved Problem 2 by using these commands, basically avoiding to set root = loop0..

>ls # Find Ubuntu partition
>set root=(hdX,Y) # Where X (0-n) is the physical drive and Y (1-n) the partition
>insmod ntfs
>loopback loop0 /ubuntu/disks/root.disk # Access this .disk with (loop0)
>linux (loop0)/boot/vmlinuzXXXXXXXX root=**[COLOR=Red]PROBLEM[/COLOR]** loop=/ubuntu/disks/root.disk ro nosplash # Load kernel, use TAB to find the correct file, replace XXXXXXXX
>initrd (loop0)/boot/initrd.imgXXXXXXXX # Use TAB to find the correct file, replace XXXXXXXX
>boot

Problem is still that I don't know what file within (loop0)/dev/ I need to access. There are no files that begin with sd. Thus I have no root.

---

### Post by darkod on 2010-01-10
The procedure you are trying is for full ubuntu install, not for wubi. For wubi try something like:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

Your wubi seems to be on the first partition of disk2, hence /dev/sdb1. See if that works. If it allows you to boot into wubi, in terminal execute:
sudo update-grub2

Don't know exactly what happened but give it a try.

PS. I stand corrected, you were trying commands for wubi but with some modifications. Try the above commands EXACTLY and see if there are error messages and what they say.

---

### Post by shuu on 2010-01-10
Should the 'sdb1' part show up when I enter /dev/ and press TAB? 'cause it doesn't.

Besides, your procedure is basically the same as what I am doing, you're just missing the insmod ntfs and.. uh.. you're not making a loopback loop0 call? I'm confused.

Edit: One problem is that the linux command does not return any errors regardless of what I enter, except for the case where I don't specify a kernel.

---

### Post by darkod on 2010-01-10
I'm not familiar with wubi. There was a wave of problems with wubi few months back where it gives you only sh:grub> prompt and that was the cure.
According to your info, if wubi was installed on (hd1,1), then you should use /dev/sdb1. You can also try /dev/sda1 because hd1 is not always sdb, it can be sda.

Another options is to boot windows and check in the ubuntu folder where you installed wubi, is there the disks folder with the file root.disk inside. That is your image of the virtual root partition for wubi.

---

### Post by shuu on 2010-01-10
Yes, I have found and located the root.disk file, it's in D:\ubuntu\disks\root.disk
I am starting to feel the root.disk is corrupt however, because this file everyone keeps talking about sda#, sdb#, sdc# .. sdA# .. it is not there when I list the files in the root.disk (via GRUB) .. and I am wondering if it is supposed to be there? There is no file at all in root.disk/dev/ that begins with sd.

---

### Post by darkod on 2010-01-10
> **shuu said:**
> Yes, I have found and located the root.disk file, it's in D:\ubuntu\disks\root.disk
I am starting to feel the root.disk is corrupt however, because this file everyone keeps talking about sda#, sdb#, sdc# .. sdA# .. it is not there when I list the files in the root.disk (via GRUB) .. and I am wondering if it is supposed to be there? There is no file at all in root.disk/dev/ that begins with sd.

No, no. sda is not a file. It's how linux labels the drives/devices. The first hard disk would be /dev/sda, the second (if you have it), /dev/sdb, etc. And the number is the number of the partition on the disk.
So, the first partition on the second drive, is /dev/sdb1. If that is your D: in windows terms, then that's what you should use.
Just try the commands both with /dev/sdb1 and /dev/sda1 to make sure you cover the possibility that hd1 might be /dev/sda.

---

### Post by shuu on 2010-01-10
Okay, well there is only C: and D:, they are not partitioned (at least not by me) but when I call >ls in GRUB I get (hd1) partition table, (hd1,1) labelled Ubuntu (which is the D: drive) - plus hd0 and hd0,1 of course for the Windows physical drive, and a loop0 device.

So what I need to do is just write (loop0)/dev/sdb1 .. and if that turns out not to work, it could be it's naming it sda1? 

Just clearing up; I have two physical drives. They are one partition each. In windows, C: and D: labelled Windows and Ubuntu. The device list in GRUB suggest (hd1,1) is labelled Ubuntu.

---

### Post by darkod on 2010-01-10
> **shuu said:**
> Okay, well there is only C: and D:, they are not partitioned (at least not by me) but when I call >ls in GRUB I get (hd1) partition table, (hd1,1) labelled Ubuntu (which is the D: drive) - plus hd0 and hd0,1 of course for the Windows physical drive, and a loop0 device.

So what I need to do is just write (loop0)/dev/sdb1 .. and if that turns out not to work, it could be it's naming it sda1? 

Just clearing up; I have two physical drives. They are one partition each. In windows, C: and D: labelled Windows and Ubuntu. The device list in GRUB suggest (hd1,1) is labelled Ubuntu.

No, not (loop0)/dev/sdb1. Type the commands one by one exactly as I wrote them in my first post. If that doesn't work, we'll see.

---

### Post by shuu on 2010-01-10
I am pleased to inform you that this issue has been solved. Thank you darkrod.

This is how I did it:

>set root=(hd1,1) //* hd1,1 is specific to my installation, use 'ls' and search through each device listed to find the correct partition for your installation*
>insmod ntfs
>loopback loop0 /ubuntu/disks/root.disk
>linux (loop0)/boot/v~ root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro // *sdb1 is directly related to the hd1,1 in point 1, hd0,1 would be sda1 while hd1,2 would be sdb2 etc*
>initrd (loop0)/boot/initrd.img~
>boot

---

### Post by darkod on 2010-01-10
Glad you got it sorted. I'm still wondering if the other commands would have worked because once you set the loop0 device as root, there is no need to type (loop0) in the commands after.
Anyway, you got it working now. :)

---

### Post by shuu on 2010-01-10
> **darkod said:**
> Glad you got it sorted. I'm still wondering if the other commands would have worked because once you set the loop0 device as root, there is no need to type (loop0) in the commands after.
Anyway, you got it working now. :)

The problem with defining root as the loop0 device is accessing /ubuntu/disks/root.disk in the linux-command statement. Though there's probably a work-around that might even be simpler (like loop=root ?) ..

---

### Post by darkod on 2010-01-10
Or:
sh:grub>set root=(loop0)

:)

---

### Post by shuu on 2010-01-10
> **darkod said:**
> Or:
sh:grub>set root=(loop0)

:)

Hm? No, here's the deal:

... previous commands omitted ...
>set root=(loop0)
>linux /boot/v~ root=/dev/sdb1 loop=[COLOR=Red]**?!**[/COLOR] (/ubuntu/disks/root.disk is a non-existent path, when you type loop=/ and TAB for options, it will lists files within root.disk, accessing root.disk itself is not possible within itself)
... next commands omitted ...

I'm thinking it might be possible to just write the statement like this, if you define root as loop0:

>linux /boot/v~ root=/dev/sdb1 loop=(root)

Though I am absolutely not sure, I'm not quite sure if root is just a pointer or what it is, and if you can just set loop to be the same as the pointer.

---

### Post by shuu on 2010-01-11
Umm, this is kind of a side-note, and inside a thread marked solved (by myself) .. but itùs (bah..) it's closely related: I thought the "sudo update-grub2" was in order to make the boot run correctly next time I booted up, but I got into the same situation when I booted up now (second time), and although itùs not a problem to get in seeing as I know what to write, I would prefer to make this permanent, so that it boots from sdb1 and the kernel (by the way, I chose a different kernel today as it seems -blah-blah-14-generic no longer was the only one, there was also a -blah-blah-17-generic, I chose the latter guessing a higher number would be a newer version and thereby better) I specified in GRUB.

Question is, how do I make the change permanent? If itùs necessary to do a manual edit of the file, please be clear so I donùt make my case worse. Iùm following your instructions to the point, no typos, thanks.

---

### Post by meierfra. on 2010-01-11
This is the permanent solution:
Boot into Windows and follows these instruction from the author of Wubi:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

### Post by shuu on 2010-01-11
Oh, so it's a problem with only Wubi? If I were to do a full install of Ubuntu later, I would not experience these troubles?

---

### Post by meierfra. on 2010-01-11
This particular bug only hits Wubi. But it it has a very easy fix: You just  need  to replace one file.  

> If I were to do a full install of Ubuntu later, I would not experience these troubles? 

Well, there is always a chance that you run into  different problems. But as  long time solution, a full install  is definitely the better solution.

---

