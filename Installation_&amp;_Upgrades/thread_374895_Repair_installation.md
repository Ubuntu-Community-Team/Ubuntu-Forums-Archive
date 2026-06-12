---
title: "Repair installation?"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by bullgr on 2007-03-03
hi...

i upgraded today my pc, and now i must reinstall winblows and ubuntu.

in winblows there is a method to repair the current installation. so, repairing the current
installation, installs the correct hardware components and i don't need to reinstall all the
programs and stuff.

so, my question: is any, like in winblows, method in ubuntu to repair the current installation
after upgrading the mashine, to avoid a fresh install?

it's really frustating to install all the stuff from the beginging. my ubuntu installation is from
breezy and i already have two succesfull updates (to dapper and to edgy).

thanks...

---

### Post by Herman on 2007-03-03
I used to just back up all my files to another media and then resize the partition as small as I can with [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")  and copy it and paste a copy of it somewhere out of the way, like close to the end of the hard disk. It takes about 3 GB of disk space. Then I resized the main install to normal size again and replaced files as needed. If anything happened to the main partition later, I would recover the files and delete the partition, and paste the backup copy of the operating system back to the free space and resize it to normal size. It only takes about ten minutes. This preserves added software, updates and settings. That's the way I used to do it before Edgy Eft came out.

However, since Edgy Eft began using filesystem UUID numbers in /etc/fstab, one needs to be aware to make sure we are mounting the correct root filesystem. Fiesty Fawn has UUID numbers in /boot/grub/menu.lst now as well. Actually, that might make it easier.  The original partition is given a new UUID number. Just leave the original partition as the backup, and resize the new one larger instead, and use the copy, since the copy is the one that is given the original UUID number.                       [About Edgy Eft's new /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")
With Fiesty it will only be necessary to edit the menu.lst file with the new partition number after the 'root' command.

Another way is to use Partimage. Partimage can be installed in Ubuntu, and it is also included in [GParted -- LiveCD.]("http://gparted.sourceforge.net/livecd.php") The best how-to for partimage is this one by aysiu, [Use PartImage]("http://www.psychocats.net/ubuntu/partimage")  Once you learn how to use Partimage, it is almost as fast as copying and pasting the whole partion with GParted, but it has the option of using file compression, and also it turn the operating system into a file, or a series of files, that can be copied to other media, such another partition or an external hard drive or DVD or CDs. However, it is more complex, and I lost an operating system once because of an error in the file compression. I think probably errors like that are rare though.

Then there's the simple old-fashioned reliable 'dd' command. It takes longer than Partimage, but it's simpler and should be very reliable. [**Learn The DD Command Revised**]("http://www.linuxquestions.org/questions/showthread.php?s=&postid=1848770")

Those three methods are all very effective, I have tried them all and they all work well for me. They do require a little bit of learning on the part of the user, but if I can do it, you should be able to as well.

Regards, Herman :)

---

### Post by bullgr on 2007-03-03
no, the upgrade i did is only the motherboard, cpu and graphic card.

the hard disks are the same, so i don't need to copy partition etc.

the problem is (that i wrote above) after the upgrade (and the hardware changes) i am not
able to boot in ubuntu and winblows.

this is normal, because the hardware charges. in winblows this can be done with the repair
installation method.

my question was, if is a same method in ubuntu, to repair the current installation,
without the need to install ubuntu from the beginging.

---

### Post by Herman on 2007-03-03
Oh, sorry, I misunderstood.

Okay then , try this instead and see if it helps you, this is for the graphics card.             [sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html")

I don't know if you need to do anything for the motherboard and cpu. If you do then I don't think I know the answer, maybe someone else can help. But try the link I gave above first and see if that's all you need.

Regards, Herman :)

---

