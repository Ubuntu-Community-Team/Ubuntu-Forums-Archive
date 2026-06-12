---
title: "Installing Ubuntu"
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by theswan on 2005-11-11
Hello everyone,
I'm a new member here. Actually, I just got a copy of OpenCD and there is a LIVE Ubuntu sample there that I can boot from my CD. I tried it and then I become interested in having a 2nd OS.
So, I downloaded the ISO file of Ubuntu 5.10 "the breezy badger". Have a new partion, my third drive from the hardisk, E:/, NTFS, having 15 Gig.
And then, I reboot, CD-priority, and installation began. I was planning to install Ubuntu in my newly created partition, E:/, however, nowhere i saw in the installation that asks me what drive should Ubuntu be installed.
I also installed GRUB to be able to select what OS I'll be using....and then now from start-up it has 4 options.
Ubuntu
Ubuntu Recovery
Memory Check
Windows XP
When I select Ubuntu from the list, there are some text the shows with [OK] on the right hand side...after these several lines, it asks for the username and password which i set-up from the installation and then I successfully logged.
My question is, is this the Ubuntu OS? I can't see the GUI just like the Ubuntu LIVE from OpenCD. Sorry if my question sounds stupid. It's my first time to install a Linux-distribution OS.

Hoping for any help. Thanks!

Also, when I logged in back in Win XP, I can't locate where Ubuntu was installed...its not in the E:/ directory i just newly created 'cause it is still empty...i'm not sure if it was installed in my 2 other HD drives, C:/ and D:/

---

### Post by etc on 2005-11-11
I'm sorry that I can't help you with the GUI problem (sounds like an X problem, trying typing in startx after you login), someone with more experience can help you with that.

The reason you can't see the Ubuntu partition from Windows is because Ubuntu uses the ext3 filesystem, and Windows only supports NTFS and FAT32.
[http://www.sourceforge.net/projects/ext2fsd](http://www.sourceforge.net/projects/ext2fsd)
Is a driver for windows that allows you to see your Ubuntu partition.

---

### Post by theswan on 2005-11-11
thanks etc..
i downloaded Ext2Fsd-0.25.zip already and ran setup.bat but nothing happens. =( did i download the right file?

thanks.

---

### Post by theswan on 2005-11-12
please ignore my post just above, i figured out how ext2fsd works...=)
my new question is this.
i have a partitionMagic installed in my PC, and when i use WINXP and open Partition Magic, i saw some other partitions that weren't there before i installed Ubuntu...
Now, i have something like this:

Partition                        Type              Pri/Log          Size (MB)

C:                                NTFS             Primary          38,060.2
*                                 Extended        Primary          38,052.4
D:                                NTFS             Logical           15,170.7
/(*:)                            Linux Ext3       Logical             9,389.5
SWAPSPACE2(*:)            Linux Swap     Logical                439.2
E:                                NTFS             Logical            13,052.8
Local Disk(*:)                 Type 88         Primary               204.0

Could anyone confirm me what is really necessary for Ubuntu?
As i remember, what I have before installing Ubuntu are partitions, C:, *, D:, and E:. So, three partitions were added upon Ubuntu installation, which are partitions: /(*:), SWAPSPACE2(*:), and Local Disk(*:).

Are these three additional partitions required?

thanks for any help. ciao!

---

