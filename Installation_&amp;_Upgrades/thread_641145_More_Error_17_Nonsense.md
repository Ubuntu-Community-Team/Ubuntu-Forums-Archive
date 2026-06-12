---
title: "More Error 17 Nonsense"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by Vaille on 2007-12-15
Perhaps this is similar to the other threads on the topic, but I haven't seen quite the same situation just yet, even though that may very well mean that I just didn't look hard enough for the appropriate solution.

In any case, I'm trying to switch over to Ubuntu as my main OS, using Windows only for games and so forth. Seeing how I don't have my XP Pro disc with me, making re-installation of that drive something I'm trying to avoid, I'm attempting to pull off a weird bit of computer acrobatics: Drive 1 has just XP and other simple Windows-related programs on it while Drive 2 is basically just a dump for games, pictures, and movies. I'd like to partition off part of Drive 2 for use with Ubuntu and keep the rest of it for Windows access. Formatting Drive 2 isn't something I'm worried about.

Unfortunately, this sort of criss-crossing thing has led to a few different problems. The main issues are either Windows being completely unable to detect Drive 2 or Ubuntu showing up at the boot screen alongside XP, but failing to load, because my computer can't mount the selected partition (error 17). Any solutions? I'm currently running with the Ubuntu Live Disc and a stubborn, burning desire to change my OS. If any other information is needed, I'll be happy to provide it. However, this is the first time I've run into this problem, so I'm not sure where to start. Any help would be greatly appreciated.

---

### Post by Herman on 2007-12-15
Hello Vaille,
I presume you only have a single hard disk? Here is a link about GRUB error 17 [When trying to boot Linux]("http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux")                                         (if you only have one hard disk).
Some people call a partition a 'drive', and others mean a hard disk when they use the word 'drive', so I'm not perfectly clear on what your situation really is.
That link (and sub-links) should be pretty well self explanatory, and should help you solve that problem in most cases.
If your situation is different from that described or if you have any problems or questions please post here again and I or someone here will help you.

If you do need specific help, can you please post the output from 'sudo fdisk -lu' here?
```
sudo fdisk -lu
```And also a copy of the bottom part of your /boot/grub/menu.lst file as well, instructions for how to get that using the Ubuntu Live CD are in a sub-link off the link already given. Or if you use [Super Grub Disk]("http://sgd.benjamin-butschko.de/") to boot Ubuntu with, it's 'sudo gedit /boot/grub/menu.lst'
```
sudo gedit /boot/grub/menu.lst
``` Thanks.

Regards, Herman :)

---

### Post by Vaille on 2007-12-15
That was written at a fairly late hour, so I apologize for the confusion.

I have two separate hard disks. The first is about twenty gigs and has XP Pro installed. The second is closer to two-hundred gigs. I'd like to take a decent chunk of the second hard drive and use it for Ubuntu stuff, making that my main OS. However, the annoying twist in my scheme makes things a bit difficult; the rest of the drive needs to be recognizable by Windows so I can use it for gaming and the like.

It'd be much easier for me to simply wipe both drives, then install Ubuntu on the smaller one, and swap Windows over to the larger disk and use it from there. However, my XP disc is nowhere to be found. I just assume it's wherever socks go after you lose them in the dryer.

So there's my predicament. I managed to get Ubuntu on the second drive this morning, which was a simple task, but in my medication-induced stupor, I forgot to place it on a partition, basically winding up with a large drive that Windows didn't even know existed.

I've browsed around a fair bit and checked various forum threads on the issue, but all of the information I've found has assumed that the user is doing something sane like taking two hard disks and making each one exclusive to a single OS, respectively, with Windows only on the first and Ubuntu or some other distro on the second. They haven't been trying to cross things over a little, which is what's tripping me up.

I'll provide the information you asked for once I can wrangle down a somewhat stable set-up. Then I can start working on the two problems that keep arising whenever I try to make Windows and Ubuntu co-exist peacefully.

EDIT: Well, I'm back to where I was a few days ago. Error 17, with any attempts at getting the second disk to boot first being met with "Error Loading OS" blinking on my screen. Here's the sudo fdisk output.

> Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    39873329    19936633+   7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x084dba92

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63    48821534    24410736   83  Linux
/dev/hdb2        48821535    49512329      345397+  82  Linux swap / Solaris
/dev/hdb3        49512330   488392064   219439867+   b  W95 FAT32
ubuntu@ubuntu:~$

