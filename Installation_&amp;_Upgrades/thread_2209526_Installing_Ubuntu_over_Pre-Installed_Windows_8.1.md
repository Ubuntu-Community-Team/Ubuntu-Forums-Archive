---
title: "Installing Ubuntu over Pre-Installed Windows 8.1"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by Pushkar_Kurhekar on 2014-03-06
Hey guys. I have an HP Pavilion 15-n013AU, it has come preinstalled with Windows 8, I have upgraded to windows 8.1 through the windows store. Now, I don't really want windows anymore, and I want to switch to Ubuntu 13.10. This is what I basically want to do.

[LIST]
[*]Backup / Get ISO / Install Media of Windows 8, which will be compatible with my OEM serial key.
[*]Delete Windows 8 completely, **no dual-booting,** I want to use my 1TB hard disk to the fullest.
[*]Install Ubuntu 13.10 ( I assume it will be like a normal USB / DVD install after the above has been completed)
[/LIST]

And one important question, what is the Recovery partition in my File Explorer? It says RECOVERY (D:). 2.45 GB used of 2.46 GB. Will this cause hindrance during the install?

Thanks in advance, and I hope I can switch soon! :)

---

### Post by PotatoHead007 on 2014-03-06
hey, do you know about UEFI etc? Might be good to check out a few links:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you do know about changing BIOS settings etc, just change boot order, boot from Ubuntu CD, and choose a full HDD installation.
Not sure what the RECOVERY partition is for, but i think its a windows8 thing(read about it somewhere). Either way, it will not hinder you, as Ubuntu will basically reformat the HDD. Hope i helped :)

---

### Post by Pushkar_Kurhekar on 2014-03-06
Hey, thanks for replying! Yes, I do know about UEFI, and apparently the recovery drive is for Windows only, and it won't cause any hindrance. What I'm looking for, now, however is the way to backup my OEM Windows or grab an ISO from somewhere which will work with my product key. After that, it's all easy.

If someone could help me out with that, it'll be cool.

Thanks!

---

### Post by PotatoHead007 on 2014-03-06
Hi, ok, all good :)
You should be able to login with your Windows 8 account here and download the ISO: [http://www.microsoftstore.com/store/msusa/en_US/pdp/Windows-8.1/productID.288401200?siteID=xIKL5.ppAuE-3G_2ylXTezNMrryTAB_ibA](http://www.microsoftstore.com/store/msusa/en_US/pdp/Windows-8.1/productID.288401200?siteID=xIKL5.ppAuE-3G_2ylXTezNMrryTAB_ibA)
Not sure about this though. I am going to try this, but only in April, when i do a fresh install of 14.04(want Win8 back too because i game alot). Should work though. If not, the people over at MS might help. Maybe :P

**EDIT: **Found this link: [http://www.eightforums.com/tutorials/27129-product-key-find-windows-8-a.html](http://www.eightforums.com/tutorials/27129-product-key-find-windows-8-a.html)
Might help ^^

---

### Post by oldfred on 2014-03-06
I think only your OEM version works with the key installed in the UEFI.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

New installs of Windows have two "recovery" partitions. One smaller one is just the Windows repair and the other is the vendor image of your hard drive. You should back both up, but use the vendor tools to make a DVD set of the vendor image. Some vendors will sell you a copy for a nominal charge, others do not.

If totally reinstalling, you can install in UEFI or BIOS mode. But I would keep gpt partitioning as your Windows version will only work with UEFI and gpt.
Ubuntu will boot from gpt partitioned drives with UEFI if you have the efi partition and with BIOS if you have a bios_grub partition. I would keep efi partition at beginning of drive even if deciding to use BIOS, so you can convert later. Often difficult to add an efi partition near beginning of drive after drive is full and it does not have to be large or about 300MB.

---

### Post by Pushkar_Kurhekar on 2014-03-07
Thanks, but why do I have to keep the gpt partitions? I think I've got a hold of the backup thing, but can't I just format the entire Drive through the Ubuntu installer and install it? And then when I want to go back, I just recover (or use an ISO), put in my product key, and it's done? I assumed it would just go about this way.... I'm a little confused after reading your post.

---

### Post by oldfred on 2014-03-07
You do not have to keep gpt, but Ubuntu works with gpt in BIOS or UEFI boot mode.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

With UEFI, your product key is in UEFI and your Windows is UEFI only which requires gpt partitioning.

---

### Post by Pushkar_Kurhekar on 2014-03-07
I got it now. But when I format it through my CD of Ubuntu 13.10, will it be a gpt partition? And will it be as easy as:

1. Boot through CD
2. Format hard disk
3. Install Ubuntu
4. Install Windows 8 OEM ISO with USB like a normal USB OS Install, enter my product key, etc etc

Hopefully, if that IS all, I'll be glad. I would like to keep UEFI, because if I ever re-install Windows, the ISO will read my OEM: DM and apply the version and stuff accordingly, I've read somewhere.

---

### Post by oldfred on 2014-03-07
If re-installing Windows you would have to do that first. It has several partitions that it needs. 
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)


I always partition in advance, so not sure of installer details now.
But how you boot install media is how it installs. So if you boot in UEFI mode with installer it will install in UEFI mode and UEFI requires gpt. Windows in BIOS mode also requies MBR(msdos) partitioning.
Ubuntu will boot in BIOS or UEFI from gpt partitioned drives, so will install in BIOS mode to a gpt drive, so be sure to boot in UEFI mode to get it to install in UEFI mode.

---

### Post by Pushkar_Kurhekar on 2014-03-07
Yeah. I'm making a recovery disk to restore in case I want to go back. Now, I went on to create a LiveDVD, when I boot from it (Secure boot is off, legacy support is on) it shows some root error of 2 lines, then immediately goes to a DOS-like menu. It's booted in EFI mode, so I know the DVD is okay. So I tried to "Try Ubuntu without changing anything" option, the Ubuntu logo with the dots comes, but then it just goes to a black screen and nothing happens. Even my Disk drive stops reading the DVD. 

What could be the problem? And the worst part of this headache is that all tutorials / Q&A's are for dual-booting, not replacing. My laptop is barely 2 months old, and windows is starting to show its slower side again, even though I have 8 Gigs of RAM....

---

### Post by oldfred on 2014-03-08
What video card/chip?
Often boot parameters are required. And with UEFI boot you have to add them to the grub menu like you would after install on first boot. 

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Ubi_one_2014 on 2014-03-08
> **Pushkar_Kurhekar said:**
> Hey guys. I have an HP Pavilion 15-n013AU, it has come preinstalled with Windows 8, I have upgraded to windows 8.1 through the windows store. Now, I don't really want windows anymore, and I want to switch to Ubuntu 13.10. This is what I basically want to do.

[LIST]
[*]Backup / Get ISO / Install Media of Windows 8, which will be compatible with my OEM serial key.
[*]Delete Windows 8 completely, **no dual-booting,** I want to use my 1TB hard disk to the fullest.
[*]Install Ubuntu 13.10 ( I assume it will be like a normal USB / DVD install after the above has been completed)
[/LIST]

And one important question, what is the Recovery partition in my File Explorer? It says RECOVERY (D:). 2.45 GB used of 2.46 GB. Will this cause hindrance during the install?

Thanks in advance, and I hope I can switch soon! :)

download the ISO.
burn it to a DVD/CD
insert the medium in to pc and restart
do not choose install, but boot from cd/dvd

if everything works, you can start the installation
that's how i did it on dell laptop,came with windows 8

---

