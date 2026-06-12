---
title: "Multiboot troubles, incl. what's GRUB?"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Croow on 2008-06-28
Hi, I'm new to linux and I hope you can help. (actual questions are posted at the end).

Over the past years I've been multibooting WinOSs by using the BIOS boot menu. Most recently I've been using XP and Vista (each installed on its own hd). This all works great because each OS thinks it's the only OS installed so there's no trouble when I swap drives in and out.

Enter Ubuntu.
I added a third hd into the mix and installed ubuntu onto it and things look great, except the XP disk, which will no longer boot. Having read some posts on this seeming common topic, I've included the 
"sudo fdisk -lu" output below.


```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc321e5da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625121279   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6e1678e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2f374192

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   378635984   189317961   83  Linux
/dev/sdc2       378635985   390716864     6040440    5  Extended
/dev/sdc5       378636048   390716864     6040408+  82  Linux swap / Solaris

```

Where,
Disk /dev/sda: 320.0 GB  (WinXP SATA AHCI)
Disk /dev/sdb: 500.1 GB  (Vista SATA AHCI)
Disk /dev/sdc: 200.0 GB  (Ubuntu IDE)

From the BIOS boot menu, choosing the XP disk produces the GRUB 1.5 menu followed by an Error 21. A second GRUB screen listing five Ubuntu options comes next and each gives an Error 17.

From the BIOS boot menu, choosing the Vista disk everything works great (well, vista-style great).

From the BIOS boot menu, choosing the Ubuntu disk everything works too.

