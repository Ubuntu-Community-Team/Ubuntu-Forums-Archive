---
title: "duel booted with ubuntu and windows 7, but windows 7 wont boot?"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by jonathandawdy on 2012-11-04
I recently duel booted with Ubuntu and windows 7. When i did i opend my windows 7 files drive and moved over some files. Now i did this for a week and then one day when i tried to open the partition it didnt mount the volume. Ubuntu says that the partition in allocated and is 391 gigs in size but it says its type is unknown and it should say NTFS.

-How do i fix this?
-How do i set the drive type without formatting it?

Other things you may want to know
-I already tried RIP and it says it cant open or effect a drive un till its type is configured.
-If it matters the windows 7 boot-loader is on a different partition(company decision don't ask me y)
-ALSO WINDOWS 7 DON'T WORK I WILL ADD THE LINK TO THAT THREAD AFTER I MAKE IT.

---

### Post by jonathandawdy on 2012-11-04
I have successfully duel booted Ubuntu on my windows 7 computer. But after i did this the windows 7 boot wont work it comes up with an error saying that the windows 7 boot-loader drive could be inaccessible.

Things you may wont to know.
-windows 7 on my computer has 2 partitions unusually one is 213(MB) drive with 180.2(MB) free. This is the windows 7 boot-loader. The other drive is a 391(GIG) with unknown amount free. This drive is the all my files and folders storage.

-I WILL PUT PICTURE IN THE THREAD OF ALL THE STATUS,INFORMATIVE,SCANS EXT. ANYTHING I THINK MAY BE HELPFULLY ON BOTH DRIVES.

I UPLOADED SOME PICTURES of tests and informative things please look at these before you comment or answer

---

### Post by Bucky Ball on 2012-11-04
Could you open a terminal and paste this in, please:

```
sudo update-grub
```Hit enter and restart when that is finished and you are back at the cursor.

Also, just post the output of:

```
sudo blkid
```... or open up Gparted partition manager and take a screenshot of that or both. Attach the screenshot rather than inserting it in the body of the post, thanks. ;)

---

### Post by oldfred on 2012-11-04
This will not fix most Windows issues, but may show us details that can suggest a solution.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Mark Phelps on 2012-11-05
Saw the error messages about misalignment -- so I have to ask, did you use the "slider" in the Ubuntu installer to SHRINK the Win7 OS partition to make room?  That has a history of sometimes causing corruption in the Win7 OS, resulting in Win7 NOT being able to boot anymore.

---

### Post by jonathandawdy on 2012-11-05
> **Mark Phelps said:**
> Saw the error messages about misalignment -- so I have to ask, did you use the "slider" in the Ubuntu installer to SHRINK the Win7 OS partition to make room?  That has a history of sometimes causing corruption in the Win7 OS, resulting in Win7 NOT being able to boot anymore.

/sda/dev1 is the windows 7 boot-loader according to Ubuntu
/sda/dev2 is the files and folders this is the misaligned partition and according to Ubuntu is irrelevant when booting in windows

ALSO GO HERE ITS A THREAD ABOUT THE MISALIGNED PARTITION. basically a thread i posted for it [UNSOLVED] though

[http://ubuntuforums.org/showthread.php?p=12337543#post12337543](http://ubuntuforums.org/showthread.php?p=12337543#post12337543)

---

### Post by oldfred on 2012-11-05
Threads merged. Please do not create duplicate threads on the same issue.

---

### Post by jonathandawdy on 2012-11-05
> **oldfred said:**
> This will not fix most Windows issues, but may show us details that can suggest a solution.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)


OH i have a storiyfor you. 
-first i posted a post insulting you because i though you deleted my other thread.

-then i edited it saying that i was sorry for misunderstanding the word merge.

-then I got a Private Massage form UROCK(Ubuntu-Forems-CEO) saying that i got a strike for insulting staff even after i changed the massage apologizing.

Some story hey Alfred. By the way im trying what you said to 
                         do..... useing boot repair to get 
                         diagnostics.but i don't know what to do 
                         with the .iso, do i install it to a 
                         live boot?

