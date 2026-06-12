---
title: "Problems with new Ubuntu install"
date: 2005-05-28
forum: Installation &amp; Upgrades
---

### Post by speedsix on 2005-05-28
Hi, relatively new to linux so go easy on me!

Have been running suse 9.2 on an amd 64/nForce 3 system for a couple of weeks with absolutely no problems atall. Have tried both 32/64bit suse, both work well.

I tried to install Ubuntu Hoary 5.04 64-bit on a separate partition and am having 2 main problems. I have XP/Suse/Ubuntu on separate partitions, initially with both Linux installs sharing a swap partition and then when I had problems separate swaps. Anyway the problems..

1. Ubuntu locks up after a random amount of time requiring a reboot, I can't get to a console so the hernel has hard locked by the look of it. Not to sure how to begin troubleshooting it. I'm assuming it is the kernel that has locked up (slightly newer than the suse kernel) and not the gui. Can't see anything untoward in the logs although didn't really expect to. Seems to lock on mouse clicks, resizing windows etc. usually within 15mins from boot.

2. Ubuntu also seems to break my Suse install, it boots into some sort of repair mode saying fsck failed on one of my partitions (not /). If I run the Suse repair from the cd and select the FSTAB checker it finds some faults, fixes them and I can boot back into Suse (but no longer Ubuntu).


If anyone can offer any advice on these two problems it would be much apreciated as Ubuntu looks very good from what I have seen. 

Thanks

Dom

---

### Post by speedsix on 2005-05-29
Anyone, I really want to start using Ubuntu? 

Thanks
Dom

---

### Post by Robokev on 2005-05-29
I would try only having one OS per drive. that could be freezing it up. other than that, maybe try to reinstall it.

---

### Post by crane on 2005-05-29
Maybe a little more hardware info would help some people trouble shot with you.
Ireally wound't worry about have multiple OS's on one drive. I'm running 4 plus a game partition and a music partition. :) 

As far as grub. Maybe you could post your config from you grub (/boot/grub/menu.lst) file. It sounds like a simple enough problem to fix.

---

### Post by ambientcomposer on 2005-05-29
I just bought a computer (dirt cheap) from a friend who has slackware on it but he can't remember the password *he says*. Anyway, I can't get anywhere and I really just want to reformat the computer and put ubuntu on it. Trouble is I don't even know where to begin. When I boot up I get a login prompt and then a prompt for password; neither of which I know. Is there a way for me to over-ride that? I have a Ubuntu iso but do I need a boot disk, or something? I don't have a floppy drive on the computer. Also, this computer will only be used for ubuntu, no dual boot or anything. 

I've looked at several places online and haven't been able to find anything that'll help me. I don't know much about the computer's hardware either. Could you please help me or point me in the right direction.

Thanks,
Stephen

---

### Post by speedsix on 2005-05-30
[QUOTE=crane]Maybe a little more hardware info would help some people trouble shot with you.
Ireally wound't worry about have multiple OS's on one drive. I'm running 4 plus a game partition and a music partition. :) 

As far as grub. Maybe you could post your config from you grub (/boot/grub/menu.lst) file. It sounds like a simple enough problem to fix.[/QUOTE]
I have sorted the grub problem out by not mounting the Ubuntu files within my Suse install. Suse works fine alongside Ubuntu now but I still get frequent hard lockups in Ubuntu.

System is a AMD 64 on a Gigabyte nForce 3 mobo with Radeon 7000.

Have tried install Linux nForce drivers from nVidia but still the same problem, has anyone got any suggestions where to begin trouble shooting?

Many thanks

Dom

---

### Post by grim42 on 2005-05-30
[QUOTE=ambientcomposer]I just bought a computer (dirt cheap) from a friend who has slackware on it but he can't remember the password *he says*. Anyway, I can't get anywhere and I really just want to reformat the computer and put ubuntu on it. Trouble is I don't even know where to begin. When I boot up I get a login prompt and then a prompt for password; neither of which I know. Is there a way for me to over-ride that? I have a Ubuntu iso but do I need a boot disk, or something? I don't have a floppy drive on the computer. Also, this computer will only be used for ubuntu, no dual boot or anything. 

I've looked at several places online and haven't been able to find anything that'll help me. I don't know much about the computer's hardware either. Could you please help me or point me in the right direction.

Thanks,
Stephen[/QUOTE]

If you can boot from the Ubuntu install ISO you can just do a normal installation. It will overwrite the hard drive completely.

You may need to go into the BIOS setup and configure it to boot from CD-ROM first not HDD.

---

### Post by speedsix on 2005-05-31
Hi again,

Ubuntu is crashing when I select something or click the mouse.

