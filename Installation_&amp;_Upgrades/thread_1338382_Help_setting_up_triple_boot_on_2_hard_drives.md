---
title: "Help setting up triple boot on 2 hard drives"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by figosound on 2009-11-26
OK folks, my situation is somewhat tricky, but that's it :D

My PC has 2 hard disks , one 160 Gb with only windows xp, and the other one 80 Gb with 3 partitions: ubuntulinux, swap and windows 7 RC. Primary HD is the 160 Gb one, as set in BIOS (if i don't do anything at startup, the machine search the OS on that HD).

The issue is: the bootloader on primary HD should not be grub, because i've installed it on secondary HD (and it works well!): anyway, no boot take place from primary drive, it only display a black screen with
```
GRUB_
```(of course _ is blinking, but I can only do a CTRL-ALT-DEL)
I can NOT start WinXP now, and this sucks, although I can access my files from ubuntu.

The question is: can I use  GRUB as global boot loader? I mean, can I install GRUB on primary drive and make it recognise my WinXP from primary, my Ubuntu from secondary, and my Win7 from secondary? If so, can you provide me a good guide to do it?

Please help, and possibly be quick [-o<

---

### Post by audiomick on 2009-11-26
Took me less than 2 minutes searching the Ubuntu Documentation to find:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You can use grub as a global boot loader, that is what it is.

Grub was the standard boot loader up to 9.04, 9.10 uses Grub 2 as standard.
Ive read of a few people changing back, but I think you can probably take your pick, and Grub 2 is the newer one.

---

### Post by figosound on 2009-11-26
Off course i can use grub, ok, but i have other issues:
1) I can not make my secondary drive become primary, because the letters windows give to drives depends on it, and Windows XP, which should boot from C:, cannot boot from D: ;
2) I have to replace the boot loader on my primary with something that can run WinXP on C: (primary), and Ubuntu + Win7 on secondary (at this time I have only the secondary boot loader working, allowing me to boot in ubuntu and seven, and I can get to it only by hitting F8 during POST);
3) I have observed that grub did not saw WinXP on the primary, therefore in /boot/grub/grub.cfg there is no mention of it (but seven is there)

Hope I made this more clear, and sorry for my english :-)

PS I write GRUB, but I mean GRUB2, or anything else that can boot my machine;)

---

### Post by audiomick on 2009-11-26
Ok. It is getting a bit out of my depth, but:
As I understand it, if you install Grub onto the front of the disc that the computer boots from, it can then find and boot anything on the computer.
You appear to have a broken grub there, so you have to either fix it, or repair the windows mbr so you can boot xp again. That seems to indicate that if you try installing Grub there, and it doesn't work, you haven't lost anything. You just have to really make sure you know which disc is which, so that you don't accidently mess up the grub on the second disc, in which case you would not be able to boot anything.

---

### Post by figosound on 2009-11-26
I'm going to repair the WinXP boot loader on the primary drive, and then I will post here the new situation...

---

### Post by mrdak on 2009-11-26
Subscribed and waiting...... ;)

---

### Post by figosound on 2009-11-26
Ok, I almost had an heart attack when windows setup started to REINSTALL the system, but the repair worked (no loss of data, luckily - kids, do backups!!), and now i can boot in xp.
The bootloader of XP presents me Teh system itself :-) and an older Ubuntu entry wich leads to an error (HAL.DLL something something - it does not matter, that's not the problem).
Clearly it did not include windows 7 nor ubuntu, which are on the secondary drive...
To start Ubuntu, I have to hit F8 and select the correct drive to boot into, then Grub2 presents me some choices of kernels, and finally a "windows 7"entry, which leads to BLACK SCREEN with tiny cursor blinking...

Here I state that my windows 7 installation was nothing more than an experiment, so I'm not worried if its gone for good, but my original question remains: how can I do to have a bootloader on primary (only WinXP) capable of also booting Ubuntu on secondary (and Win7 optionally)?

---

### Post by darkod on 2009-11-26
OK, I don't have much experience in dual booting two windows versions since when dual booting it was always windows and linux, but in few posts I have seen recommendations that if planning to triple boot, you need to sort out your two windows versions first because it seems windows combines somehow the boot process of 7 and XP, in this case.

So, if Win7 was experimental, and if Ubuntu is still new installation without any IMPORTANT data inside, I would try:
1. Boot with ubuntu cd selecting Try Ubuntu, go into Gparted and delete all the partitions on your second drive, Win7 and Ubuntu. Use Gparted to create one single ntfs partition for Win7 with the size you want for the system partition. Do NOT create any other partitions at this point.
2. Boot with Win7 DVD and install it on the already created partition. It will not ask you to create separate 100MB boot partition in this case, otherwise if you use windows 7 installer to create the system partition it will also create small 100MB partition and waste one primary partition for you.
3. After Win7 is installed, check whether it will combine both 7 and XP in its bootloader. Do not proceed until you have both of them in the windows bootloader and both of them are booting and working fine.
4. If you want another ntfs data partition on the second drive, you can use Win7 and create another ntfs partition with the size you want. Be careful to leave enough unpartitioned space for Ubuntu.
5. After all that is working, boot with Ubuntu CD, select Install Ubuntu, either choose Manual Partitioning or select use lergest continuos free space, etc, any option you feel confident with. I personally always create partitions manually.
6. In the last screen of the install, before clicking Install, click on Advanced. It will show the disk where grub will be installed. You can select yourself whether it will be /dev/sda or /dev/sdb. Be careful, what you call first and second drive is not necessarily A and B for Ubuntu. Select grub2 to be installed on the drive that you wish to boot from. It is your choice which drive will that be. But, I would selectthat drive to be first option in BIOS BEFORE starting to install Win7 and Ubuntu. So which ever drive you choose, adjust the order of the drives in BIOS before installing 7 and ubuntu. It will help with correct boot process.

If you get stuck anywhere along the way, come back. :) And let us know what happened.