---

### Post by lisati on 2012-11-05
@jonathandawdy: You can put the ISO file on a CD or USB stick, the same way as you would with an installation ISO.

More information can be found here:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

An alternative to using the ISO file is found on the "Boot Repair" page, in the section "2nd option : install Boot-Repair in Ubuntu"

---

### Post by oldfred on 2012-11-05
To install boot repair into your Ubuntu install you just have to copy & paste the two commands in link on Boot Repair.

If you downloaded the full ISO, you have to burn it to a CD or install to flash drive. Do not overwrite your Ubuntu flash if it is the only one you have.

All boot ISOs are installed this way. There are several installers that will correctly convert an ISO file to a bootable device and not just copy it.
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


Until we see all the details of your system we do not know what the issue(s) are. And both threads were asking for similar information, so solution is likely to be one issue, even if it may seem like more than one. 

Since we all are volunteers we want to know what others have already contributed, so we do not duplicate the instructions wasting our time when we could be helping someone else, or perhaps giving conflicting instructions.

Flying off the handle at volunteers trying to help you usually does not get more help. And most of the admins are pretty strict as there just is no reason for issues to evolve into even larger issues.

---

### Post by jonathandawdy on 2012-11-06
> **oldfred said:**
> To install boot repair into your Ubuntu install you just have to copy & paste the two commands in link on Boot Repair.

If you downloaded the full ISO, you have to burn it to a CD or install to flash drive. Do not overwrite your Ubuntu flash if it is the only one you have.

All boot ISOs are installed this way. There are several installers that will correctly convert an ISO file to a bootable device and not just copy it.
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


Until we see all the details of your system we do not know what the issue(s) are. And both threads were asking for similar information, so solution is likely to be one issue, even if it may seem like more than one. 

Since we all are volunteers we want to know what others have already contributed, so we do not duplicate the instructions wasting our time when we could be helping someone else, or perhaps giving conflicting instructions.

Flying off the handle at volunteers trying to help you usually does not get more help. And most of the admins are pretty strict as there just is no reason for issues to evolve into even larger issues.
-----------------------------------------------------------------

Don't worries Alfred i wasn't getting mad at anyone i did at you but then i said sorry. I was telling you that the CEO gave me a strike for getting mad at you but he ignored the part were i edited the comment and said sorry. I'm not being rude to staff.  
I mean why would i get mad at staff your staff and you helped me 10 hours after i posted the thread how could i be mad at you. In-fact you might even solve both of my BIGGEST problems your like my new best friend.

---

### Post by jonathandawdy on 2012-11-06
> **oldfred said:**
> To install boot repair into your Ubuntu install you just have to copy & paste the two commands in link on Boot Repair.

If you downloaded the full ISO, you have to burn it to a CD or install to flash drive. Do not overwrite your Ubuntu flash if it is the only one you have.

All boot ISOs are installed this way. There are several installers that will correctly convert an ISO file to a bootable device and not just copy it.
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


Until we see all the details of your system we do not know what the issue(s) are. And both threads were asking for similar information, so solution is likely to be one issue, even if it may seem like more than one. 

Since we all are volunteers we want to know what others have already contributed, so we do not duplicate the instructions wasting our time when we could be helping someone else, or perhaps giving conflicting instructions.

Flying off the handle at volunteers trying to help you usually does not get more help. And most of the admins are pretty strict as there just is no reason for issues to evolve into even larger issues.

-----------------------------------------------------------------

There i finally got it.

---

### Post by oldfred on 2012-11-06
Windows has what is the PBR or partition boot sector. Somewhat like MBR but first sector of partition. Windows has to have a NTFS boot signature in the PBR, that is what is missing from your sda2. 

You also have some misalignment. The NTFS boot signature has also have the start & size of the partition. That has to match partition table or you have issue. 

```
sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  [COLOR=Red]According to the info in the boot sector, sda1 has 
                       409599 sectors, but according to the info from fdisk, 
                       it has 415641 sectors.[/COLOR]

```That says it does not match. Generally chkdsk will fix that error as it sees it as NTFS.