My motherboard is a Gigabyte GA-P35-DS3R, and I think any IDE disk will always register after a SATA disk with AHCI on, so moving cables isn't an option.
I would prefer to have each OS installed on its own disk independent of the other disks (that is, disk Y doesn't need the bootloader from disk X).

What's GRUB, and do I really need it?
How do I get my first HD (the XP disk) to boot again?
Does linux even support this style of multibooting?


Thanks for reading this far and if you have any suggestions please consider that I know very little about linux.

---

### Post by Pumalite on 2008-06-28
Go into BIOS and make the Ubuntu drive (IDE) the first drive in the boot order, then edit menu.lst and include XP and Vista.

---

### Post by Croow on 2008-06-28
Thanks for the quick reply, which brings up some additional questions.

What's GRUB, and do I really need it?
How do I get my first HD (the XP disk) to boot again?
Does linux even support this style of multibooting?

Since you mentioned "menu.lst" does that mean multibooting isn't possible without GRUB?

If I remove the Ubuntu drive from the computer my XP disk still won't boot because the Ubuntu install changed it somehow. I don't see how changing menu.lst (residing on a disk not connected to the computer) will allow XP to boot again.

Are you saying that Ubuntu can only multiboot with the aid of a software bootloader?

---

### Post by Pumalite on 2008-06-28
[http://www.goodells.net/multiboot/](http://www.goodells.net/multiboot/)

---

### Post by lisati on 2008-06-28
Grub is *one* tool to help with the boot process, including multi-booting. It uses a "menu.lst" file to help it figure out (amongst other things)what OSes you have on your system. As far as I know, it can handle different OSes on different drives, but I have no personal experience of that kind of setup to draw on.

---

### Post by Miljet on 2008-06-28
I think I understand what you want to do and it should be possible. I think that GRUB (GRand Unified Boot manager) installed itself into the mbr (master boot record) of your XP drive. You should be able to use your XP recovery disk to repair it. Just use "fixmember." If you don't have a recovery disk for XP, it can be done from within Ubuntu. Just do a forum search for "fixmember."

---

### Post by Pumalite on 2008-06-28
If you just want to fix your Windows MBR; use your installation disk:
Hit 'r' for Recovery>FIXMBR>FIXBOOT
Or, use Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by Croow on 2008-06-28
Thanks everyone. I've gotten things working (mostly).

So, I used the XP install disk to repair the XP drive. At this point the two WinOSs were working fine, but the Ubuntu wouldn't boot, giving an error like,"Failure to load operating system," or something like that.

Using the Super Grub Disk to boot up from I was able start up the Ubuntu disk. Then I tried to repair the Ubuntu installation to not need the SGD while starting up. Not knowing precisely what I was doing I managed to again wipe out the XP MBR. Curses!

I re-repaired XP via the recovery console then disconnected the two Win HDs (by pulling the cables off), with the Ubuntu as the only drive remaining. Next I retried repairing Ubuntu with SGD, which combined with some edits to menu.lst, has fixed just about everything.

So each of the Windows disks boots just fine regardless of any other disks installed. Ubuntu boots via Grub, which now lists options for 1,2, or 3 disk configurations.

I'm sure there are easier ways to do all of this, but maybe this tale of woe can help someone else with their troubles.

Thanks all

---

### Post by squir on 2008-08-04
I hope it is okay to continue in this thread.  My problem is similar but as a newbie I'm not sure the same answers apply.
I have 2 SATA 150GB HD.  I divided them into partitions 40/40/10/30/30 and formatted to NTFS.  I put WinXP on C on first HD with only first HD connected.  Then disconnected HD and connected 2nd HD installing Vista enterprise on C.  Next connected both HD and tried installing ubuntu 8.04.  I had to install manually to get it to install on Disk 2 on last partition but instructed to put swap on first HD on partition with only 10GB.  I requested ext 3 journaling file system and put mount point /

When it finished installing it notified “unable to install GRUB in (hd0). Executing grub-install (hd0) failed.  This is a fatal error.  Internal error. Failed to initialize HAL.”  Now the swap partition is hidden. 

Now it boots directly to winxp without asking.  
1-	Please tell me if there is a way to correct the GRUB and how to do it in detail. 
2-	If I must I will reinstall vista and try again with ubuntu but how can I get the swap partition back that it setup and hidden. Should I use partition magic to get back the hidden partition?  How do I let GRUB install to MBR. Can I use something like Super GRUB? [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
3-	Please be as specific as possible for a newbie.
Please help!

---

### Post by squir on 2008-08-04
> **squir said:**
> I hope it is okay to continue in this thread.  My problem is similar but as a newbie I'm not sure the same answers apply.
I have 2 SATA 150GB HD.  I divided them into partitions 40/40/10/30/30 and formatted to NTFS.  I put WinXP on C on first HD with only first HD connected.  Then disconnected HD and connected 2nd HD installing Vista enterprise on C.  Next connected both HD and tried installing ubuntu 8.04.  I had to install manually to get it to install on Disk 2 on last partition but instructed to put swap on first HD on partition with only 10GB.  I requested ext 3 journaling file system and put mount point /

When it finished installing it notified “unable to install GRUB in (hd0). Executing grub-install (hd0) failed.  This is a fatal error.  Internal error. Failed to initialize HAL.”  Now the swap partition is hidden. 

Now it boots directly to winxp without asking.  
1-	Please tell me if there is a way to correct the GRUB and how to do it in detail. 
2-	If I must I will reinstall vista and try again with ubuntu but how can I get the swap partition back that it setup and hidden. Should I use partition magic to get back the hidden partition?  How do I let GRUB install to MBR. Can I use something like Super GRUB? [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
3-	Please be as specific as possible for a newbie.
Please help!
This is basically a continuation of my previous postIf I unhide the swap partition on the first HD (with winXP installed)how can I tell ubuntu to make a new swap partition on the HD that has ubuntu installed.  Would it be better to just reformat the 2nd HD and start over.  Can I just reformat the disk or do I need to uninstall ubuntu first? Thanks for being patient.

---

### Post by prabhakaran1989 on 2008-08-04
Have u solved the problem?

if u have not solved try this..place the ubuntu drive in PRIMARY MASTER ?SLAVE ...then try editing the menu.lst...

Another Best way is connect all the Hard disk d try installing UBUNTU 8.04
U will not have any problem in booting of windows!! i have the same problem d resolved by the last method!

---

### Post by squir on 2008-08-06
When connected separately winXP works and vista works.  I've reformatted the LINUX swap file on the winXP HD.  My question is can I just try to reinstall ubuntu over the old unsuccessful install or must I do something else first?

---

### Post by Pumalite on 2008-08-06
Install; go Manual and use the old partitions. You can ignore /swap

---

### Post by squir on 2008-08-07
Please help:  I have 2 SATA HD.
With only one HD connected I installed winXP PRO shown here as sdb1
With only the 2nd HD connected I installed vista enterprises shown here as sda1
Then I connected both and tried installing ubuntu 8.04
I did a manual install choosing sda8 for ext3 journaling file system and marked format
Choose / as mount
Choose sda6 as swap
Then I apparently made a mistake letting the default choose of hd0 for GRUB
I was told ubuntu would setup a boot menu for all 3 system automatically
Now I want to reinstall ubuntu but after I choose ext3, mount and swap it complained no root file system is defined.
Please tell me what to do now.
                           Mount	  size	used
                           point
/dev/sda
/dev/sda1 NTFS  			41947MB 14200MB
	/dev/sda5 NTFS			41932MB	7300MB
	/dev/sda6 swap			10487MB	0MB
	/dev/sda7			31461MB	unknown
	/dev/sda8 ext3		/	34208MB	2700MB
/dev/sdb
	/dev/sdb1 NTFS			41940MB	13700MB
	/dev/sdb5 NTFS			41940MB	40800MB
	/dev/sdb6 FAT32			10487MB	33MB
/dev/sbd7 NTFS			        31453MB	8100MB
/dev/sdb8 				34208MB	unknown	
Freespace				8MB
Thanks

---

### Post by squir on 2008-08-07
I was able to reinstall directly from the ubuntu desktop but it did not give me the option to choose where to install GRUB and I got the same result: unable to install GRUB in (hd0)
Executing "grub-install (hd0)" failed
This is a fatal error
how can I correct this or get back to the GRUB options during installation
Thanks once again

---

### Post by Pumalite on 2008-08-07
Option is in Advanced Tab, step 7 I think. Fix your Windows MBR with your installation disk or Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Search this Forum for:
Dualboot Two Hard Drives

---

### Post by squir on 2008-08-11
I've made some progress and this is where I'm at:
What I want to do is get a **bootmenu that lists my 3 OS**: winXP, Vista and Ubuntu.  I understand that installing ubuntu last will setup the bootmenu on it’s own, but it didn’t for me.  Please help me get this menu
I have 2 SATA HD.
With only one HD connected I installed winXP PRO shown here as sdb1
With only the 2nd HD connected I installed vista enterprises shown here as sda1
Then I connected both and tried installing ubuntu 8.04
I did a manual install choosing sda8 for ext3 journaling file system and marked format
Choose / as mount
Choose sda6 as swap
Then I apparently made a mistake letting the default choose of hd0 for GRUB
Result: unable to install GRUB in (hd0)
Executing "grub-install (hd0)" failed
This is a fatal error
Tried reinstalling with grub on same partition as ubuntu /dev/sda8 with same “unsuccessful result
If I disconnect the ubuntu HD winXP comes up, with both connected vista comes up.  If I physical connect the two HD in opposite order will that help.
Please tell me what to do now.
Mount		size		used
point
/dev/sda
/dev/sda1 NTFS  			41947MB 	14200MB
	/dev/sda5 NTFS			41932MB	7300MB
	/dev/sda6 swap			10487MB	0MB
	/dev/sda7				31461MB	unknown
	/dev/sda8 ext3		/		34208MB	2700MB
/dev/sdb
	/dev/sdb1 NTFS			41940MB	13700MB
	/dev/sdb5 NTFS			41940MB	40800MB
	/dev/sdb6 FAT32			10487MB	33MB
/dev/sbd7 NTFS			31453MB	8100MB
/dev/sdb8 				34208MB	unknown	
Freespace				8MB

I’ve now tried the Super GRUB disk but unsuccessfully although I’ve downloaded the Illustrated Dual Boot SGD page.  The last attempt said, “GRUB loading stage 2,configfile (fd0)/boot/sgd/menu.lst”
1.	I still do NOT get a bootmenu that I want (with the 3 OS listed).  I was thinking of trying the GNU/LINUX or FIX BOOT OF GNU LINUX but it says its for single HD.  With everything connected it goes automatically into Vista at present.
2.	Should the bootmenu come up everytime or will I need to use the SGD floppy diskette everytime?  
3.	If I try reinstalling ubuntu could someone tell me what settings to choose to correctly install the GRUB?
I find it very confusing and don’t want to have to reinstall the 3 systems.
4.      Someone suggested I physically put the ubuntu disk first and then edit the menu.lst.  Could someone tell me with the above config what exactly how to edit the menu.lst, that is what to type.
Thanks

---

