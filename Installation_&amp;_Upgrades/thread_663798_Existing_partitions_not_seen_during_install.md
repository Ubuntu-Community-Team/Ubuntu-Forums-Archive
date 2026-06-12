---
title: "Existing partitions not seen during install"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by utnubu2ebun on 2008-01-10
I have an WinXP Pro install on a Dell Inpiron 8600.  I have tested the machine using the LiveCD and like what I see and am attempting to install.  I have a problem with the ubuntu installer not seeing existing partitions that I created.  I am using Acronis Disk Director to manage my disk partitions.  I think I have read enough of the posts to have some understanding of what is required and this is what I have setup:

Part 1: Primary 51GB NTFS for XP
Part 2: Logical 10GB FAT32 used as a hidden partition for backing up critical data from XP using Acronis True Image.
Part 3: Primary 10GB Ext3 prepared for root(/) Ubuntu install
Part 4: Logical 1.25GB Linux Swap
Part 5: Logical 20GB NTFS for common data storage and Ubuntu /home

The reason I wanted to prepare the partitions from XP is that I didn't want to loose Part 2 since it was a hidden partition, although I think it is only hidden from XP.  The large XP partition is due to VirtualPC running various testing instances of XP, although I don't think size is an issue.  I don't have any unallocated space.

When running from the LiveCD of Ubuntu 7.10, the file browser shows all my partitions on the internal HD (including the NTFS Parts) except for the Linux Swap, as well as my usb connected drive.  The problem starts when I run GParted from System>Admin>Partition Editor.  It lists the HD as /dev/sda with the entire drive unallocated 93GB.  The external drive shows up just fine as /dev/sdb1 152GB with 14GB used, 139GB free.  Then when I run the install, on step 4 for the Partitioning I choose Manual.  I get the same results and the following drive listing:
[FONT="Courier New"]
/dev/sda
/dev/sdb	
   /dev/sdb1		163921 MB  unknown
[/FONT]

Looked like a problem with GParted in the 7.10 distribution, so I also ran the GParted LiveCD.  When I run it in (with force VESA) to get the GUI I get the same result showing the entire drive unallocated.  When I run it in console mode and then run the 'partimage' command, it does show all the partitions correctly in an older dos style window titled 'Partition Image 0.6.4'.  I am not familiar with this tool, so don't know why I am seeing the partitions this way but not in the VESA/GUI mode nor during the Ubuntu Install.  Any insight as to what to try next would be greatly appreciated.  Thanks.

---

### Post by wolfen69 on 2008-01-10
run the install setup and when you get to the partitioning part choose manual and see if the partitions are there. if not, you can create the needed partitions then.

---

### Post by dabang on 2008-01-10
I'm not familiar with Acronis Disk Director, but it's very unusual that Linux can't see your partitions. A few things come to my mind though.

Guess Nr.1: Acronis Disk Director does something really strange and proprietary to the partition table...
Guess Nr.2: How are your logical partitions located on the disk? I may be wrong, but I thought only 1 extended partition is aloud? So, are your logical partitions located in one extended partition? If not, maybe that's the problem?

What you could try is:
WARNING: Backup your data first! This could destroy your partition table....

- Disconnect all external USB drives
- Delete all partitions meant for linux with the same tool you created them.
- Run Ubuntu Live CD again
- See what gparted does
- If gparted fails again, open a console and type: sudo cfisk
- If cfdisk fails too, I have no further clue, if not, create your partitions with cfdisk, start installer again and I guess it should work then

By the way: DON'T use NTFS partitions for /home (or any other linux filsystem)! I don't even know if the installer would do this?

This is how it could look like:

sda1 - WinXP
sda5 - Acronis backup (logical drives start with "5")
sda6 - swap
sda7 - shared NTFS (I'd use FAT32)
sda2 - / (ext3)
sda3 - /home (ext3)

This would make 3 primary and 3 logical partitions.

I don't know if this is of any help, sorry.

---

### Post by utnubu2ebun on 2008-01-10
> **wolfen69 said:**
> run the install setup and when you get to the partitioning part choose manual and see if the partitions are there. if not, you can create the needed partitions then.

When I run the setup and select manual, the partitions are not there.  The drive is unallocated.  When I then go to create a new partition table a warning message says"you have selected an entire device to partition.  if you proceed with creating a new partition table on the device, then all current partitions will be removed".  So I bail at this point since the only thing I can select is the entire device and proceeding will wipe out my XP and Backup Partitions.  I don't see any other options or settings for creating partitions on this window.  Ideas on how to create partitions at this point without loosing the existing partitions?  Thanks.

---

### Post by utnubu2ebun on 2008-01-10
> Guess Nr.1: Acronis Disk Director does something really strange and proprietary to the partition table...

a definite possibility.  It doesn't mention an extended partition in its operation.  Not sure if that is just to make it simple to use or if it does something proprietary.  The partitions DID show in the Ubuntu file browser and with the GParted console, so ??

> Guess Nr.2: How are your logical partitions located on the disk? I may be wrong, but I thought only 1 extended partition is aloud? So, are your logical partitions located in one extended partition? If not, maybe that's the problem?

The graphical representation does not put the logical partitions inside an extended, so could be.

I think I will try:
1) your suggestion of leaving free space by removing Intended Ubuntu partitions.
2) if no success, go back to a single partition, see if I can get Ubuntu in and then recreate my backup part.   And yes, back up all before.  

