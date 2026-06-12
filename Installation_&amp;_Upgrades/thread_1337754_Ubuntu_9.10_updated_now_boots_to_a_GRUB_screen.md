---
title: "Ubuntu 9.10 updated now boots to a GRUB screen"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by Zaphod69 on 2009-11-25
Hi,

Total NOOB here. I've installed Ubuntu 9.10 from inside Windows XP on my Toshiba M70A. Over the past 5 days it's been awesome - love it and if I didn't have some Win apps I need I'd kill off XP.

This morning an update manager popped up - 26 updates to install. Let it do that and rebooted.

Now when I choose Ubuntu from the boot menu it brings up something called GRUB.

My HDD does not have a separate partition for Ubuntu - it's all installed on my NTFS partition.

How do I get it to boot up Ubuntu?

And how do I get it to keep whatever it needs to keep booting Ubuntu? (IE without having to type in whatever commands it needs at the GRUB prompt)?

TIA :D

Zaphod

---

### Post by inevitable7 on 2009-11-25
i have this very same problem

---

### Post by DrMarcusAurelius on 2009-11-25
I have the same problem.  I have a Wubi install of 9.1 that was working fine until I updated and restarted this afternoon.  I still have the option to choose XP or Ubuntu, but when I choose the latter is goes to a Grub screen.  What do I type to get it to load the virtual disk and boot my Wubi install again?  Thanks

---

### Post by Opie32958 on 2009-11-25
Yep, I have the same problem, posted it in a different thread. Nobody seems to have an answer yet.

---

### Post by inevitable7 on 2009-11-25
i tried some of the stuff listed in here, i'm a complete noob and i don't know what i'm doing

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

