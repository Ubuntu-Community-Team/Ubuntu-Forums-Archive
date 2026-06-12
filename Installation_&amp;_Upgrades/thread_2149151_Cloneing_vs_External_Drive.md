---
title: "Cloneing vs External Drive"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by GUZZLR on 2013-05-27
Hello All
I have an external 1TB NTFS drive in a case which I seldom use.  I have an HP Widows 7 with a 500GB drive which is about 65% filled.  I was going to clone the old 500GB to the new 1TB drive, install it into the HP. and install Ubuntu 13.04 as a Dual Boot.  
Here's my question: 
1. Instead of all that, why can't I just keep the 1TB as an external (hooked up via eSATA), install 13.04 to the external, therefore keeping my 500GB inside the HP? 
2. Won't Ubuntu recognize the external drive and ask if I want to load the OS on that drive; thereby; running along side Windows in the HP?
3. If this can happen, when I boot the machine, will Ubuntu still ask which OS I want to boot into?

Thanks for the help

---

### Post by ahallubuntu on 2013-05-27
Are you planning to extract the external drive from its case and install it internally?  If not, you won't be able to boot Windows.  You can't run Windows from an external drive.

You CAN run Ubuntu from an external drive, if you wish.

---

### Post by GUZZLR on 2013-05-28
I think you just answered my question.  I wanted  to keep the Windows disk internally, and the Ubuntu disk externally.  when I load the the Ubuntu install disk, will it allow me to load Ubuntu onto the external drive, and keep windows operating as normal interanally?  And, will it give me the option which disk I want to boot to (internal or external) to choose OS.
Thanks

---