But sda2 does not show any NTFS  signature. Partition table says it was formatted NTFS.

```
    File system:       
    Boot sector type:  [COLOR=Red]Unknown[/COLOR]
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''    ----SEE WHAT I MEAN HOW I FIX THIS-----

```Testdisk can restore from a backup the NTFS partition's PBR, or if backup is bad build a generic one that then Windows chkdsk will fix.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

If above does not work then run the rebuildBS. 
As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)


So run testdisk  from Ubuntu or Ubuntu liveCD on sda2, try to recover from backup or rebuildBS.
Then from a Windows repairCD or USB run chkdsk on sda1 and on sda2 after testdisk repairs.

---

### Post by jonathandawdy on 2012-11-08
Alfred Please check your sources because if i follow it completely it deletes my partition table,takes 4 hours,deletes all the grub config,deletes all of grub except GRUB-RESCUE;$ and says to reboot...

if i skipped the  closer scan(the one that take 4 hours) then it fixed my issue about the unknown drive. BUT I HAD TO BOOT IN BOOT-REPAIR TO GET A HOLD OF SOMEONE WHO KNEW HOW TO FIX IT

Now that i fixed my drive i need to fix windows 7. So i'm going to try windows repair and if that doesn't work then IL let you know.

SO THIS THREAD IS NOW BEEN HALF SOLVED!!!!!

---

### Post by oldfred on 2012-11-08
Repairing PBR should only take a few minutes. Did you go into the deeper search functions of testdisk to search for files. That should not have been necessary if you followed the instructions on fixing PBR or partition boot sector.

If partitions get moved or renumbered it is likely that you would have to reinstall grub2's boot loader. Boot-Repair is one the easiest ways to fix booting issues. 

But you still need to run Windows repairs from a Windows repair console.

---

### Post by Bucky Ball on 2012-11-08
Well all is half good ... 

From the Code of Conduct:

 > ALL CAPS is interpreted as screaming.

;)

---

### Post by jonathandawdy on 2012-11-13
OK my windows 7 works now but i have myself a somewhat urgent problem. Now i would make a separate thread except, what i did to fix my original problem i think may have caused a new problem.

Windows 7 has been working for about 4 days and all of a sudden my disk drive keeps making beeping noises. Also by booting Ubuntu and going to the disk utility's i see something wrong with the numbers. I added a picture because its really hard to explain.

By the way the information on my hard drive is also in the pictures.

If this is off topic Alfred then feel free to move my post to a different thread. I left it here because it was connected to the original problem.

---

### Post by Bucky Ball on 2012-11-13
Yep, well that'a well weird, but don't know if it has anything to do with what you've done to fix. If you have Win and Ubuntu dual-boot installed, and you could boot into both problem free, and your partitioning is done, Gparted shouldn't look anything like that. It should be showing it all; extended, primary, whatever partitions are there and the filesystem they are formatted as. Try this and post the result, and yes, perhaps on a new thread:

```
sudo blkid
```You should post another thread or I can move your last post to create a new thread and edit it accordingly. The editing would be better done by you so you can provide a link to this thread for people to get some background. 

If you create a new thread regarding this, post a link back here to let us know and we'll see what we can do to solve.

And yes, oldfred's a vunderkind and one very helpful and wise staff member, specially about this stuff. Much appreciated round here. ;)

---

### Post by oldfred on 2012-11-13
In addition to Bucky Ball's suggestion of blkid, run these also.

sudo fdisk -lu
sudo parted /dev/sda unit s print

Both Windows and testdisk have been know to miscalculate the last sector of the extended partition. Something to do with rounding and there use of the old CHS and new drives really being LBA. 
If a partition's sectors are beyond the end of the drive or total sectors that is a partition error and many tools stop working on partition errors.

For terminal output just copy & paste, if long include in code tags (# on edit panel)
If screenshots use the paperclip icon in edit panel to attach to your post.

---