---

### Post by darkod on 2009-11-26
> **figosound said:**
> 
The bootloader of XP presents me Teh system itself :-) and an older Ubuntu entry wich leads to an error (HAL.DLL something something - it does not matter, that's not the problem).


Windows bootloader can't "see" linux. How did it manage to have an entry for ubuntu, old or new? Were you trying something like booting Ubuntu from windows bootloader?

---

### Post by figosound on 2009-11-26
> **darkod said:**
> Windows bootloader can't "see" linux. How did it manage to have an entry for ubuntu, old or new? Were you trying something like booting Ubuntu from windows bootloader?

Sorry, I omitted to say that I had a previous wubi installation, which got wasted because of this bug
[https://bugs.launchpad.net/wubi/+bug/477169](https://bugs.launchpad.net/wubi/+bug/477169)

I uninstalled it, but the entry in windowze boot loader remained :mrgreen:.
Anyway, the entry in boot.ini says:
```
C:\wubildr.mbr="Ubuntu"
```

I think i could delete it without any harm... But I don't want to :-\"

Back OT, thank you very much for your help, but for now I'm done with formatting and reinstalling and the like: maybe in a few days I will try to, but for now I'd like to know a way to do what i want that does not involve reinstallations and repartitioning :cool:

---

### Post by darkod on 2009-11-26
As I said, I'm not too experienced in booting two windows versions. The point is after you restored XP MBR on your first drive, it now sees only your XP as expected (plus the remains of the wubi boot). If indeed windows is combining the boot process, that would have been done by windows7 if it was installed after XP. But it would be broken by restoring XP MBR now.
So at this moment we can't even know if 7 and XP would boot fine even without ubuntu and grub. It's not easy to find a solution like that.
You can try setting the second disk as the first choice for boot in BIOS and see what you have as a bootprocess there. At the moment XP just boots straight from first disk.
On the second disk you might have the win7 bootloader with XP inside too, and even grub2 with all of them. :)

PS. Check the files on the win7 partition on your second drive, in the root of the partition (not root of ubuntu). Do you have files/folders like /bootmgr, /boot/bcd, boot.ini, ntldr?

---

### Post by figosound on 2009-11-26
> **darkod said:**
> 
PS. Check the files on the win7 partition on your second drive, in the root of the partition (not root of ubuntu). Do you have files/folders like /bootmgr, /boot/bcd, boot.ini, ntldr?

This is strange... no one of these files/folders are in the Win7 partition, but they are in the WinXP partition... It seems that Win7 placed all his stuff there, and this is correct, as it's the primary drive...

Curse you, NTLDR:lolflag:

Maybe I could make an entry on the WinXP boot loader to launch Win7 - that will be neat!

---

### Post by darkod on 2009-11-26
Like I said, windows somehow combines booting for two versions together. But I'm not sure of the actual rule. You could try adding win7 to XP bootloader but not sure it can cope with that. It should be the other way around, win7 bootloader booting both 7 and XP.

---

### Post by presence1960 on 2009-11-26
before I can suggest anything it would be nice to have a whole lot more info on your setup & boot process. Do this please:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by presence1960 on 2009-11-26
> **figosound said:**
> Sorry, I omitted to say that I had a previous wubi installation, which got wasted because of this bug
[https://bugs.launchpad.net/wubi/+bug/477169](https://bugs.launchpad.net/wubi/+bug/477169)

[B][U]I uninstalled it, but the entry in windowze boot loader remained :mrgreen:.
Anyway, the entry in boot.ini says:
```
C:\wubildr.mbr="Ubuntu"
```

I think i could delete it without any harm... But I don't want to :-\"
[/U][/B]


That is exactly how you get rid of the wubi entry. Why don't you want to get rid of it? You no longer have wubi.

---

### Post by oldfred on 2009-11-27
If you want a review of your boot process post the script presence1960 recommended.

Windows does combine boot files into one so you can boot both. When it does that grub can only boot into the combined windows where you can choose which windows to use. If you want to boot both sepratedly directly from grub their is a work around. Also windows can be on the second drive. Grub will load it and using map or mapdrive commands make windows think it is still the first drive.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

Or as another poster did:
Or do what I did when I installed Win 7. - unplugged the drive with XP during the install.

---

### Post by presence1960 on 2009-11-27
> **oldfred said:**
> If you want a review of your boot process post the script presence1960 recommended.

Windows does combine boot files into one so you can boot both. When it does that grub can only boot into the combined windows where you can choose which windows to use. If you want to boot both sepratedly directly from grub their is a work around. Also windows can be on the second drive. Grub will load it and using map or mapdrive commands make windows think it is still the first drive.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

Or as another poster did:
Or do what I did when I installed Win 7. - unplugged the drive with XP during the install.

oldfred, thanks for the link to multibooters site. I bookmarked it.

---

