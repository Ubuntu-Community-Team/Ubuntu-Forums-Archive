---
title: "Backing up windows XP and installing ubuntu in a dual boot system"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by RRoman42 on 2008-05-28
Hi everybody,

I've played around with the ubuntu 8.04 live-cd for a bit, and decided that I want to make the jump to a dual boot system. However, I'm rather afraid of mucking up my windows xp install, and would much rather have a backup/disk image available in case things go tits up. I've got an external harddrive with some space, and I've already got my photos, music and documents backed up there, but I don't know what the best way of backing up my windows drive is. 

Here's what I'm working with:

My laptop is an Acer Extensa 4101 WLMi (apparently very similar to the Aspire 1690) with 1.6GHz, 1 GB of RAM and a ~74GB Hard drive divided as follows:


- a "PQSERVICE" partition of 2.93GB. I presume this is some sort recovery partition for windows, since it says "EISA-configuration"

- C: drive (FAT32, size: 35.7GB, 11.9GB free) which is composed of approx. 6 GB of games, and ~16GB Windows XP and associated crud 

- D: drive (NTFS, size: 35.8 GB, 5,37 GB free) where I have my personal files, my pictures and music, as well as some games and programs. I have already backed up everything important to my external hard drive.


I also have a ~150GB external Harddrive which is divided as follows (all partitions are NTFS, but I can reformat some of them to FAT32 if necessary. All partitions are 32GB, except L: which is 21GB):

- H: drive ("Backup 1")  is currently empty; I figured this is where I'd backup my windows partition to, reformatting to FAT32 is necessary.
- I: drive ("Backup 2") is where I've got my files from the D: drive backed up to.
- J: drive ("More movies"): Some movies on here.
- K: drive ("Movies"): Some movies on here.
- L: drive ("Misc"): Various bits and bobs on here.

I've attached a screenshot with all this info in case I haven't myself clear.

Now, what would be the best way to backup my C: drive to my H: drive? Should I use partimage (if yes, does that come on the live-cd? if not, how do I get it?)? Should I just start up the ubuntu live cd and copy the files manually? Do something else? I'm planning on making the C: partition smaller during the ubuntu install, by the way.

Also, if anyone has any tips on how I should plan my partitions, feel free to share.


Thank you very much for your help :)

---

### Post by Pumalite on 2008-05-28
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by Herman on 2008-05-28
The most important thing is to make a backup of your important files.

Make sure you don't delete any of the partitions you already have there when you are installing Ubuntu. 
Some Acers with 'E Recovery', and there may be files stored in the 'D' drive, without which you may receive annoying error messages at each boot-up. For that reason, do not just erase your 'D' drive and install Ubuntu in it. It is better to resize your existing partitions instead, and move them towards the beginning of your hard disk. The idea is to make some free space to install Ubuntu in at the end of the hard disk. You can probably do that easiest if you use Gnome Partition Editor from the Ubuntu Hardy Heron Live CD before you start your installation.

Then when you get to the partitioning stage of the installation, probably if you just select 'Guided - use the largest continuous free space', Ubuntu will install just fine all by itself. Because three of your maximum of four allowed primary partitions per hard disk are already occupied, Ubuntu will need to make an 'Extended' partition at the end of your hard drive, and make a logical partition inside it for installing Ubuntu in, with another logical partition for the swap area after it. 

[GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") can be used for resizing your partitions in a low memory computer if the full Ubuntu LiveCD has problems running properly because of lack of memory, and if you make a swap area with that, then your Ubuntu Live CD will boot and will work a lot better because of the swap area on the hard disk. It's possible to install Ubuntu in a computer with as little as 256 MB or even less installed memory if you do it that way.
GParted LiveCD has Partimage already included in it, but you will need to mount your file system in your USB drive with commands in the terminal. After that you will be able to use partimage to make backups of the file systems in your hard disk.

Aysiu has an excellent web page about how to use partimage. [Use PartImage]("http://www.psychocats.net/ubuntu/partimage")
It would be a great idea (but not compulsory), to make a backup of all your partitions with partimage. You may do that before or after the installation of Ubuntu.
I installed Ubuntu in a friend's Acer and made a partimage backup of their Windows C: drive and stored it in Ubuntu for them. Months later it came in very handy when their Windows installation came down with an incurable virus. I was able to restore their Windows installation perfectly for them from the partimage backup in Ubuntu, after nothing else would work. 

For Windows XP and some other versions of Windows, (excluding Vista as far as I know), you can make a useful bootable Windows LiveCD.
After you have one of those you can even make your own Windows Installation Disc. You can use commands in Ubuntu to help you do that. Here is a link to that site, [BartPE]("http://www.nu2.nu/pebuilder/").
If you have a proper Windows Installation CD, you will be able to run important commands like CHKDSK, FIXBOOT, and others that you may need for fixing or maintaining your Windows installation, or even re-install your very own Windows OS in case something goes wrong and your Acer Recovery partition won't boot or doesn't work, (like for example, a virus nukes your partition table or something like that).
You should check up on the legalities yourself with your particular computer manufacturer before making your own Windows Installation CD. You may find that you are actually very restricted in what you can and cannot do with your own computer, depending on the terms of the license agreement you signed, which is why you should use free software instead. 
You can rely on free software, free software is always repairable or re-installable if you can't repair it.

---

