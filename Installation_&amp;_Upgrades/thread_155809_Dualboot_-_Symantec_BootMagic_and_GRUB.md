---
title: "Dualboot - Symantec BootMagic and GRUB"
date: 2006-04-05
forum: Installation &amp; Upgrades
---

### Post by sprogger0 on 2006-04-05
Folks,
Absolute beginner but no friend of Gates.
I use Symantec PartitionMagic V8 as well as BootMagic on WinXP.

Have 2 x SATA drives Win XP on 160GB and (after much trashing of partitions) finally got Ubuntu 5.1 to load on the 300GB second drive. I had disabled BootMagic to allow Ubuntu to load from CD.

Issue - when I finally got Ubuntu installed (with Grub) I could boot both Windows and Unbuntu using Grub.. however .. when I re-enable Bootmagic and asked it to boot Unbuntu off its drive .. Bootmagic menu comes up .. I choose Linux (UBuntu) drive and it then says preparing to boot (and doesnt get anywhere)....

Is there anyone out there who has successfully got Bootmagic to bring up Ubuntu?

Chris

---

### Post by Sef on 2006-04-05
> I use Symantec PartitionMagic V8

There are known issues with Partition Magic.  It tends not work well with Linux.  Would you be able to partition with another partitioner?

---

### Post by sprogger0 on 2006-04-05
Sef
Thanks for that ...

The issue is not with PartitionMagic (although I did manage to trash the second hardrives partition table by using both Ubuntu partioning and Partitionmagic)

The issue is that now I have BootMagic enabled (this works fine bringing up Windoze) abd GRUB has disappeared ... what I am looking to do is figure out how I can get BootMagic to boot the Ubuntu partition.

---

### Post by Sef on 2006-04-05
I found this on boot magic:

> When you installed Linux, you were asked whether to install GRUB to the MBR of the hard disk or to the Linux partition. You should have chosen the second option.

Exactly. Unlike GRUB or LILO, BootMagic will NOT be able to load a Linux kernel, however it can load any boot sector (well, fortunately so, that's the role of a bootloader to start with :p).

And loading a boot sector is what you want to do here.

[http://www.techspot.com/vb/all/windows/t-37980-dual-booting-linux-with-bootmagic-instead-of-grubHelp.html]("http://www.techspot.com/vb/all/windows/t-37980-dual-booting-linux-with-bootmagic-instead-of-grubHelp.html")

And another:

> I already had WinXP running perfectly on partition one of my first hard drive. I then made a linux partition using partition magic (i also made a swap partition). Then I installed boot magic (part of the partition magic package), and activated it. Then i rebooted the computer with the mandrake cd in the drive, and installed mandrake. When it asks you about the boot manager, INSTALL IT IN THE ROOT FOLDER OF LINUX!!!!!!! THIS IS IMPORTANT!!! Once linux is installed, reboot the computer and choose windows, and configure a linux choice in the boot magic configuration (this is in windows xp). Reboot the computer , and you should be able to boot into either system. If you choose windows, it will boot into windows. If you choose Linux, it will go to Lilo, and then you can just choose linux from there, and it works fine. Hope this was some help.

[http://www.linuxforums.org/forum/mandriva-linux-help/11744-trouble-booting-both-linux-windows.html]("http://www.linuxforums.org/forum/mandriva-linux-help/11744-trouble-booting-both-linux-windows.html")

---

### Post by sprogger0 on 2006-04-06
Sef
Many thanks .. Eventually solved this by noting down the full partion name that Ubuntu had given the /ext3 partition (/dev/sdb3) ..wiping all the partitions on the second drive .. making one large NTFS partition .. letting Ubuntu install make its own partitions and THEN ... when GRUB installer tried to install gave it the /dev/sdb3 drive name and BINGO 

Up and running ... (now onto to the next 500 questions)

---

