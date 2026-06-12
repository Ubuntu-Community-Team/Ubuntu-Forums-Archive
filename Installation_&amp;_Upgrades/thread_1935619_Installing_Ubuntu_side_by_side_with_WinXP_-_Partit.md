---
title: "Installing Ubuntu side by side with WinXP - Partition Questions"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by mick_ub_v11 on 2012-03-04
With the help of this forum I successfully loaded Ubuntu onto my Dell desktop and then onto another.  I am now loading Ubuntu 11.10 onto my notebook laptop.  I have it working ok, but I messed up on the optimization where it concerns partitioning, because I really only know enough to be dangerous.

The notebook has no CD-ROM drive, so I created a bootable USB.  Works fine.  My WinXP notebook was originally configured thus:
C:  39.0 GB total; 23.1 GB Free
D:  106 GB Total; 105 GB Free
991.8 MB RAM


I believe that it must be one physical disk drive with two logical drives (C: & D: ).  So I figured I would allocate 90 GB on D: to Ubuntu, leaving the remaining 15 GB to WinXP.

During my first install pass, when it came to the easy slider where you could slide the middle bar left or right to give Ubuntu more or less disk/partition space, I (sorrowfully, now) thought I would be better off making sure I used only the D: disk for the 90 GB that I wanted for Ubuntu, so I took a different route whereby I believe I got specific in designating EXT4 for the 90 GB for Ubuntu onto the D: drive (EXT4 sounded familiar from my previous computer installs).

Then there was the install, which all went just fine.  Ubuntu works.  WinXP still works.  However Ubuntu only had (first install) about 22 GB allocated to it.  There was indeed an EXT4 partition with 90 GB, which I can see, but I cannot access.

I did two more passes at delete and re-install Ubuntu from the USB drive, thinking I might get another crack at that slider choice where you get to slide the bar back and forth to allocate partition size to Ubuntu.  No such luck, of course.  It was a one-time opportunity.  However, with each additional re-install, a new "swap area" partition gets created which leaves the partition available to Ubuntu smaller by the amount of each new swap area partition (about 1 GB).


I created a spreadsheet (pasted below) to show the choices that are available to me when I try yet another re-install and opt for the bottom "Something else" choice to re-size partitions yourself.  Hopefully it's readable and you already know what it should say.

I'm also attaching two PDF's: One of the Ubuntu disk status  spreadsheet and the Second of the WinXP disk staus screenshot.

I realize that this should be simple enough and that I should already have RTFM, but I would nonetheless appreciate at least being pointed in the right direction to recover all this seemingly lost disk/partition space for Ubuntu.

I also realize I could forego all this trouble and just make the entire notebook Ubuntu, but first I want to just get this fixed.

Thanks much,

Mick 


Installation Type						
Device	Type	Mount Point	Format?	Size	Used	(Top Bar)
/dev/sda						
/dev/sda1	FAT32			4194 MB	2922 MB	Green 4.2 GB
/dev/sda2	NTFS			41948 MB	17071 MB	Orange 41.9 GB
/dev/sda3	EXT4			90000 MB	1605 MB	Blue 90.0 GB
/dev/sda7	EXT4			20712 MB	3522 MB	Green 20.7 GB
/dev/sda8	swap			1060 MB	0 MB	Orange 1.1 GB  (linux-swap)
/dev/sda6	swap			1058 MB	0 MB	Blue 1.1 GB  (linux-swap)
/dev/sda5	swap			1060 MB	0 MB	Green 1.1 GB  (linux-swap)
						
						
Device for boot loader installation:						
/dev/sda  ATA WDC WD1600BEVT-7  (160.0 GB)						
						
						
Edit a Partition:						
Use as:	EXT4 Journaling File System					
	EXT3 Journaling File System					
	EXT2 File System					
	ReiserFS Journaling File System					
	btrfs Journaling File System					
	JFS Journaling File System					
	XFS Journaling File System					
	FAT16 File System					
	FAT32 File System					
	swap area					
	do not use this partition					
						
						
Mount Point:						
	/					
	/boot					
	/home					
	/tmp					
	/usr					
	/var					
	/srv					
	/opt					
	/usr/local

---

### Post by darkod on 2012-03-04
OK, first of all, hit Pause a little. :) Take a breath... And stop doing new installs since as you saw, it creates new partitions every time.

Question 1: Do you still want to have a 15GB ntfs partition for XP (ubuntu can also read/write on it)?

---

### Post by darkod on 2012-03-04
Lets go on...

Start a new install with the Something Else option (manual partitioning=better control).

Starting bottom to top, start deleting all partitions sda3 to sda8. MAKE SURE you DO NOT touch sda1 or sda2!!!!

