---
title: "Installation on second disk"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by thewildprophet on 2008-04-24
Dear all,

I'd like to install the new ubuntu on a second SATA disk. on the main I have win xp installed.  however, i'd like the system to boot from the second disk should the first one not be there ... is it possible ? in other words i don't want the installation system to overwrite the windows MBR ... but I still want to be given the dual boot capabilities.  I might need to reinstall windows again in the near future, or i might decide to move the Ubuntu HD to another pc.

thank you 

luka

---

### Post by Herman on 2008-04-24
:) Hello .

Sure, it's easy to install GRUB to the MBR of any hard disk you want.

Your computer will always boot from the first hard disk though.

There are lots of different ways you can achieve your goal.
One way is to make your Windows hard disk the second hard disk and your Ubuntu disk the first one, and then install Ubuntu.
Ubuntu will install GRUB to MBR in the first hard disk, and Windows should be set up with a pair of 'map' commands in GRUB, to trick it into thinking it's still in the first hard disk. That means you won't need to edit boot.ini.
Here are two good threads explaining that, [**Dualboot Two Hard Drives**]("http://www.ubuntuforums.org/showthread.php?t=179902"), and[CENTER][LEFT][**Trying to Dual Boot, using two HD's**]("http://www.ubuntuforums.org/showthread.php?t=120994")

[LEFT]Another way you can do it is to leave your hard disks the way they are and install Ubuntu on your second hard disk and install GRUB to your second hard disk's MBR.
If you do that Ubuntu won't boot.
Not unless you press your F8 key or F12 during boot-up or whatever key it is that brings up a boot menu from your computer's BIOS, (if your computer's BIOS has that feature, most do), and select your second hard disk.
Then Ubuntu will boot.
To direct GRUB to install in a non-first MBR or in a partition (boot sector) or wherever you want, you need the Ubuntu 'Alternate' Installation CD. See the following link for details, [Ubuntu Hardy Heron Two Disc Multi Boot]("http://users.bigpond.net.au/hermanzone/p14.htm").
 The Ubuntu 'Desktop' Live/Install CD may be able to do it too. You can try by hitting the 'Advanced' tab in step 7 of 7 of the install, and type in (hd1), on the line for where to install GRUB to.
See the following link for details,[COLOR=#000000][Hardy Heron Beta / Gutsy Gibbon Dual Boot Installation A]("http://www.herman.linuxmaniac.net/p24.html") [/COLOR]

Actually, it would be okay to install GRUB to both or all hard disk's MBRs.
GRUB is clean and safe, whereas Windows is subject to viruses which infect the MBR and boot sector. Windows will boot okay from any boot manager in the MBR, but it's boot sector is vital.
GRUB has far more features and capabilities than any other boot manager or loader.
You could make a dedicated GRUB partition on all of your hard disks and install GRUB to MBR in all of them and you'll never have any problems booting under any circumstances, if you know how to use GRUB.  [How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").

Regards, Herman :)
[COLOR=#000000]
[/COLOR][/LEFT]
                                                                                                                                                                                                   [/LEFT]
[/CENTER]

---

### Post by thewildprophet on 2008-04-24
most impressive, thank you so much !

---

### Post by Herman on 2008-04-24
:) Okay, you're most welcome, maybe your post will help someone else with the same question too.
Thanks for saying thanks!

Regards, Herman :)

---

