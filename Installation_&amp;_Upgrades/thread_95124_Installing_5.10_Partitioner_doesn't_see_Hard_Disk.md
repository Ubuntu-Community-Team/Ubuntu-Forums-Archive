---
title: "Installing 5.10: Partitioner doesn't see Hard Disk"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by nighthawk39 on 2005-11-25
Hello, I'm trying to install Ubuntu Breezy in a dual boot configuration with Windows XP.  However when i get to the stage of installation where it asks me to setup my partitions ("Partition Disks") it doesn't show my hard drive in the list.  Here is what it shows:
> **Partition Disks**

*(description of what the partitioner does)*

Configure software RAID
Configure the Logical Volume Manager
Guided Partitioning
Help on Partitioning


Undo changes to partitions
Finish partitioning and write changes to disk

As you can see no information on my hard drive is displayed.  I tried "Guided Partitioning", then selected "Manually Edit Partition Table" and it brought me back to here.  Any ideas?

> **Partitions as Windows sees them:**

(C) Local Disk 121GB NTFS **Windows XP**
(D) Documents 58.8GB NTFS
(F) Ubuntu 9.7GB FAT32 **Where I want to install Ubuntu**

Hard drive is a Maxtor 200GB Internal Ultra-ATA IDE.

---

### Post by bwog on 2005-11-26
Did you use a windows tool to make these partitions (like Partition Magic)?

The breezy live CD has gparted (dont know about the hoary live CD), can you see the partitions with gparted? Does it give an error message?

Did you verify your install CD?

Is it a secret which hardware you use?

When this problem is resolved and you cannot install properly, you can try to use ext3 instead of fat32.

---

### Post by junamuno on 2005-11-26
I try to run Gparted from my Ubuntu live cd, but it opens the program and then it just keep trying to read the disc and it freezes, basically I need to make a partition of my HD because I want to keep windows (for now only), what could I do????

---

### Post by AgentZ86 on 2005-11-26
When you get to the apart about manually editing partition table, your saying that you do not see any list of your drives ? Please advise?

I had some similar confusion about the install process as I did not like the terminology they were using cause it indicates that I will be erasing everyting or re-writing the partition table and thats not what I wanted to do either.

However after scrolling down to the bottom part of the screen which was not visible at my first attempt I saw a (finish partitioning and write changes to disk.

I selected this and at this point a screen came up with partition settings to select, highlight your partition you wish to change and hit enter,

Then on the next screen there will be 2 main selections to highlight,partition settings, and select mount point. Make it whatever you wish, best to select ext.3 for partition settings and then (use as (/root file system)
Then select Done setting up the partition
Then scroll down to finish
Then write changes - yes
Then install Grub-OK
Install MBR-no (select no if you already have other grub on the MBR and if you just want to install and add a line item to your current grub menu list)
If you don't have grub already then it is ok to (install MBR-Yes)
Then the screen says you have to determine which dive partition to install grub.

Some examples:
(hd0,?) means first primary drive and the ? says which partition, however I don't know why but it's numbers do not actually match the partitions, but this is the way it is.
(hd0,1) means primary 2nd partition, so if your windows is on partition 1 and your ubuntu is on partition 2, then you would enter (hd0,1)for partition 2 with parenthises just like I've writen
There is another way of doing it also using /dev/hda2, which is the same thing as (hd0,1) don't ask me why.
Anyhow if you want ubutu on hda3 or partition 3 then you type (hd0,2) for partition 3, or /dev/hda3

Now if you selected NO for write to MBR , then you would have to enter a line entry in grub menu by adding a line item in a file called - menu.Ist found in the boot directory of your grub loader that you are currently are using.
However if you select Write MBR-Yes, then Ubunto should set this up for you and no other manual entries to boot loader should be neccessary.

If you selected NO and manually selected your partition like it did, then your menu.Ist entry would look like mine shwn in red.

The line items could look something like this:

timeout 15
color cyan/blue white/blue
foreground ffffff
background 0639a1
gfxmenu /boot/grub/message

title MEPIS
kernel (hd0,1)/boot/vmlinuz-2.6.10 root=/dev/hda2 nomce quiet splash=verbose vga=791 
initrd (hd0,1)/boot/initrd.splash 

title WINBLOWS
rootnoverify (hd0,0)
chainloader +1

title PCLinuxOS
rootnoverify (hd0,4) # this is hda4 in GRUB's notation
chainloader +1

title Mandriva
rootnoverify (hd0,5) # this is hda5 in GRUB's notation
chainloader +1

[COLOR="Red"]title UBUNTU
rootnoverify (hd0,6) # this is hda6 in GRUB's notation
chainloader +1[/COLOR]

title MEMTEST
kernel /boot/memtest86.bin


Anyhow hope this helps I'm not sure why you can't get to the screen with your drive, but I believe it has something to do with moving foward in the installation like the part I mentioned about manually edit partition table and scroll down to finish partitioning and write changed to disk, 
I think this is where it realized that no changes were made and takes you to the drive list so that you can make changes etc. Try that and post your results
Print this to help you walk thru it which your installing.

---

### Post by nighthawk39 on 2005-11-26
**Edited my first post so it shows the exact options on the partitioner menu.**

In response to bwog:

Originally I made 2 partitions using the Maxtor Maxblast software that came with the hard drive.  The partitions were approximately 130GB (Windows) and 56GB ("Documents").  I later used Partition Magic (the one that runs without being booted into Windows) to resize the Windows partition to 120GB, and created the 10GB Ubuntu partition.

> The breezy live CD has gparted (dont know about the hoary live CD), can you see the partitions with gparted? Does it give an error message?
I haven't tried that tool, but I will make another reply once I have if the step AgentZ86 mentioned in this thread doesn't work.

> Did you verify your install CD?
Not as of yet, thanks for the tip. ;)  Will post an update once I have.
**Update: Verified the CD and it is fine.**

> Is it a secret which hardware you use?
Umm... I don't think so lol, sorry I didn't mention in the original post.  Here it is:
Power: Enermax 460W
Motherboard: ASUS P5WD2 (LGA 775)
Processor: Pentium D 830 (3.0GHZ, dual-core, 64-bit)
Storage: Maxtor DiamondMax 200GB 7200RPM U-ATA IDE
Network: Onboard Gigabit LAN
Video: HIS Radeon x800 GTO 256MB GDDR3

If you need to know anything else let me know.

> When this problem is resolved and you cannot install properly, you can try to use ext3 instead of fat32.
Ok! :)

