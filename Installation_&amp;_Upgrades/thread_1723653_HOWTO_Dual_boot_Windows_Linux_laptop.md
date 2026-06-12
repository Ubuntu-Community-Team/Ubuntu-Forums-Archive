---
title: "HOWTO Dual boot Windows Linux laptop"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by Leo Rivers on 2011-04-07
How I made my Dual boot ****Windows XP **** Linux laptop work

PLEASE SEE WARNINGS IN THE COMMENT DIRECTLY AFTER THIS ONE!


> If people blindly follow your instructions and have (more likely these days) a Vista or Windows 7 PC, they will most likely corrupt their existing installation -- by allowing the Ubuntu installer to shrink their Windows install.

If you're going to put stuff like this out the the community, you need to be careful to qualify it by indicating it is for Windows XP, NOT for Vista or Windows 7 users.

If you intend this to be used by Vista or Windows 7 users, you need to add wording about using Windows to shrink their OS, NOT using the Ubuntu installer or GParted.

Also, because installing dual-boot runs the risk of corrupting the Vista/Win7 boot loaders, which generally does not happen with Windows XP, you need to add instructions for folks to obtain Vista or Win7 Repair CDs -- so they can repair their boot loaders.  Mark Phelps 


*I am NOT a linux guru, I am just sharing the results of my efforts! *






Your goal is to have a laptop into which you can boot Windows or Linux.

Your primary understanding is that Windows XP is an old operating system and makes some important ignorant assumptions.

The first assumption is that Windows was a proprietary computer operating system produced by a Corporation that wanted a monopoly control of the computer operating system market. This meant that it would

Assume that it was going to be the only operating system of the computer

And assume that it need no capacities to recognize the presence of any other operating system or file system.

This first assumption that Windows would be the only operating system of the computer means that you have to install a boot record and a bios that establishes that this computer is &#8220;compatible&#8221; rather than name the more efficient modern setting.

The second assumption means that you have to make sure that Windows is installed in the first true partition right at the front of the cylinder. You can install Linux in a logical partition behind that on the hard drive.

Linux is a modern computer operating system and is adaptable to its environment and is produced in a way that it recognizes other computer operating systems on the hard drive and it can install itself anywhere.

Your secondary understanding is that you will have to first install Linux to prepare the hard drive if such a way as that there is a NTFS formatted partition in your very first primary, (first) partition, i.e.  /dev/sda1. This is for windows to reside in. Part of the secondary understanding is that you don't install all the bells and whistles with this Linux installation because you are going to nuke the boot record when you install Windows into the partition. This is no problem because then you will install Linux a second time and then it will create the boot record in grub and make everything happy.

Part of the secondary understanding is that you will install Linux for the primary purpose of downloading gparted, a partition manager, and move your partitions around if you want to save your data or whatever. I have a better idea.

By far better idea is that you do what I ended up doing which is to 

&#8212; Boot from a live Linux disk.

&#8212;  backup your data to a thumb drive or USB drive.

&#8212; Boot from a live Linux disk

&#8212;  just nuke and repartition your hard drive so

&#8212;  there is an empty NTFS Partition at  /dev/sda1.

&#8212; Make sure that the setting for your  bios is set to &#8220;'compatible&#8221; this is the reason (for probably about 24 failed Windows installs where Windows simply couldn't see the partitions I was making for it. I am not exaggerating the number of failed attempts)
&#8212; Install Linux lightly into the first part of a logical extension making room for a swap drive that is twice the size your RAM memory

&#8212; Make sure the boot flag on the partition that Windows will reside is set to &#8220;boot&#8221;

&#8212;  Reboot with the Windows disk that you have. It will now see where it is supposed to go, being completely blind to everything that's in the logical extension. As long as you don't choose to format your hard drive all the damage that Windows will do will be to put Windows on your computer. That is enough.

&#8212; During the install leave the room and do something fun because looking back at the computer while Windows is installing can make you crazy.

&#8212; Reboot into Windows and there is something that you will do here but I will NOT mention here for clarity but I will make an endnote containing that information.

&#8212; Setup Windows to please yourself.

&#8212; reboot from the live Linux distribution. 

&#8212; Install Linux. It will ask you about whether you want to just install it along with an operating system or not. I hope it is not necessary for me to answer that question for you.

&#8212; At this time Linux will rewrite the boot data so from then on when you start a computer you can hit escape and get that menu that let you choose whether you want to run Windows or a modern operating system.

&#8212; Now what you'll want to do if you don't have the CD that came with the computer with the drivers for your laptop is to Ethernet cable connect your laptop to a computer with an Internet connection. Go to your laptop manufacturer's website and download the drivers for the Windows operating system wireless app. Then when you reboot into Windows with that installed you can connect to the Internet and get all the rest of the drivers and whenever you want in the way of apps.


I want to thank everybody here on the Ubuntu List for helping me figure out the various parts of this puzzle. It is my ignorance but they have kindly endured. I would also like to thank Kevin Ashley of Clever Pepper who is who volunteer Linux guru at the Cottage Grove Oregon volunteer computer clinic on Wednesday nights for helping you put the pieces together the right order.

May all beings benefit
Leo Rivers.
Thursday, April 7, 2011 6:51:28 AM

---

### Post by Mark Phelps on 2011-04-07
If people blindly follow your instructions and have (more likely these days) a Vista or Windows 7 PC, they will most likely corrupt their existing installation -- by allowing the Ubuntu installer to shrink their Windows install.

If you're going to put stuff like this out the the community, you need to be careful to qualify it by indicating it is for Windows XP, NOT for Vista or Windows 7 users.

If you intend this to be used by Vista or Windows 7 users, you need to add wording about using Windows to shrink their OS, NOT using the Ubuntu installer or GParted.

Also, because installing dual-boot runs the risk of corrupting the Vista/Win7 boot loaders, which generally does not happen with Windows XP, you need to add instructions for folks to obtain Vista or Win7 Repair CDs -- so they can repair their boot loaders.

---