I think it has something to do with driver kernel modules, if I run lsmod the list is ALOT larger than my suse install and it doesn't contain certain entries like amdagpgart etc.

How does linux decide which modules to load at boot? Does it just scan through /lib/modules/ and pick what it thinks it needs or is it hardcoded somewhere?

Many thanks

Dom

---

### Post by mingus on 2005-05-31
First, there is no issue with running mult distros same box.  My SOHO has SuSE (my main, admin sys), Ubuntu, Kubuntu, Xandros, Yoper, XP - no prob at all.

You may have rcvd the fsck msg because your fstab is loading the other partitions and it either has a parm error in the file or one of the partitions is using a non-journaled filesystem that it thinks has a problem (ala fat32 and chkdsk in W$ land).

Apologies in advance for the length of the following - frankly, I'm hoping you find something I haven't yet which may clear this up.

I have been struggling a bit with the kernel module procedure as well.  It appears that Debian uses a different method, and from what I've researched, either that has changed or Ubuntu is doing something different.  There is a program named modconf ref'd in the docm that is menu-driven and helps build /etc/modules.conf.  However, I can't find modconf in Ubuntu and don't have a Debian install to compare to.  Furthermore, many posts will refer to the program update-modules, which writes out the same /etc/modules.conf file.  Replacement for modconf?  However, man update-modules indicates this is an obsolete command.

In any event, when I ran update-modules it didn't do anything however, until I stumbled onto the deb package modutils; after installing it update-modules worked.  The directories /etc/modutils/ and /etc/modprobe.d/ are where the input files are, and where you define modules you want the kernel to recogonize.  You then add the module name to file /etc/modules and it should then be loaded by the kernel at boot.

I found that without the necessary entries in /etc/modutils/, with sometimes options also defined there, and the /etc/modules.conf file built, that I would get errors trying to load the module whether it be manually with modprobe or at boot via /etc/modules.

When you look at /etc/modules you will see the modules the kernel has detected that needed to be additionally loaded.

That's all I've learned so far.  SuSE uses an entirely different approach which is maintained via the YAST interface, so this is new stuff to me.

--mingus

---

### Post by ambientcomposer on 2005-06-01
[QUOTE=grim42]If you can boot from the Ubuntu install ISO you can just do a normal installation. It will overwrite the hard drive completely.

You may need to go into the BIOS setup and configure it to boot from CD-ROM first not HDD.[/QUOTE]
 I wasn't able to boot into the BIOS but I reset the BIOS settings by reseting the CMOS battery and that allowed me to change the boot device to cd so that I could bypass the login to linux. So far ubuntu looks pretty sweet. Real smooth installation. Thanks for the help.

---

### Post by speedsix on 2005-06-01
Excellent thanks for the reply, I have only been using linux for a few weeks so the concept of modules is a little confusing!

Still trying to troubleshoot the freezes, have found the following;

Can reproduce lockups everytime by repeatedly resizing a column quickly in Synaptic.

Cannot SSH into Ubuntu once locked

[may be related?](https://bugzilla.ubuntu.com/show_bug.cgi?id=10668) 

Tried both regular AND k8 kernel

Running on standard drivers

Kubuntu only locked up once, changed the permission of powernowd as suggested in BugZilla and it didn't lock up again during the next 30mins or so, Ubuntu locks up often.

'Failsafe Gnome' still locks Ubuntu up

Suse runs fine


Dom.

---

### Post by mingus on 2005-06-01
Hmmm . . . Thinking back, over the years the reasons I've seen this symptom have been due to an access problem with the disk (structural, corrupted partition table), a corruption in the filesystem (broken journal, unrecoverable bad blocks), faulty memory manager or application's use of memory (but only in Windows), and bugs in the GUI.

I'd first be inclined to try mounting the Ubuntu partition under SuSE, and then beating on it with some big programs.  For example, in GIMP you define a large swap file (not partition) and it is of course, memory intensive.  Try reading/writing a large graphics image to that partition.  And check dmesg for any abnormalities being returned by the kernel when the partition is loaded (do so from both Ubuntu and SuSE?).

You could try to access the partition table with a partitioner like cfdisk - not to change anything! - just to make sure the table can be read.  

And have you tried Ctrl-Alt-Backspace to kill the X-Server and put you back in the boot shell?  When you do that are you locked at the prompt, too?

Have you created any partitions or done any formatting on this disk with non-Linux partitioners?  Have you used more than one different partitioner on this disk?

All I can think of at the moment.

PS.  BTW re modules, I've since been told that /etc/modutils/ and /etc/modules.conf was changed in the 2.6 kernel to /etc/modprobe.d/ and /etc/modprobe.conf.

---