After you have deleted sda3 to sda8, all that space will be one big unallocated space, not belonging to any partition.
Now... If you decided to have a 15GB ntfs partition, create it now into that unallocated space. Make it primary, 15GB ntfs.

After that, continue to create into the rest of the unallocated space:
root partition (main system part.), size 15GB, filesystem ext4, logical, mount point /
swap partition, size 2GB, filesystem swap area, logical, doesn't use mount point
/home partition, size all the rest, filesystem ext4, logical, mount point /home

For the bootloader drop-down choice, leave it as /dev/sda.

Having separate /home helps you in future clean installs. Right now you might not know what this means, but soon it will be clear. It's better to create it now.

That should be it more or less. Any questions feel free to ask.

---

### Post by mick_ub_v11 on 2012-03-04
I don't really care about the 15 GB for WinXP.  It seemed like a good idea at the time.  It actually isn't necessary.  If it simplifies the resolution, then let's do without it.
 - Mick

---

### Post by darkod on 2012-03-04
> **mick_ub_v11 said:**
> I don't really care about the 15 GB for WinXP.  It seemed like a good idea at the time.  It actually isn't necessary.  If it simplifies the resolution, then let's do without it.
 - Mick

I already made another post with more instructions. I wanted the first to be short in case you keep trying. :)

Creating the 15GB ntfs has nothing to do with ubuntu. It doesn't make it more complicated, or easy.

Simply create it if you want, or not. You are probably aware that XP will not be able to read the linux partitions and use the data, so if you feel you need little bit more space, you can create one more ntfs partition. 90GB is plenty for ubuntu anyway.

The choice is entirely yours.

---

### Post by mick_ub_v11 on 2012-03-04
OK, I deleted all but sda1 and sda2.
I'm not going to bother with the 15 GB for WinXP.
That leaves 113898 MB for Ubuntu.
I have 5 button choices: New Partition Table; Add; Change; Delete; Revert.
I'm assuming I use Add to create the Swap Partition and the /home partition.  The /home looks right, but I'm not seeing how the swap partition is specified.
Thanks so far,
 - Mick

---

### Post by darkod on 2012-03-04
Yeah, you use Add for creating new partitions.

I guess you are creating all of them as logical partitions. For swap simply select logical, the size, and select swap area in mount point or filesystem type (don't remember right now where exactly was it). But you only need to select it in one spot, and the other option will get greyed out.
I think it was filesystem type where you needed to select swap area.

EDIT: Not sure if we understand each other, you also need a root partition (mount point / ). That is the main system partition, as I said above. The separate /home is optional but recommended. / is not optional, you have to have it.

---

### Post by mick_ub_v11 on 2012-03-04
OK, under "Add" I see the "swap area" choice.
As to "Location for the new partition:"  I'm assuming "End" for swap area, only because that is where it appeared to be placed by the previous installs, and also Beginning for /home.
 - Mick

---

### Post by mick_ub_v11 on 2012-03-04
OK, just to be clear:
as to the Root partition:  this will be:
Logical or Primary?
I'll make this 90GB
Location: Beginning ??
Use as:  EXT4 JFS ?
Mount Point:  /

Thanks, Mick

---

### Post by mick_ub_v11 on 2012-03-04
OK, Sorry, I'm just getting the Root partition bit from your original reply above.  I got confused with BOTH the WinXP NTFS and the root partition being the same 15GB, I first read that as the root partition WAS the WinXP NTFS partition.  Got it now.

---

### Post by darkod on 2012-03-04
> **mick_ub_v11 said:**
> OK, Sorry, I'm just getting the Root partition bit from your original reply above.  I got confused with BOTH the WinXP NTFS and the root partition being the same 15GB, I first read that as the root partition WAS the WinXP NTFS partition.  Got it now.

We try to be clear but we don't always succeed. :)

It seems you got it going.

As for the Beginning or End choice when creating partitions, I haven't gone into a deep study what is best. I usually create them at Beginning which means one by one. The Beginning or End refers to the unpartitioned space where you are creating the partition, whether to be at the end of it, or the beginning.

---

### Post by mick_ub_v11 on 2012-03-04
OK, Ubuntu install in progress:
/ root partition is 15 GB;
/home partition is about 95 GB;
swap area is 2 GB.
I'll post the results when done
 - Mick

---

### Post by mick_ub_v11 on 2012-03-04
OK.
Ubuntu installed with 110.1 GB.

Hat is off to Darko D!!!

 - Mick

---

### Post by darkod on 2012-03-04
Glad you got it going. Enjoy it now.

Just a note for the future: If you ever need to make a clean install overwriting the same root partition, don't forget that by having separate /home partition you can keep all the data there intact. Investigate how to reinstall with separate /home and how to keep the data.

---

### Post by mick_ub_v11 on 2012-03-04
Thanks again, Darko D.

 - Mickie B. himself.

---

