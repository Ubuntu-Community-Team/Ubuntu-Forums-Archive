---
title: "I really F@$^ed up"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by Virtuosity0021 on 2007-05-20
So, as a fan of ubuntu, I tried to install it myself.  That was my first mistake.  My second came when I, the extremely novice beginner, tried to make it a dual boot.  Dammit.  My OS was Windows XP Professional, on a Dell C840.  

So I installed it on my External hard drive, 30gb, 2 partitions.  Everything went well, the files on the windows disk (I have 2, including the extrernal one) are seemingly all in tact.  When I try to boot, however, the dell bios comes up, passes, and I get:

> Grub loading stage1.5  -(or something like that)

Grub couldnot etc etc etc...
Error 21.-I can get details on this if necessary.

So I am really in a pickle here, as this is not exactly my computer.  Any help would be great, and preferably, at the moment, I don't want ubuntu on my computer.  If at all possible, I would like things back to windows XP pro for now, running as before.  Im guessing that the bios will need to be changed.  

Please help!  And if possible, please use detail, as I am (obivously) a noob.  Thanks!!!

-If there is an EASY way to make this a dual boot system, i'm all for it.  Also, the startup disc I have doesn't work when I boot from a cd-rom in the boot menu.  It gives the same error.

---

### Post by Peter09 on 2007-05-20
Hi,
I am a newbie as well, it is worth persevering with Ubuntu. Anyway some small bit of help until an expert arrives. Go here and you will find the GRUB command lines which will allow you to boot to windows using GRUB.

[http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI](http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI)



Hope this helps

---

### Post by kerry_s on 2007-05-20
Just pop in your windows cd and use> fixmbr

---

### Post by Peter09 on 2007-05-20
Heres some info on error 21 if you want to go ahead with dual booting

[http://www.mepis.org/node/7330](http://www.mepis.org/node/7330)

---

### Post by bulldog on 2007-05-20
> **Virtuosity0021 said:**
> So, as a fan of ubuntu, I tried to install it myself.  That was my first mistake.  My second came when I, the extremely novice beginner, tried to make it a dual boot.  Dammit.  My OS was Windows XP Professional, on a Dell C840.  

So I installed it on my External hard drive, 30gb, 2 partitions.  Everything went well, the files on the windows disk (I have 2, including the extrernal one) are seemingly all in tact.  When I try to boot, however, the dell bios comes up, passes, and I get:

-I can get details on this if necessary.

So I am really in a pickle here, as this is not exactly my computer.  Any help would be great, and preferably, at the moment, I don't want ubuntu on my computer.  If at all possible, I would like things back to windows XP pro for now, running as before.  Im guessing that the bios will need to be changed.  

Please help!  And if possible, please use detail, as I am (obivously) a noob.  Thanks!!!

-If there is an EASY way to make this a dual boot system, i'm all for it.  Also, the startup disc I have doesn't work when I boot from a cd-rom in the boot menu.  It gives the same error.

Can you boot from an USB device?
If yes you have to fix the windows MBR and install GRUB on the USB disk with ubuntu.
If not installing ubuntu on an external disk is rather useless.

Grub is now installed on your first boot device,but can't find your external hdd.
So it can't find the menu.lst to boot.
No panic,just use the windows install disk and go through the pre install steps till you get three options.
1/ install windows
2/repair a windows
3/exit

Choose the second option which will bring you to a recovery console.
You'll have to provide the administrator password and then you can choose the windows install,most likely one.
Then type fixmbr and fixboot,you'll get a warning but ignore that and go through.
After that reboot and windows will be boot able again.
You can format your ubuntu partitions in ntfs again and your done.

---

### Post by Virtuosity0021 on 2007-05-20
Thanks guys.  As of right now, I have a grub help disk, which enabled me to temp. boot to windows.  

Also, the "startup disk" that I have, is defunct.  When i pop it in, reboot and try to boot from the IDE device, I still get te grub error.  Because of this I cannot get into the recovery console.  

Any help on how to make a recovery disk, or what to do from here would be nice.  

Also, when I hook up the HDD with linux on it, windows wont recognize the drive at all.  Before installing ubuntu, I had made 2 partitions.  1 at 25gb for music and such (something I actually backed up) and a 5gb partition for the linux, which I set as the ext2 with mount point /.  I used the 25 gb partition as the swap partition....something  I probably shouldn't have done.  

I need to learn to do things only when I know exactly what i'm doing.  This isn't the first time I've messed up something with windows:p

Thanks again guys, i really enjoy the help.

---

### Post by PrimoTurbo on 2007-05-20
All you need to do is use your Windows XP cd, the exact same cd you use to install Windows XP with. There is no Start up disk or anything like that anymore, only Windows 98/Me and lower required a boot disk.

If your Windows XP CD doesn't work then you can simply get a boot disk from here, [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

I used to use a Windows 98 boot disk (floopy) to reset my MBR for a long time, before I even realized the Windows XP CD had a recovery console.

The command to fix the mbr might be different depending on the version of the recovery console/bootdisk so try the following in this order.

Try:

fixmbr

if it doesn't work try:

fdisk /mbr

Good Luck

---