In response to AgentZ86:

I tried click the last option (Finish partitioning and write changes to disk) and here is the message I got:

> **[COLOR="Red"]Partition Disks[/COLOR]**

[COLOR="Blue"]No root file system[/COLOR]
No root file system is defined.

Please correct this from the partitioning menu.
So when I click continue it brings me back to the menu.  I am going to try reformatting that partition as ext3 like bwog suggested.

---

### Post by nighthawk39 on 2005-11-26
[QUOTE=bwog]The breezy live CD has gparted (dont know about the hoary live CD), can you see the partitions with gparted? Does it give an error message?[/QUOTE]
I can't run it, it keeps asking for a password even though I never defined one.  It rejects everything I put in.  "sudo gparted" in terminal doesn't work either.

(I have to run the liveCD in expert mode because my video card (x800) isn't fully supported it looks like, because it never starts the X server in normal mode)

---

### Post by bwog on 2005-11-26
Strange, that password for the liveCD, I dont remember that. Ill try it and get back here. 

The radeon card will be recognized after install, you need to install some drivers for that, but there are howtos. (ati finally improved their drivers)

---

### Post by bwog on 2005-11-26
It is as I remembered, there is no password for the live cd, I ran gparted (without changing anything). Obviously you did not set a bios password. 

Partition Magic can give problems, although I have never seen that it prevented seeing the hard disk. Point is that you dont need it, and it may give problems. 

The only thing I can think of right now is removing the fat partition with P.Magic. That wont hurt. Check if the installCD can recognize the disk and make a new ext3 partition on free space with the install CD. 

If that doesnt work perhaps you can try a fresh install of XP without P.Magic. Or can you uninstall P.Magic without running into trouble? That will take time, so in that case perhaps you can wait for better answers first.

There are no exotic controllers in your hardware specs, as far as I can see.

---

### Post by nighthawk39 on 2005-11-26
[QUOTE=bwog]Obviously you did not set a bios password.[/quote]
How is that obvious, and will that affect my installation?

> The only thing I can think of right now is removing the fat partition with P.Magic. That wont hurt. Check if the installCD can recognize the disk and make a new ext3 partition on free space with the install CD.
I removed the FAT32 partition using Partition Magic as you suggested and the Install CD still doesn't show any partition information in the partitioner.

> Or can you uninstall P.Magic without running into trouble?
It runs off the CD, it isn't installed to my hard drive.

I am going to try using Partition Magic right now to create a ext3 partition and see if it sees that.

---

### Post by nighthawk39 on 2005-11-26
Humm after reading this thread ( [http://www.ubuntuforums.org/showthread.php?t=71855&highlight=ite](http://www.ubuntuforums.org/showthread.php?t=71855&highlight=ite) ) I am starting to think my controller isn't supported... (ITE8211).

---

### Post by bwog on 2005-11-26
That would explain it. Bad luck. Possibly someone will make a tutorial to work around this.

**Edit:** However, searching the net for ITE IT8212 ubuntu shows that there are users who installed ubuntu, but just couldnt use raid.

There is also some tech-speak about your motherboard and the driver here: [http://lists.xensource.com/archives/html/xen-users/2005-08/msg00778.html](http://lists.xensource.com/archives/html/xen-users/2005-08/msg00778.html)
So it can be done, but I cant help you with this.

---

### Post by nighthawk39 on 2005-11-26
[QUOTE=bwog]That would explain it. Bad luck. Possibly someone will make a tutorial to work around this.

**Edit:** However, searching the net for ITE IT8212 ubuntu shows that there are users who installed ubuntu, but just couldnt use raid.

There is also some tech-speak about your motherboard and the driver here: [http://lists.xensource.com/archives/html/xen-users/2005-08/msg00778.html](http://lists.xensource.com/archives/html/xen-users/2005-08/msg00778.html)
So it can be done, but I cant help you with this.[/QUOTE]
Thank you for all your help so far! :)  I'll keep working on it.

---