### Post by ahallubuntu on 2013-05-28
Yes, you can install Ubuntu on the external drive without disturbing the internal Windows drive.  In fact, you can probably use just a tiny portion of the external drive for Ubuntu - maybe 20GB - and leave the rest as NTFS (or just shrink the existing NTFS partition by 20GB or so using Gparted, then install Ubuntu in the free space.

However, you must be careful: during the installation of Ubuntu, make sure you choose the location of the Grub boot sector as your external drive, not your internal drive!!!!  I  have never installed 13.04, but in 12.04 you can choose the location where Grub's boot sector will be written.  Typically, the internal drive would be /dev/sda and the external drive (with nothing else connected) would be /dev/sdb  but be sure you which is which during the installation so you get it right.

Afterward, to boot Ubuntu, you'll need to use your BIOS boot menu - on a Dell you hit F12 to get a boot menu, not sure what the key is on an HP (sometimes you must also enable that feature in BIOS Setup).  When you choose the external hard drive, you'll get a Grub boot menu but if you choose the internal drive it will boot right to Windows like it does now.  You could also set your BIOS to default to booting from the external drive, I suppose, but it will be easier if you get used to using the BIOS boot menu I think to choose the external drive and boot Ubuntu.

---

### Post by Mark Phelps on 2013-05-28
The SAFEST thing to do in this situation is to have ONLY the external drive connected when you install Ubuntu.  That way, you won't have to worry about accidentally installing GRUB to an internal partition and, quite possibly, hosing up Win7 booting in the process.

---

### Post by sudodus on 2013-05-28
I run Ubuntu from an eSATA drive in a multiboot environment. No problems at all. If I understand it correctly, the computer does not make any difference between a drive that is connected via eSATA and a drive connected via normal SATA (internally). I haven't tried with Windows from eSATA, but [Grenage]("http://ubuntuforums.org/member.php?u=263074") has. See post #17. It works but is not portable. We all know Windows does not run from USB except during installation or as PE (preinstallation environment).

Anyway, I agree with Mark Phelps, install Ubuntu to the eSATA drive and if possible, disconnect the internal drive during the installation. 
Shut down, connect the internal drive, boot and run ```
sudo update-grub
``` which should find Windows and make an entry for it in the grub menu.

---

### Post by GUZZLR on 2013-05-28
> **sudodus said:**
> I run Ubuntu from an eSATA drive in a multiboot environment. No problems at all. If I understand it correctly, the computer does not make any difference between a drive that is connected via eSATA and a drive connected via normal SATA (internally). I haven't tried with Windows from eSATA

So on your set up, running eSATA, when you turn on the machine, Ubuntu ask if you want to boot into Ubuntu or Windows?  I agree the computer should not tell a difference between Internal SATA, or external SATA...they're both the same interface going directly to the mobo.
Thanks

Also, I like the idea of pulling the Windows drive and running directly to eSATA drive.  had not thought of doing that

---

### Post by GUZZLR on 2013-05-28
> **ahallubuntu said:**
> Yes, you can install Ubuntu on the external drive without disturbing the internal Windows drive.  In fact, you can probably use just a tiny portion of the external drive for Ubuntu - maybe 20GB - and leave the rest as NTFS (or just shrink the existing NTFS partition by 20GB or so using Gparted, then install Ubuntu in the free space.

When I install Ubuntu, won't Ubuntu create a small partition just for the OS...I thought it did that  automatically.  Thanks

---

### Post by ahallubuntu on 2013-05-28
> **GUZZLR said:**
> When I install Ubuntu, won't Ubuntu create a small partition just for the OS...I thought it did that  automatically.  Thanks

It's an option during installation, yes, but I wouldn't do the "automatic" option.  Ubuntu may choose to make a larger partition than you need.  Personally, I'd create the space I needed manually and choose manual partitioning.  You really need only two partitions, one for / and one for swap.  You would need to shrink the existing NTFS partition (assuming you keep it) and create the new partitions.  (Shrinking would be quick if the partition is nearly empty now.)  It's fine to create one extended partition and then two logical partitions inside of it - Ubuntu doesn't care if you use primary or logical partitions for the OS.

I missed that it was eSATA - yes, that would work just like an internal SATA drive so you could go with your original option to clone Windows to the external drive and add Ubuntu partitions.  You can clone with Gparted and a live CD if you wish - it works quite well that way, especially if you then install Ubuntu on the same drive and use Grub to choose which OS to boot.

---

### Post by C.S.Cameron on 2013-05-28
Following is step by step for making a Full install of *buntu 12.04 on a USB hard disk drive, installing 13.04 almost the same.
All partitions except / are optional.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.

Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Insert the target USB drive.
Select language
Select install Ubuntu.

Select Download updates while installing and Select Install this third-party software.
Continue

At "Installation type" select "Something else".
Continue

Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Start with an external drive that has been formatted NTFS.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." as large as required.
Location = Beginning.
"Use as:" = "do not use this partition".
Leave "Mount point" blank.
Select "OK"

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 5000+ megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 5000+ megabytes, Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.

Click "Install Now".
Select your location.
Continue.

Select Keyboard layout.
Continue.

Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
Do an sudo update-grub If you want to boot your system from the grub of the external drive, as sudodus noted.

---

### Post by sudodus on 2013-05-29
> **GUZZLR said:**
> So on your set up, running eSATA, when you turn on the machine, Ubuntu ask if you want to boot into Ubuntu or Windows?  I agree the computer should not tell a difference between Internal SATA, or external SATA...they're both the same interface going directly to the mobo.
Thanks

Also, I like the idea of pulling the Windows drive and running directly to eSATA drive.  had not thought of doing that

The grub menu has entries (lines) for Ubuntu, Windows ...

I think the simplest thing for you is to keep the internal drive as it is, if you can change the boot order, so that it boots from the eSATA drive (either via a bios menu or by switching the connections to the mobo). Then you can get a dual boot system without touching the drive with Windows.

---

### Post by C.S.Cameron on 2013-05-29
> **sudodus said:**
> The grub menu has entries (lines) for Ubuntu, Windows ...

I think the simplest thing for you is to keep the internal drive as it is, if you can change the boot order, so that it boots from the eSATA drive (either via a bios menu or by switching the connections to the mobo). Then you can get a dual boot system without touching the drive with Windows.

+1

---

### Post by ubfan1 on 2013-05-29
Another benefit to disabling the hard disk for installing from USB is to workaround bug 384633, grub-install leaves you with a wrong boot device (forgetting the install media will be gone).  Typically, the HDD is sda, the install media is sdb, and the the target USB sdc at install time, and the grub.cfg gets generated with an sdc on the linux boot line (instead of the UUIDs used elsewhere).  After the install media is removed and you try to reboot, the HDD is sda, and the target USB is now sdb, so trying to boot off sdc fails with something like "root not found".  Editing the grub boot command fixes the first boot, and update-grub makes the fix permanent.   Some recent changes in grub-install may now leave the wrong device as sda(!) so avoiding the whole mess by removing the disk seems to be "a really good thing".

---

### Post by GUZZLR on 2013-05-29
```

Do an sudo update-grub If you want to boot your system from the grub of the external drive, as sudodus noted
```

I'm just not sure if I am following you guy's correctly. Upon my last installs (12.10 & Mint14), I  installed Ubuntu/Mint along side Windows, when I boot, the screen gives me the choice of booting into either windows or Linux.  So I want to verify if I am thinking correctly (thanks for everybody's patience).
[LIST=1]
[*]Physically remove my internal Windows 500gb drive from my HP laptop 
[*]load my external 1tb eSATA via my eSATA laptop hookup 
[*]Instll Ubuntu by directing the installer to laod Ubuntu to the external eSATA drive (I will skip the area of manually partitioning and let Ubuntu allow me to use the slider upon intall) 
[*]Turn off the computer and reinstall my original 500gb drive. 
[*]Turn the computer on...This is where I am confused.  If I turn the computer on, won't it boot into Windows as normally?  If so, how do I get to Ubuntu on the exteranl to run "sudo update-grub"? 
[*]And, if I run the update-grub command, will I still have the choice of booting into either Windows or Ubuntu on the external HDD? 
[/LIST]

Thanks for the help

---

### Post by ahallubuntu on 2013-05-29
You can set the boot order of your attached drives in the BIOS (or UEFI), so you could enter the Setup screen before an OS is booted and set the order so that one drive is booted before another.

But most modern computers also allow you to hit a key at boot time and get a "boot menu" of attached drives (plus CD/DVD drive, etc.) to allow you to boot whatever you wish.  That boot menu function varies by make/model of computer; on a Dell it's the F12 key to get a boot menu.

The "update-grub" command will search whatever partitions can be found for bootable operating systems and put them in the Grub menu.  So, if you re-attach your internal drive, boot Ubuntu, and do "update-grub," it should find Windows and allow you the choice to boot that (or Ubuntu) in the future.  But Ubuntu will be the default OS unless you change that.

---

### Post by C.S.Cameron on 2013-05-30
If you set the external drive as first drive in BIOS, rather than pressing F12, it will continue to be the drive that boots and thus the grub that gives the choice of which drive to boot.
Having to press F12 isn't that tough though, if your computer has this option.

---

### Post by Grenage on 2013-05-30
> **ahallubuntu said:**
> Are you planning to extract the external drive from its case and install it internally?  If not, you won't be able to boot Windows.  You can't run Windows from an external drive.

You CAN run Ubuntu from an external drive, if you wish.

What; has something changed? I've run Windows 7 on ESATA...

---

### Post by sudodus on 2013-05-30
> **Grenage said:**
> What; has something changed? I've run Windows 7 on ESATA...

Good piece of knowledge, that Windows runs on eSATA :-)

---

### Post by GUZZLR on 2013-05-30
```
[COLOR=#000000]*Are you planning to extract the external drive from its case and install it internally? If not, you won't be able to boot Windows. You can't run Windows from an external drive.*[/COLOR]
```

No, I'm thinking of keeping the Windows drive installed as is...internally, and running Linux from the external

---

### Post by GUZZLR on 2013-05-30
```
[COLOR=#000000]If you set the external drive as first drive in BIOS, rather than pressing F12, it will continue to be the drive that boots and thus the grub that gives the choice of which drive to boot.[/COLOR]
```
this is an excellent idea.  I think I understand now...GRUB is the purple screen with the two lines of selection for me to select either Ubuntu, or Windows.  So this is what overrides MBR when I install Linux, and this is why I run the update, so GRUB will find Windows on the C:drive after I reinstall the Windows internal drive back inside the machine...I think I  get it now...If this is correct, it makes sense now.

---

### Post by C.S.Cameron on 2013-05-30
> **GUZZLR said:**
> ```
[COLOR=#000000]If you set the external drive as first drive in BIOS, rather than pressing F12, it will continue to be the drive that boots and thus the grub that gives the choice of which drive to boot.[/COLOR]
```
this is an excellent idea.  I think I understand now...GRUB is the purple screen with the two lines of selection for me to select either Ubuntu, or Windows.  So this is what overrides MBR when I install Linux, and this is why I run the update, so GRUB will find Windows on the C:drive after I reinstall the Windows internal drive back inside the machine...I think I  get it now...If this is correct, it makes sense now.

You got it.

---

### Post by GUZZLR on 2013-06-01
Hello, and thanks for the help...
So here's what I did:
[LIST=1]
[*]Power down and remove my internal Windows 7 HDD
[*]Attached my external drive via eSATA
[*]Powered up and ran the Ubuntu installer on the live CD.
[*]The installer recognized the external eSATA drive as any normal drive and proceeded with a normal installation
[/LIST]

Here's where I stopped the install (thumbnail) 
Questions:
[LIST=1]
[*]Why is the drive read as an FAT 16?  When I originally formatted this drive, for my Windows computer, I set it as NTFS, but now it shows as FAT16, How do I get it back to NTFS?  I was under the impression that FAT16 can not handle large amounts of storage, and this is a 1TB drive (the external drive)
[*]Do I choose YES or NO on the partition window?
[/LIST]

The idea here is I will run Linux on the external eSATA, and Windows 7 on the original internal
Ubuntu 13.04 install (1TB 2.5" Seagate external)
Windows 7 Pro (500GB internal)
Computer: HP Pavilion dv6

Thanks

[ATTACH=CONFIG]243393[/ATTACH]

---

### Post by sudodus on 2013-06-01
1000 MB = 1 GB, that's the pendrive. Use the pull down menu at the top right corner of gparted to select another drive (the eSATA drive, that should be bigger).

But don't install Ubuntu into NTFS, it needs a linux file system, I suggest ext4. So you need to edit the partitions on that eSATA drive, either using the installer (at the partitioning page) or separately before installation, using gparted.

---

### Post by sudodus on 2013-06-01
> Do I choose YES or NO on the partition window?

I suggest that you think about the partitioning for a while. What do you want to have on that drive?

- Only Ubuntu, or Ubuntu and some other operating system?
Ubuntu needs at least one root partition and one swap partition.

- Maybe a separate Data partition?

- Maybe a partition for testing operating systems?

- a separate /home partition?

I usually edit the partitions with gparted before starting the installer. Then I select 'Something else' at the partitioning window and select the partition I have prepared for the root partition. The swap partition will be selected automatically.

Finally I check that the boot-loader will go to the right place, to the head of the drive that you are preparing (not to any partition), so for example /dev/sda, if you have removed the internal drive.

---

### Post by GUZZLR on 2013-06-01
Well, my original intention was to have Ubuntu on the external drive and windows on the internal drive; that way, I could use Windows, and slowly begin to ween myself off windows and onto Ubuntu.  Hopefully, at some point, the only reason why I would go to windows is Excel VBA coding, and the use of Visio...along with other software that I would need occasionally (for work) that is not available to me, through Linux (I do not feel comfortable with WINE).  Currently, I am using Ubuntu on an old Dell that I was experimenting with.  I have discovered that the majority of my personal computing can be done with Linux, and a small part on Windows, which I still need for work, when I choose not to bring home my work laptop.

---

### Post by GUZZLR on 2013-06-01
```
1000 MB = 1 GB, that's the pendrive. Use the pull down menu at the top  right corner of gparted to select another drive (the eSATA drive, that  should be bigger).
```
This I will do, If I understand you correctly, I will find in the drop down a drive much much larger.
Also, I'm re-reading what CS Cameron wrote in post #10...I do not understand the meaning of a Home partition?  Why would I use a Home partition?
So, on my previous post, I have the choice of Yes or No because the installer has found the disk to have a "Mounted Partition"  so in the case of CS Cameron, I would choose Yes and have the installer unmount the partition...would you concur? 

Thanks[ATTACH=CONFIG]243410[/ATTACH]

---

### Post by GUZZLR on 2013-06-01
```

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 5000+ megabytes, Beginning, Ext4, and Mount point = "/" then OK.
```

This is confusing to me.  If I only choose 5000mb, will not the rest of the drive be wasted?  If I have 600+gb of documents, pictures, videos, and music, how can it possibly fit on 5gb of space?  This is what I do not understand about using only 5gb out of 1tb of space?   I plan on using the drive as a full install of Linux.  This came from post #10.
Thanks for the help

---

### Post by C.S.Cameron on 2013-06-02
> **GUZZLR said:**
> ```
1000 MB = 1 GB, that's the pendrive. Use the pull down menu at the top  right corner of gparted to select another drive (the eSATA drive, that  should be bigger).
```
This I will do, If I understand you correctly, I will find in the drop down a drive much much larger.
Also, I'm re-reading what CS Cameron wrote in post #10...I do not understand the meaning of a Home partition?  Why would I use a Home partition?
So, on my previous post, I have the choice of Yes or No because the installer has found the disk to have a "Mounted Partition"  so in the case of CS Cameron, I would choose Yes and have the installer unmount the partition...would you concur? 

Thanks[ATTACH=CONFIG]243410[/ATTACH]

I usually restart the computer after using gparted and do not get asked this question, but the correct answer is yes.

---

### Post by C.S.Cameron on 2013-06-02
> **GUZZLR said:**
> ```

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 5000+ megabytes, Beginning, Ext4, and Mount point = "/" then OK.
```

This is confusing to me.  If I only choose 5000mb, will not the rest of the drive be wasted?  If I have 600+gb of documents, pictures, videos, and music, how can it possibly fit on 5gb of space?  This is what I do not understand about using only 5gb out of 1tb of space?   I plan on using the drive as a full install of Linux.  This came from post #10.
Thanks for the help

All the partitions except / are optional. If you make a separate /home then all your photos etc go there, new installed programs end up in /, swap is good if you want the computer to be able to hibernate when not in use, the windows partition is good say if you want to take a bunch of songs or movies over to a friends house who uses Windows. A separate home can be useful when upgrading to a new version of Ubuntu so you don't loose stuff.

For a 1TB drive you might have 500GB NTFS, 100GB /,  390GB /home and 10GB swap.

If you don't need to use your drive on a Windows computer and you plan on rsyncing your old home folder when upgrading, then you might have 990GB / and 10GB swap.

Decide what you need before starting. your picture showed FAT16 but it is better to start with NTFS, but only if you want a windows partition.
5000MB is a minimum size, you can adjust size later with gparted, but that takes time.

---

### Post by sudodus on 2013-06-02
> **C.S.Cameron said:**
> All the partitions except / are optional. If you make a separate /home then all your photos etc go there, new installed programs end up in /, swap is good if you want the computer to be able to hibernate when not in use, the windows partition is good say if you want to take a bunch of songs or movies over to a friends house who uses Windows. A separate home can be useful when upgrading to a new version of Ubuntu so you don't loose stuff.

For a 1TB drive you might have 500GB NTFS, 100GB /,  390GB /home and 10GB swap.

If you don't need to use your drive on a Windows computer and you plan on rsyncing your old home folder when upgrading, then you might have 990GB / and 10GB swap.

Decide what you need before starting. your picture showed FAT16 but it is better to start with NTFS, but only if you want a windows partition.
5000MB is a minimum size, you can adjust size later with gparted, but that takes time.
+1

Just to show, that I have read your questions and C.S.Cameron's replies. (I agree with his advice.)

---

### Post by GUZZLR on 2013-06-02
Well, I don't plan on using windows on the external drive, so how about something like this:
1TB = 6GB/ Beginning EXT 4
989GB/home Beginning EXT 2
5GB Beginning Use As Swap

My thinking here is the Ubuntu OS will go on the 6GB/, all my documents, media, etc...will go in the 989GB/home, and swap is for hibernation.

Am I thinking correctly in that the OS "sees" the home partition, and directs all files there...the "/" is only for housing the OS?

---

### Post by sudodus on 2013-06-02
> **GUZZLR said:**
> Well, I don't plan on using windows on the external drive, so how about something like this:
1TB = 6GB/ Beginning EXT 4
989GB/home Beginning EXT 2
5GB Beginning Use As Swap

My thinking here is the Ubuntu OS will go on the 6GB/, all my documents, media, etc...will go in the 989GB/home, and swap is for hibernation.

Am I thinking correctly in that the OS "sees" the home partition, and directs all files there...the "/" is only for housing the OS?

Yes, but I suggest that you use ext4 also for the /home partition, because it has journaling, which increases the security, a kind of backup to repair damages to the file system.

And I would change the proprotions a little. Increase the root partition to at least 16 GB. Since you have a lot of space I would say 24 GB. This gives you extra space for the /tmp directory for temporary files, that might be big in some cases.

---

### Post by C.S.Cameron on 2013-06-02
> **GUZZLR said:**
> Well, I don't plan on using windows on the external drive, so how about something like this:
1TB = 6GB/ Beginning EXT 4
989GB/home Beginning EXT 2
5GB Beginning Use As Swap

My thinking here is the Ubuntu OS will go on the 6GB/, all my documents, media, etc...will go in the 989GB/home, and swap is for hibernation.

Am I thinking correctly in that the OS "sees" the home partition, and directs all files there...the "/" is only for housing the OS?

/ needs to be large enough for all the programs/apps you plan to install and swap needs to be larger than the amount of RAM on the computer.

Perhaps start with:

/ = 50 to 100GB
Swap = 2 x RAM size
/home = remainder of disk.

You can adjust sizes later using gparted if you need more or less.
1

---

### Post by GUZZLR on 2013-06-02
I believe I understand now...thanks

---

### Post by GUZZLR on 2013-06-02
I still have problems.  When I install to something else, the installer does not give me the option to create a new partition table.  I see 1tb of NTFS.  If I hit the "-" on the installer, it will take away the NTFS partiton and leave me with 1TB of free space.  Is this a good idea?
Thanks

So I tried this again, went into GParted and shrank 932 GB (/dev/sda1) down to about 15GB; however, that left me with an enormous amout of "unallocated" space...so that didn't work. So I cancelled everything.  In GParted, I show:

[ATTACH=CONFIG]243450[/ATTACH]

---

### Post by C.S.Cameron on 2013-06-02
Try clicking the +, (this is add in 12.04), not the -.

---

### Post by GUZZLR on 2013-06-02
But I still have almost the entire 1TB on NTFS, Don't I need to do something about that first?
Thanks

---

### Post by C.S.Cameron on 2013-06-02
NTFS space:
Click "/dev/sda1" and "Change".
Make "Size" =10000MB.
"Use as:" = "do not use this partition".
Select "OK"

Root Partition:
Click "free space" and then "+".
Select "Primary", "New partition size ..." = 50000MB, Beginning, Ext4, and Mount point = "/" then OK.

Home Partition:
Click "free space" and then "+".
Select "Primary", "New partition size ..." = 938000MB, Beginning, Ext2, and Mount point = "/home" then OK.

Swap Space:
Click "free space" and then "+".
Select "Primary", "New partition size ..." = remaining space, = 12000MB, Beginning and "Use as" = "swap area" then OK.

---

### Post by GUZZLR on 2013-06-05
```
NTFS space:
Click "/dev/sda1" and "Change".
Make "Size" =10000MB.
"Use as:" = "do not use this partition".
Select "OK"

Root Partition:
Click "free space" and then "+".
Select "Primary", "New partition size ..." = 50000MB, Beginning, Ext4, and Mount point = "/" then OK.

Home Partition:
Click "free space" and then "+".
Select "Primary", "New partition size ..." = 938000MB, Beginning, Ext2, and Mount point = "/home" then OK.

Swap Space:





Click "free space" and then "+".
Select "Primary", "New partition size ..." = remaining space, = 12000MB, Beginning and "Use as" = "swap area" then OK.
```

So I did all of this and installed.
I could not get 12,000MB of swap area, all that was left was about 2,400MB...so I dont know if that was enough, If not, I suppose I could reload the disk and reinstall again?  Also, I used the home space as you suggested with ext.2, and forgot about Sudodus' suggestion of also using Ext.4 because of Journaling. So I'm thinking I may reinstall it with his suggestion.  I also noticed an Ext.3 with Journaling.
_Questions:_
1. is the swap space large enough?
2. what about reinstalling and also using Ext.4 for the root (as you suggested) and Ext 4 for home...can you have two partitions with the same extension?
3. reinstall using Ext.3 for the root, and Ext.4 for the home (because both of these have journaling)?


[ATTACH=CONFIG]243555[/ATTACH]This is my external drive now, with out the internal reattached...so far, everything seems to be working fine.  What do you-all think?

Thanks for the help

---

### Post by sudodus on 2013-06-06
> **GUZZLR said:**
> _Questions:_
1. is the swap space large enough?
2. what about reinstalling and also using Ext.4 for the root (as you suggested) and Ext 4 for home...can you have two partitions with the same extension?
3. reinstall using Ext.3 for the root, and Ext.4 for the home (because both of these have journaling)?

...so far, everything seems to be working fine.  What do you-all think?

Thanks for the help

1. If you intend to hibernate you need at least as much swap as RAM (in the same units, GiBi-bytes in both cases). Otherwise 2.4 GB is OK.

2&3. Both ext3 and ext4 are excellent file systems, ext4 is newer and somewhat improved. I think it is well debugged by now. You need not reinstall. It should be enough to **[FONT=courier new]rsync -Hav[/FONT]** (the content in) your /home partition to an external drive (when booted from the Ubuntu install drive), reformat the /home partition and **[FONT=courier new]rsync -Hav[/FONT]** all the content back to that /home partition again.

Ext4 is the name of the file system type, not of the partition, and you can have many partitions with the same file system type. The partitions can be identified with the block device, UUID and label. UUID is the most unique and safe way to identify a partition, and it is normally used in **[FONT=courier new]/etc/fstab[/FONT]**

---

### Post by GUZZLR on 2013-06-08
So what I've discovered, and what I definately did not know, is when I'm running Linux on the external, it is also picking up my internal Windows hard drive, which I can get to and edit files.  I was under the impression that I would need to copy all the Windows internal disk files to the Linux external disk, or some type of syncing software.  This is not the case.  
So, I now have 800+GB of space non formated to NTFS, which is probably a very big waste, as I can get to all my files from the internal windows drive.  In reality, as was stated several pages back, I really need only a few GB's of space to house the Linux OS, and all the rest can be formatted NTFS.

Questions:
1. If I format the small NTFS currently, then I would need to use something other than "do not use this partition" what should it be, and should it be at the front, or back?
2. If I go with a 70GB portion for the root, and say about 8GB of SWAP area, what about the home area, I would think this would be small as the majority of my files, videos, pictures, etc...are still stored on the internal Windows drive?

Again, the NTFS part I'm not sure about, If I do have a large area for NTFS, when I boot to Linux, will LInux even "see" the NTFS, and only see the smaller partitions of: root, home, and swap areas?

Thanks for the help

---

### Post by sudodus on 2013-06-08
> **GUZZLR said:**
> So what I've discovered, and what I definately did not know, is when I'm running Linux on the external, it is also picking up my internal Windows hard drive, which I can get to and edit files.  I was under the impression that I would need to copy all the Windows internal disk files to the Linux external disk, or some type of syncing software.  This is not the case.  
So, I now have 800+GB of space non formated to NTFS, which is probably a very big waste, as I can get to all my files from the internal windows drive.  In reality, as was stated several pages back, I really need only a few GB's of space to house the Linux OS, and all the rest can be formatted NTFS.

Questions:
1. If I format the small NTFS currently, then I would need to use something other than "do not use this partition" what should it be, and should it be at the front, or back?

Maybe I don't understand this question. I suggest that you boot from the install CD/DVD/USB drive and use the separate GUI program ***gparted ***to edit your partitions. Ubuntu can use many kinds of partitions, including FAT32 and NTFS of Windows. It makes no big difference where the partitions are situated on the hard drive with two important exceptions.

a. In a really big drive, the boot partition, which is the root partition '/' if there is no separate boot partition, must not be too far back on the drive. But for example 100 GB for Windows in the beginning of the drive is OK, you can boot into Ubuntu on a partition behind that. (You can also boot into Ubuntu on a logical partition inside an extended partition.)

b. If you want to resize a partition, you can only do it by moving the boundary between adjacent partitions. There cannot be holes in a partition.

> 
2. If I go with a 70GB portion for the root, and say about 8GB of SWAP area, what about the home area, I would think this would be small as the majority of my files, videos, pictures, etc...are still stored on the internal Windows drive?

Again, the NTFS part I'm not sure about, If I do have a large area for NTFS, when I boot to Linux, will LInux even "see" the NTFS, and only see the smaller partitions of: root, home, and swap areas?

Thanks for the help

It is a good idea to have multimedia files in a separate ***data*** partition, and put the label ***data*** on it, because it might cause problems for Windows, if you write files from Ubuntu into the system partition of Windows, usually C: The file browsers in Ubuntu and Windows will recognize it using the label, so you will see it as ***'data'***.

To have access from Ubuntu and Windows, ***format the data partition with the NTFS file system***. You should create the partition from Ubuntu, but it is a good idea to make the file system and maintain the file system from Windows.

---

### Post by GUZZLR on 2013-06-08
[ATTACH=CONFIG]243654[/ATTACH][ATTACH=CONFIG]243655[/ATTACH]
So this is a screen shot of the internal Windows drive & the external Linux drive from windows (picture 1).  While in windows, windows apparently only sees the approximate 9gb space (picture 2), and not the rest of the 1tb of space used for Linux.  So, I was under the impression that Windows can only use the NTFS portion of the drive?  And, you're saying that Linux does not care. 
So to get the most use out of so much space, it would seem to me, to have a small amount of area for the Linux OS, and a large amount of area partioned NTFS so I can use the external drive for Linux, and Windows...does that make sense?

This is my understanding, and please correct me if I'm wrong...
1. While booted in Linux
2. I maneuver to the Internal Windows drive from Other Devices
3. I then find my files in the My Documents folder (windows)
4. I proceed to make changes to, lets say a .docx Word file, or I create a new folder inside the Windows My Documents C: drive
5. If I close out of Linux, and boot to Windows, these modifications are shown in C: My Documents
Here's my understanding...
The changes I made to the Word file and/or creation of a new folder are in the Windows C: drive, and have nothing to do with the external Linux drive...Is this correct?  If it is, it would seem to me, that I have a very large portion of wasted space on the external drive, because any file modifications (while maneuvering in C:drive Windows is accessing the C: drive, and not the external drive)?  If this is true.

If this is true, I believe: 
1. I should copy the C:drive image onto the larger 1tb external drive.  
2. Then, replace the older 500gb original HP drive with the new 1tb drive (thus having a new C: drive 1tb instead of 500gb)
3. Then, use the older 500gb as an exteranl drive, and use this older drive to reload the Linux OS, and run Linux as my OS, but have the larger storage available and housed internally in the portable laptop for Windows too, since Windows recognizes NTFS and Linux doesn't care.

Does this make any sense, or am I way off?

Again, thanks for the help

---

### Post by C.S.Cameron on 2013-06-08
The NTFS partition should be the first partition so Windows is not confused.

---

### Post by GUZZLR on 2013-06-08
```
multimedia files in a separate ***data*** partition, and put the label ***data*** on it,
```

How do I put a label on a partition?  is this an option in the drop down menu?
Thanks

---

### Post by sudodus on 2013-06-08
You can use ***gparted*** to do it. It is one of the few rather safe tasks to do with gparted. This program is included in the Ubuntu install disk, and it is easy to install into an installed system.

---

### Post by GUZZLR on 2013-06-08
Actually, I believe I should reload the 13.04 OS on this external drive because I actually loaded a 32bit version I used on an earlier machine.  Hence, the part earlier about putting the 1tb drive into the machine as the replacement C:drive.  If/when I do that, I'll have the 500gb origianl drive. Thoughts about this manuver? 
Thanks

---

### Post by GUZZLR on 2013-06-08
So I'm thinking I need to relabel the /home to /data?  Also, in GParted, it looks like I do this by using the "Swap Off" function?

---

### Post by sudodus on 2013-06-08
No, do not relabel the /home to /data.That will not work. By the way, /home is not a label, it is the directory name where the partition is mounted. /home belongs to Ubuntu and needs a linux file system.

If you want a data partition, let it be separate, and a data partition should have the NTFS file system to be used by both operating systems.

-o-

Swapoff means that you switch off the swapping (temporarily), which might be necessary for some operations.

Can you see where in gparted, that you can set or change the label? Right-click on a partition, and you get a menu ... If you do not use English it might be something else, a translation of label (in Swedish it is etikett). The partition must not be mounted, when you edit it. So unmount if necessary.

'Label' is a simple human readable identification (label or name) attached to a partition.

---

### Post by GUZZLR on 2013-06-08
So I'm still confused about the data partition, because I still can't understand why I need to create another partition (data) to house media, when I can get to all my media inside the C:drive in the internal original drive? It would seem I need:
1. 800 gb of NTFS: /dev/sdb1 (at the beguinning)
2. /dev/sdb2 Ext4 "/" to boot and save apps. (50gb)
3. /dev/sdb3 Ext4 "/home" and only about 100gb (because I don't see anything going on it because all my files are on the internal C:drive
4. /dev/sdb4  Linux-Swap  the remaining space

Also, what about files like excel, word, pdf, powerpoint,etc... would that also reside on the data partiton?  How can all these files reside on the data partiton on the external drive, when they are already on the C: drive internal?  Confusing big time. Sorry

---

### Post by C.S.Cameron on 2013-06-08
You only need to copy files from your internal HDD to your external HDD If you want a backup.
The first partition, (NTFS), is where to put new stuff you want to access when booted from Windows.

Say, a friend just downloaded a bunch of, (Public Domain), movies from Archive.org and you want a few, but he only has Windows.
You can take the drive over to his house and download them to the NTFS partition.
You can then watch them on your computer either with Windows or Ubuntu.

Both Windows and Ubuntu can use a NTFS partition, win-win.

With the partition sizes you propose above, it should be a long time before you need to adjust them.

---

### Post by GUZZLR on 2013-06-08
```
1. 800 gb of NTFS: /dev/sdb1 (at the beginning)
2. /dev/sdb2 Ext4 "/" to boot and save apps. (50gb)
3. /dev/sdb3 Ext4 "/home" and only about 100gb (because I don't see  anything going on it because all my files are on the internal C:drive
4. /dev/sdb4  Linux-Swap  the remaining space

```

So I believe I'm slowly catching on here.  With 800gb NTFS, I could use this drive for my windows backup and easily make a system image of the current 500gb + all my files. then comes the boot area with apps, and the "/home" is if i store any personal files on Ubuntu, like Libre and PDF stored in the Documents Home folder inside Linux only, not in the C:drive Windows.

When I originally installed, I had NTFS set for "do not use", what should it read in the drop down now?
Thanks for the help as this is making sense now.

---

### Post by C.S.Cameron on 2013-06-09
The "do not use" just tells the installer not to format that partition, to leave it NTFS, you can still use it.
/home also stores settings and preferences like wallpaper, internet favorites, wireless settings, cookies, etc.

---

