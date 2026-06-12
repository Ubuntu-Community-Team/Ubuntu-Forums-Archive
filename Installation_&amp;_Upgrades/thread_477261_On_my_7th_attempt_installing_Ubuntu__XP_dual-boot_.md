---
title: "On my 7th attempt installing Ubuntu / XP dual-boot system"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by dkim68 on 2007-06-18
I have a dual-booting Dell Inspiron 6400 laptop that currently has Windows XP installed on it and a previous install of Mandriva Linux. I was using System Commander to select the OS from a boot menu. Even though I did not need it, Mandriva installed GRUB on it's ROOT partition. I set it with a timeout of zero so it loaded Linux upon reaching the GRUB menu. I tried once to say no to installing GRUB during installation and just strictly use System Commander as the bootloader but Mandriva wouldn't have it.

Anyway, back to the point, now I want to switch from Mandriva to Ubuntu. I didn't have a seperate /home partition in Mandriva so I  backed up all my e-mails, etc. onto a CD-ROM. I formatted the Mandriva partition and have tried at least SEVEN TIMES today to install Ubuntu but am unable to get it to boot up. Whether it's System Commander not seeing it or setting the Linux root partition as active and getting an error. I have yet to see the Ubuntu desktop loaded from my hard drive (only the install CD).

First, I'm not certain I'm partitioning correctly. The install is going on a 120GB hard drive of which 70GB is reserved for Windows XP and apps. The rest of the unallocated space where I want to install Ubuntu is about 40GB. I wanted to manually divide up the space this way:

ROOT - 15GB - /
SWAP -   2GB
HOME - 23GB - /home

I don't know if the ROOT and HOME partitions should be PRIMARY partitions? OR enclosed within an EXTENDED partition as two LOGICAL partitions? And should they be of type EXT3?

I tried creating a "/boot" partition of 512MB EXT3 but then the status for my 23GB of space I'd reserved for the "/home" partition became "UNUSABLE". ??? So I read that a /boot partition wasn't necessary and that the GRUB files could reside on the root partition. Which must be true since that's how my Mandriva install was working. After doing away with a "/boot" partition the 23GB of space for the "/home" partition suddenly became usable again. ??? I think this is because I had too many partitions specified as PRIMARY, but I'm not sure.

I've tried various methods from Ubuntu install's built-in partitioning, Gparted, Partition Magic, System Commander's Partition Wizard, all with no luck.  I'm at my wit's end and ready to throw in the towel here. ](*,)

Can someone please help me? :shock:

---

### Post by Toet on 2007-06-18
I use a similar configuration of the harddisk, all primary partitions, you can have 4 primary partitions max. I use reiserfs and used to use ext3, no problems there. 

On Ubuntu install I choose grub install in mbr of the first harddrive. After installation add the xp partition in the /root/grub/menu.lst. That should be all you have to do.

Don't know if grub works with other boot program, that could be a problem.

---

### Post by dkim68 on 2007-06-18
SUCCESS!!! I just got it to work! \\:D/

The problem lied in System Commander's inability to automatically detect that a Linux OS had been installed. The key ended up being to follow this little procedure from Avanquest/VCOM System Commander's website:

[SIZE="3"]"If LILO or GRUB is installed using the Partition method, sometimes Linux may not appear immediately on the OS Selection menu. This is typical of an installation to the extended partition. Follow these steps to make it appear:

From the OS Selection menu, press (Alt-S) for the Settings options.
Select the Order Add and Remove menu.
Press Alt-A to Add.
Select the Partition option.
Highlight the Linux Native or UNIX-83 partition.
Press Alt-T to toggle the bootable status of the selected partition to Yes.
Return to the OS Selection menu, the selected partition will now appear."[/SIZE]

Someone had posted a link to this info on another board. If I hadn't done a web search and found his post I would've never figured this out.

---