What I'm attempting to do is simply take the space not used by Ubuntu and create a shared partition between my two operating systems. This may or may not be the right way to go about doing it. I also noticed that the list looks extremely weird, as if a monkey came in there with a screwdriver and started mucking everything up.

I'd paste the end of the menu.lst, but I can't get the command to work, because the disk drive that the Live CD is in is named with numerous spaces and a forward-slash. The terminal breaks up the command line and spits out an error. I can't seem to easily rename the drive, either, and I'm starting to wonder if I should simply give Ubuntu the entire second hard drive and just stick XP Pro on a bigger one once I get the money. I've been dealing with this for days and it's starting to wear on me.

---

### Post by Herman on 2007-12-15
Okay, no worries about the confusion, but it does mean you might have been getting GRUB error 17 for completely different reasons, and here is our link about that, [GRUB Error 17 In a computer with more than one hard disk.]("http://users.bigpond.net.au/hermanzone/p15.htm#In_a_computer_with_more_then_one_hard")

Is one of your hard disks IDE (PATA) and the other one SATA?

If they are both IDE drives, please check to make sure they are plugged in and jumpered properly.
If you have a ribbon cable with  plain black plugs, that's  a standard IDE cable, and with that kind of ribbon cable you need to make sure one hard disk is jumpered as 'Master', and the other is jumpered as 'Slave'.
If your PATA cable has a blue end for the motherboard socket, a grey plug (for the slave hard drive), and a black plug (for the 'Master' hard drive, then you have a 'Cable Select' type of PATA cable, and you should set your jumpers on both drives to 'Cable Select'.
There should be a sticker on your hard drives with diagrams on it to help you get the jumper settings right. (Every brand of hard drive is different).

If you have one SATA and one PATA hard disk, there is probably not much to do as far as hardware is concerned. You probably just need to switch your hard disks around in our BIOS. See this link, [    Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority").
That could be the quickest and easiest way to fix your problem.

About your Windows XP Installation CD, you can make your own from files in the root of your Windows file system if you can follow the instructions in this link: [http://www.nu2.nu/bootcd/#wxp](http://www.nu2.nu/bootcd/#wxp)

It is normal for Windows not to be able to 'see' or detect the presence of Ubuntu, since Windows doesn't understand Linux file systems.
Ubuntu should automatically detect and mount your Windows partition though.
If you have a separate /data partition Ubuntu should mount that too, but that should not affect whether Windows can access the /data partition at all. At least not for any reasons I can think of.

Regards, Herman :)

EDIT: I noticed you have no boot flag in your second hard disk there, you should be able to fix that with a partition editor. I don't know if that would be your main problem, (I doubt it, but it would be normal to have a boot flag there somewhere).
```
 Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    39873329    19936633+   7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x084dba92

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63    48821534    24410736   83  Linux
/dev/hdb2        48821535    49512329      345397+  82  Linux swap / Solaris
/dev/hdb3        49512330   488392064   219439867+   b  W95 FAT32
ubuntu@ubuntu:~$
``` It looks like both of your drives are PATA hard disks too, so please shine a light around inside your computer case and check those jumper settings. :)

---

### Post by Vaille on 2007-12-15
I poked around in there and both drives were set up fine. The first hard disk, with Windows installed, was the master, and the second, with Ubuntu and Friends, was the slave.

Switching the boot priority of the drives resulted in the same OS loading error that I received when I attempted to alter it outside of the BIOS with the standard F11 boot menu. I'll try sticking a flag on the Ubuntu partition. If this fails, I'll simply give the entire second drive to Ubuntu and worry about the other stuff later.

Thank you for the help so far, as well as the link to the instructions for setting up an XP CD. I was looking for something on that, but never really worded the search right. Cheers for now. Let's see if I can finally sweep all of this stuff off of the table.

EDIT: Sticking a boot flag on there didn't work. Error 17 again. I'm done dealing with this for now. There's a solution somewhere, I'd imagine, but I'll have to leave all of that up to a local computer shop filled with people more experienced than myself. Thanks again for your help and patience. Have a happy holiday.

---

### Post by Herman on 2007-12-16
Okay, I was going to suggest jumpering the 250 GB drive as Master and the 20.4 GB drive as Slave next,  to see if that would do the trick.
I agree with you that is really might be better to leave any work inside your computer case to properly trained technicians though.

We never did get to see your /boot/grub/menu.lst file yet either, that could hold the key to your problems and is normally simple to fix, (if the problem is in the boot entiries).

Thanks for your co-operation and patience so far anyway. Sorry I wasn't able to help you solve the problem yet.
Bye for now,
Regards, Herman :)

---