Thanks for your help and I will report on the results.

---

### Post by utnubu2ebun on 2008-01-11
Success after lots of trial and error.  

- XP: I had to remove all partitions, first the ones I had made for Ubuntu and then my backup partition.  I left the main XP partition alone, so had a large chunk of free space.  
- Ubuntu Intaller:  I was then able to setup the partitioning in the installer, but it failed to format the 10GB ext3 I had setup for the root.  Running GParted in Umbutu couldn't format it either.
- XP: I went back to XP and Disk Director and saw all the parts and was able to format the partition to ext3.
- Ubuntu Installer:  Installer saw the partitions with proper formting and I was able to assign the root and /home directories.  

I did leave 10GB free to see if I can get the hidden backup partition back on the drive from the XP side without Messing it all up.

Lesson is to simplify and clean up the drive first, then use GParted through the installer or alone to create the proper setup.  Still don't know why I could see the partitions in file directory and GParted console, but not in GParted GUI and Ubuntu Insaller, but I think I'll just leave that  a mystery and move on.

So Ubuntu seems to work on this old laptop (Dell Inspirion 8600), a bit slow, but good enough to test out.  Now on to getting wireless network, wireless mouse/keyboard to work, installing apps and seeing what it can do.  Thanks for your quick responses and help.  Reading through the posts, this seems like a really supportive and active forum.

---

### Post by dabang on 2008-01-11
Congratulations!! And good to hear/read. Hard to tell what was causing those issues, but I think it was the hidden partition. I guess it's likely to work if you create one now. So good luck! If you need any help, come back here or have a look at [http://tuxmobil.org/](http://tuxmobil.org/)

Cheers!

---

### Post by dburnett77 on 2008-01-11
You need to find the vmlinuz command that boots your partition for the installs you're trying to save.

For SUSE, it's:  /dev/sda
Ubuntu:  /dev/hd0

etc.

Take a look at your rc.local files, and it should be in there.  Copy that to which ever install you just did, and copy it in via grub manager.  Or, just include it via text editor in your boot file:

which for Ubuntu, is:  /boot/menu.lst

and is also the format used most by GRUB:  that is the /boot location.

---

### Post by utnubu2ebun on 2008-01-13
> **dburnett77 said:**
> You need to find the vmlinuz command that boots your partition for the installs you're trying to save.

Being new to Ubuntu, I am a little lost here . .  Ubuntu is booting just fine and gives me the option to select different Ubuntu modes and XP.  

> **dburnett77 said:**
> which for Ubuntu, is:  /boot/menu.lst

I found this and think that when I get back to work this week I will need it to load XP automatically rather then Ubuntu.  I think I read about doing this elsewhere in the forum, but have been unsuccessful in finding it.  What I have is:

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3ad56fd3-67f0-4ddf-995a-3f056026c2bc ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3ad56fd3-67f0-4ddf-995a-3f056026c2bc ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

I am guessing I just move the XP entry above the Ubuntu ones.  Thanks!

---

### Post by dburnett77 on 2008-01-16
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

has good info., and also some of the links may provide better information than I've given.
It goes into detail how to restore GRUB, and the menu.lst options.

---

### Post by utnubu2ebun on 2008-01-16
> **dburnett77 said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

has good info., and also some of the links may provide better information than I've given.
It goes into detail how to restore GRUB, and the menu.lst options.

Thanks for this.  I like to come at it from both directions, using the tools and also opening up the files and looking around.  I have edited the menu.lst file putting the following code that was at the end above the three Ubuntu options.  

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Now when I boot, XP is at the top of the list and if I don't do anything it is loaded.  Someday I hope to switch the order back and use Ubuntu as my primary OS, but for now this works so that I can experiment and learn in Ubuntu.  Thanks for your help.

---

