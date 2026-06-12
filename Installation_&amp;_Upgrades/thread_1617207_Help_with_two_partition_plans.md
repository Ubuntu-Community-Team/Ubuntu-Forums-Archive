---
title: "Help with two partition plans"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by zhaotianwu on 2010-11-09
I want to reload windows xp + Ubuntu from scratch, I have no experience with dual-boot installation so any advice or tips would be greatly appreciated.

Now we start with a blank 250GB harddrive in my Samsung N310 netbook, and then,
Plan 1: 
partition the whole 250GB harddrive into 2 logical disk, namely drive c: and d:, both of them are NTFS, and then format them ==> install windows xp to Drive C: ==> boot from USB drive and run Ubuntu USB installer, and [COLOR=Red]let the installer do its partition for Linux's EXT3[/COLOR]

Plan2:
partition the whole 250GB harddrive into [COLOR=Red]3[/COLOR] logical disk, namely drive c:, d: and [COLOR=Red]e:[/COLOR], with drive c: and d: being NTFS while drive e: being [COLOR=Red]EXT3[/COLOR] ==> install windows xp to Drive c: ==> install Ubuntu directly to drive E:


The bottom line here is that 1) there must be 2 logical drives (both are NTFS) for windows xp; 2) I want a EXT3 partition where Ubuntu resides. Can any expert kindly advise me which plan mentioned above is more viable or feasible? Thanks a lot.

---

### Post by Quackers on 2010-11-09
What I would suggest is making 2 partitions formatted in NTFS for your Windows system and leave unallocated space for Ubuntu to install itself in.
Once Windows is installed and running you can then boot from the Ubuntu Live cd/usb and at the partitioning phase in the installer select the manual partitioning option. You can then choose to install Ubuntu in the unallocated space.

---

### Post by dino99 on 2010-11-09
plan 3:

install xp on c: , dont format the free space

let the ubuntu installer install ubuntu on the free space: 3partitions: / (root, bootable, ~ 12Gb, ext4), swap ~ 2Gb, /home (ext3 or ext4, all the space you need), grub2 installed to boot both ubuntu & xp

*** you can prepare your disk with partedmagic ( c + 3 ubuntu partitions) then install ubuntu with the "alternate" iso on the prepared / (you need to take note of its name when formatting, like /dev/sd?)

---

### Post by zhaotianwu on 2010-11-09
> **dino99 said:**
> plan 3:

install xp on c: , dont format the free space

let the ubuntu installer install ubuntu on the free space: 3partitions: / (root, bootable, ~ 12Gb, ext4), swap ~ 2Gb, /home (ext3 or ext4, all the space you need), grub2 installed to boot both ubuntu & xp

*** you can prepare your disk with partedmagic ( c + 3 ubuntu partitions) then install ubuntu with the "alternate" iso on the prepared / (you need to take note of its name when formatting, like /dev/sd?)


Hi dino99,
Thank you very much for your professional-grade advice, I have three follow-up questions here:

1. Regarding the 3 partitions, namely /root, swap and /home, do I need to do it manually with ubuntu installer? Or does it require a third party application like partitionmagic? Is it very easy to go wrong? I'm just a newbie.

2. You mentioned "alternate" iso, what is it? I'm currently expecting to use ubuntu-10.10-netbook-i386.iso for my netbook, is it the right choice to install? What's the fundamental difference between different .iso files?

3. I don't quite understand your last sentence("**you need to take note of its name when formatting, like /dev/sd?"**). What does it mean? Could you please explain a bit in plain language?


Thank you very much!

---

### Post by ImaLamer on 2010-11-09
Let me give you a much simpler approach - something that can be done with just the installation media you have at hand...

Boot your Windows install CD and use their tool to create your first partition, whatever size you'd like Windows to be (1/3rd to 1/2 the drive?). This will be the first primary partition, Windows loves that. What you can't control at this point is that Windows 7 will create a second partition just before it called "System Reserved". It will be 100mb and hold the boot information for Windows. Ignore it, it's fine where it is and can be changed later from Windows/install DVD if desired. This is easy, though at the same time advanced.

Once you have Windows booting and installed proceed to installing Ubuntu from the Live CD...

When given the opportunity to setup the drive I'd suggest doing the following/creating the following partitions:

```
1 EXT3 partition for / (root directory, will hold boot files and your program installs).
1 EXT3 partition for /home (your user files).
```

Leave room to later create a swap partition should you need it - though most systems today rarely use it (how much memory do you have, if less than 4gb, then it is advised).

The home directory and root directory sizes: Keep in mind that the goal here is to keep your home directory separate in the case of a crash, for backup reasons or simply for upgrading later. This will hold your documents and personalized settings, and should be large enough for such. If you download a lot of video, keep this in mind - because everything will be downloaded here first (by default in 90% of the programs you will use) even if you plan to move files later to another drive or partition. It would maybe be advised to split the drive three ways, one third for Windows, one third for the / directory and a third for /home.

If you think you'll need a swap partition then leave a little bit of room (equal to the amount of RAM) at the end of the disk. At this point you've got really 4 primary partitions:

```
System Reserved - Created by Windows, largely invisible under Windows - 100mb
C:\ - Created by Windows install, of course your Windows home - ~80GB
/ - Created by Ubuntu install, holds most of your filesystem - ~80GB
/home - created by Ubuntu install, holds your personal files and settings. - ~80GB
```

If you want to add a swap partition later, simply fire up Gparted once you've got Ubuntu running and create a **logical / extended** partition container and then partition using "Linux Swap" as the partition type. This can be then added to the FSTAB file (text file which controls Ubuntu's mounting of drives) and once added will be used (guides abound on adding a swap partition, let me know if you want links to one).

**EDIT**: Let me add this note; you can only have 4 primary partitions on a drive. Windows will use two right away without major wrangling on your part. So you must plan for this, you can not have System Reserved, C:\, and three more Ubuntu-type partitions unless one of them is in Logical space. I would not recommend putting /, /boot, or /home in a logical partition.

Also note, you can install Windows, let it create the "System Reserved" partition, then use the Ubuntu live CD (Gparted) to delete it, then resize the Windows partition to fill that space - though you will be left with a Windows install that can not boot. This can be fixed by then going into the Windows install DVD and selecting the repair option and then restoring the boot loader as in this guide;

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD") 

So in this method:

* Install Windows
* Test that it boots
* Kill the System Reserved partition from Ubuntu LiveCD
* Resize Windows partition to recover lost space
* Fix the Windows boot loader per the tips above (though Startup Repair may do it for you!)
* Boot Windows - to test
* Proceed to install Ubuntu, let Grub install to MBR of drive, it will boot Windows as long as it booted above
* Enjoy dual boot :)

---

### Post by gordintoronto on 2010-11-09
Mr. Zhao, "C:" and "D:" are Windows terms. Ubuntu has different terms, such as /dev/sda1

I would install Windows but leave free space, then during the Ubuntu install create an Extended partition using the entire free space, and within that three logical partitions, root, swap and home. It is a little bit tricky, you just have to pay attention to what is on the screen.

---

### Post by zhaotianwu on 2010-11-09
Thank you. And what is the difference between /root and /boot? I've read both but never clear about this.

---

### Post by dino99 on 2010-11-10
never said /root, said:   / (which is root ...) not the same :(

---

### Post by gordintoronto on 2010-11-11
I have no idea what /boot is. There is no such partition or file on any of my computers.

---