and by grub menu, i mean this
[IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.cli.boot.png[/IMG]
where it just says sh:grub>

---

### Post by Zaphod69 on 2009-11-25
> **inevitable7 said:**
> i tried some of the stuff listed in here, i'm a complete noob and i don't know what i'm doing

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

and by grub menu, i mean this
[IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.cli.boot.png[/IMG]
where it just says sh:grub>

Thats the Grub screen I get.

Is the easy solution to boot off the Ubuntu Live CD and repair it as described at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) ?

TIA

---

### Post by kultrva on 2009-11-26
Same problem here. It started tonight right after I installed updates.

---

### Post by PaulinVictoria on 2009-11-26
Same for me too.  Updated, asked me to restart and that was the last I saw of Ubuntu.  Good job I still have my reliable Vista installation on this disk.  And who'd have thought that anyone would ever say that???

---

### Post by Zaphod69 on 2009-11-26
After doing some searching I found this thread - [http://ubuntuforums.org/showthread.php?t=1310820&page=2](http://ubuntuforums.org/showthread.php?t=1310820&page=2) and followed LuisPT's advice -

At the Grub shell
(first I did ls which showed - (loop0), (hd0), (hd0,1)

set root=(hd0,1)
linux (loop0)/boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd (loop0)/boot/initrd.img-2.6.31-14-generic
boot

Initially I tried it with vmlinuz-2.6.31-15-generic but the system immediately rebooted. With vmlinuz-2.6.31-1.14-generic I managed to get a little further.

Had a heap of information scroll past very quickly then this:

Begin: waiting for root system
[    2.236078] clocksource tsc unstable (delta=-83303508ns)
Done
Gave up waiting for root device Common problems:
-boot args (cat /proc/cmdline)
     -check rootdelay = (did the system wait long enough?)
     -check root = (did the system wait for the right device?)
-missing modules (cat /proc/modules; ls /dev)
Alert! /dev/hd0 does not exist. Dropping to shell!

BusyBox V1.13.3 (ubuntu 1:1.13.3-1ubuntu) built in shell (ash)
(initramfs)_

To me it looks like Grub accepted the commands entered and that (hd0) was the correct drive but it's not right somewhere else in the boot sequence.

Any thoughts? (please)

Even tho I'm not a fan of Windows I have not had many booting problems after installing updates on it.

---

### Post by darkod on 2009-11-26
> **Zaphod69 said:**
> 

Even tho I'm not a fan of Windows I have not had many booting problems after installing updates on it.

I completely understand the frustration but just to point out that you don't have a "real" ubuntu installation. Unfortunately it seems that the ubuntu team trying to make it easier to try ubuntu inside windows, got in way over their heads. First of all windows is still running the show, and it's difficult to combine that.
Like the OP said, you don't really have ubuntu partition at all. And any help or tutorials that you find have to be examined carefully because most of them would apply only for a full ubuntu installation.
I would always recommend to try ubuntu with the Try Ubuntu option from the CD. It offers the option to run from the CD without any changes to the hdd. Of course, wubi offers some advantages like installing software, etc.
My advice to all that have tried ubuntu trough wubi would be: If you really liked it, remove wubi with Add/Remove programs like you would any windows app, and install ubuntu as proper dual boot ASAP. It will work even faster, and better because it's not inside windows.

These updates might be creating some problem that the designers of wubi didn't think of, and there are a lot of possibilities for problems when you are trying to make linux to work inside windows.

---

### Post by Opie32958 on 2009-11-26
Aw heck, I think I'll just go for darkod's solution. Shouldn't have to, but he probably does a valid point. Got a four day weekend anyway.

---

### Post by Zaphod69 on 2009-11-26
I think I'll go that way as well. Darkod makes a valid point but I really didn't want to lose what I'd set up on my ubuntu.

---

### Post by presence1960 on 2009-11-26
> **darkod said:**
> I completely understand the frustration but just to point out that you don't have a "real" ubuntu installation. Unfortunately it seems that the ubuntu team trying to make it easier to try ubuntu inside windows, got in way over their heads. First of all windows is still running the show, and it's difficult to combine that.
Like the OP said, you don't really have ubuntu partition at all. And any help or tutorials that you find have to be examined carefully because most of them would apply only for a full ubuntu installation.
I would always recommend to try ubuntu with the Try Ubuntu option from the CD. It offers the option to run from the CD without any changes to the hdd. Of course, wubi offers some advantages like installing software, etc.
My advice to all that have tried ubuntu trough wubi would be: If you really liked it, remove wubi with Add/Remove programs like you would any windows app, and install ubuntu as proper dual boot ASAP. It will work even faster, and better because it's not inside windows.

These updates might be creating some problem that the designers of wubi didn't think of, and there are a lot of possibilities for problems when you are trying to make linux to work inside windows.

+1

darkod is indeed correct. Wubi is not meant to be a permanent installation, but rather a "test drive" for those unwilling to commit to partitioning their hard disk until they decide if they really like Ubuntu. See here for more info:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://en.wikipedia.org/wiki/Wubi_(installer)](http://en.wikipedia.org/wiki/Wubi_(installer))

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

---

### Post by sinurge on 2009-11-26
> **Zaphod69 said:**
> After doing some searching I found this thread - [http://ubuntuforums.org/showthread.php?t=1310820&page=2](http://ubuntuforums.org/showthread.php?t=1310820&page=2) and followed LuisPT's advice -

At the Grub shell
(first I did ls which showed - (loop0), (hd0), (hd0,1)

set root=(hd0,1)
linux (loop0)/boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd (loop0)/boot/initrd.img-2.6.31-14-generic
boot

Initially I tried it with vmlinuz-2.6.31-15-generic but the system immediately rebooted. With vmlinuz-2.6.31-1.14-generic I managed to get a little further.

Had a heap of information scroll past very quickly then this:

Begin: waiting for root system
[    2.236078] clocksource tsc unstable (delta=-83303508ns)
Done
Gave up waiting for root device Common problems:
-boot args (cat /proc/cmdline)
     -check rootdelay = (did the system wait long enough?)
     -check root = (did the system wait for the right device?)
-missing modules (cat /proc/modules; ls /dev)
Alert! /dev/hd0 does not exist. Dropping to shell!

BusyBox V1.13.3 (ubuntu 1:1.13.3-1ubuntu) built in shell (ash)
(initramfs)_

To me it looks like Grub accepted the commands entered and that (hd0) was the correct drive but it's not right somewhere else in the boot sequence.

Any thoughts? (please)

Even tho I'm not a fan of Windows I have not had many booting problems after installing updates on it.
At the end of this line 
linux (loop0)/boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro [I]


Add the following parameter [/I]pci=nomsi

follow the others line the same as you did. I used your lines and put this parameter mine worked fine. 

post booting update the grub, sudo grub-update and then reboot. Post that i had no problem.

---

### Post by Zaphod69 on 2009-11-27
Thanks Sinurge - appreciate the help.

I've actually run the installer and have it on my system now in it's own partition. Updates are downloading right now :p

I'm sure others will use your information tho.

Looking forward to getting it all set up now and learning how to best use it :D

Cheers

---

### Post by phlip45 on 2009-11-27
So I have this same problem. Installed some updates and it now loads into Grub.

I tried the steps listed on this site: [https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)

I set the root and prefixes to (loop0) since the others didn't work. After I did this I could locate my linux files and such so I figured that was the right one. However I keep getting stuck on step 5 of the recovery thing which is the 
insmod /boot/grub/linux.mod
It says file not found. Since I don't have that file apparently I can't load the kernel which means I can't fix the problem. 
Anyway I can get around this, or somehow get this file?

---

### Post by lsk3993 on 2009-11-28
I have this problem too and was given a command that should get me into Ubuntu but it's really quite an effort to type out
> sh:grub>[B]set root=(loop0)
[/B]sh:grub>[B]linux /boot/vmlinux-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
[/B]sh:grub>[B]initrd /boot/initrd.img-2.6.31-14-generic
[/B]sh:grub>**boot**
How long will it take for the bug to be fixed so I can just type that in once and install the fix?
Or would it be better to just install Ubuntu properly as opposed to using Wubi? The only reason I used Wubi in the first place was because I didn't know which option to select from the LiveCd and i didn't want to mess up my Xp install

---

### Post by rinrada on 2009-11-28
> **sinurge said:**
> At the end of this line 
linux (loop0)/boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro [I]


Add the following parameter [/I]pci=nomsi

follow the others line the same as you did. I used your lines and put this parameter mine worked fine. 

post booting update the grub, sudo grub-update and then reboot. Post that i had no problem.


I have tried following the instructions on:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

and the various instructions in this thread, as above, and others but I keep getting stuck during the boot at the following point:-
[ 9.233181] sd 4:0:0:0: [sdb] Attached SCSI disk
Done.
Gave up waiting for root device. Common problems...

sd6 is the partition with Linux installed and the one I set as root.
This problem arose because I deleted a sd5  (in Windows) - so I guess it is finding it difficult to count to six? I hope I don't have to do a complete reinstall, please!

---

### Post by rinrada on 2009-11-29
Even reinstalling doesn't seem to work - the partition editor just hangs.[-o<

Help, please!

---

### Post by rinrada on 2009-11-29
Ok finally worked out what was going wrong - though updating the Grub is still giving problems.

For the benefit of others with similar problems - follow the instructions on
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)

However in the line
[B]linux /vmlinuz root=/dev/sdXY ro

My linux partition was (hd0,6) - be sure to use /dev/sda6 in the line above not /dev/sd06:-

It might seem obvious to some but it had me stuck for quite a while.

Now just need to update my grub2 - still getting errors.

[/B]

---

