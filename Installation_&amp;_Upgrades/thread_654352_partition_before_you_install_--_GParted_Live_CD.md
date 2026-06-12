---
title: "partition before you install -- GParted Live CD"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by Charles-2007 on 2007-12-31
Executive Summary:  give some consideration to downloading and using the standalone GParted partitioning software to simplify your subsequent Ubuntu installation.  You can get it from Sourceforge:

[http://gparted.sourceforge.net](http://gparted.sourceforge.net)

OK longer explanation:  yes this is in the Ubuntu build but boy is it easy to run as a freestanding GParted Live CD.  I write this as a relative newbie who has done three installs on different machines and, like many folks, wanted to dual boot.

GParted (in whatever form) allows you to repartition without crashing your existing Windows partition.  Running it independently, you can focus on this one task before having to deal with the Ubuntu install.

The download is an ISO file (just like the Ubuntu downloads).  I think it is worth the effort to get this independently.

Best wishes.

---

### Post by forestpixie on 2007-12-31
+1

But before you start make sure you're backup's are ok

---

### Post by Charles-2007 on 2008-01-01
Yes the info at Psychocats is excellent.  Hermanzone at Bigpond has great stuff too.

I posted my recommendation because I bet there are number of people interested in trying out Ubuntu on their Windows-based machines and many of these PCs have a single hard drive with Windows on "C:" and backups on "D:"

Since these are just partitions of a single hard drive, GParted allows the Windows user to repartition without corrupting data (yes back-up your stuff anyway and probably run DEFRAG in Windows first).  The paranoid Windows user can then reboot and be reassured that it all still works and then move on to Ubuntu installation.

I basically followed Psychocats advice.  I created the following partitions using GParted Live (which is fantastically easy to use):
-partition with Windows (no change on my machine although you can shrink it it you wish)
-partition for files shared between Windows and Ubuntu e.g. DOC or Open Office formats
-partition for Ubuntu formatted as ext3
-partition for Linux swap files formatted as swap files

Evidently the new Ubuntu release can natively read/write off NTFS partitions but I was chicken and have the common partition FAT32.

Then when installing Ubuntu rather than using "automatic" partitioning opt for "manual" and tell the installer to put Ubuntu into the ext3 area (this will look something like /dev/hda5 so you might want to write this partition down if you use GParted first).

There are some other options (like telling the installer where to mount the installation, for which I selected "/") that can be viewed at psychocats.net -- I have just written the above to help some poor Windows user who is as dumb as I am or as cowardly.  Believe me if I smoked my Windows installation and messed up my wife's settings, I would not be IN the doghouse, I'd be buried UNDER the doghouse!

Best wishes.

---

### Post by observative on 2008-01-01
Just confirming that Charles-2007's Executive Summary worked for me...although I still had to use the Alternate CD due to "no root file system" error. BUT it did work :)

I also want to confirm that "Evidently the new Ubuntu release can natively read/write off NTFS partitions...". Gutsy Gibbon (Ubuntu 7.10) does read/write from/to my secondary common NTFS drive and the NTFS partition on my primary dual boot disk with w2k and u7.10.

Thank you Charles-2007!

Edit:
I thought I should add that I ran up against more brick walls because of "bad hardware installs and CMOS configuration" than I could imagine. Make sure your hardware is properly installed, configured, and files backed up before you proceed with partitioning and/or installation. This shouldn't be much of an issue to those who bought a "off the shelf" computer, more so for those (like myself) who have added and changed hardware over the years or just started that way. I have seen many posts that conclude with "bad hardware installs".

I'm also adding that upon a second attempt (with hardware properly config'd) that the Live CD installed just fine for a dual boot on my W2K server.

---

### Post by momist on 2008-01-02
> **Charles-2007 said:**
> Executive Summary:  give some consideration to downloading and using the standalone GParted partitioning software to simplify your subsequent Ubuntu installation.  You can get it from Sourceforge:

[http://gparted.sourceforge.net](http://gparted.sourceforge.net)

GParted (in whatever form) allows you to repartition without crashing your existing Windows partition.  Running it independently, you can focus on this one task before having to deal with the Ubuntu install.

The download is an ISO file (just like the Ubuntu downloads).  I think it is worth the effort to get this independently.

Best wishes.

Hi Charles,  Thanks for the pointer.  I thought that this would be the ideal way out of my current fix, but it seems nothing is that easy.

My problem was to replace a very defunct Dapper installation with the latest Gutsy. When the simple install failed and I lost my MBR, I had to use the WinXP installation disk to recover a usable computer.  The hda has 23Gb given  to XP and 5Gb to (K)Ubuntu, with a bit left over for SWAP.  The hdb has three large FAT32 partitions for files to be shared.  Now XP shows hda as part NTFS and part 'Unallocated', so I thought the thing to do was use GParted to format the unallocated area to Ext3.  GParted live CD won't run an X session, and complains that as I'm still in BASH, I should run a script, but I can't make that work either.

I have looked around the 'net for information on the live CD, but can't seem to find a simple instruction of how it should be used?

Ian

---

### Post by momist on 2008-01-02
OK, so I found this:
[http://gparted-livecd.tuxfamily.org/larry/livecd/livecd.htm](http://gparted-livecd.tuxfamily.org/larry/livecd/livecd.htm)
but it says "Once this is done, the graphical mode will start...", which it doesn't!  I really don't know how to run the Forcevideo script, as everything I try returns "Command not found"

---

### Post by Charles-2007 on 2008-01-07
First off, if you mess up your dual boot installation you can clean up your Windows boot.  You need a Windows or DOS boot disk (or your Windows CD) so you can run from a command line

fdisk /mbr

You can research this command on the Microsoft site for your reassurance.

Now, I'm just a rookie.  The Ubuntu Live CD by default installs GRUB (the boot program) in the MBR (boot sector).  GRUB is nice, although some Windows anti-virus programs don't seem to like it.  I didn't want to use GRUB on my dual boot desktop at home, to avoid potential marital discord.  You can tell the Live CD in the final step NOT to do this.  This is under "advanced" options and you can tell the install CD to put it in the same partition as your Ubuntu install.

If you flummoxed your dual boot and put it back to Microsoft flavor, or you told the installer to put the boot software in the Ubuntu partition, then when you boot into Windows it will seem that the Ubuntu installation is hidden.  It is:  Windows can't see it.

There IS a way to get Windows to offer you the option to boot to Ubuntu.  I will write about that later after I review some references.  Meanwhile, if you don't want to use GRUB, download "GRUB Super Disk" to burn to CD.

Then under normal circumstances the PC will boot to Windows.  Using the boot disk, you can opt to boot to Linux.  Hmm maybe this isn't so bad if you have toddlers whacking the keyboard...

Best wishes.

---

### Post by Charles-2007 on 2008-01-07
Addendum for Momist I cautiously speculate that if your Windows installation is working, leave that alone, and perhaps you could use GParted to delete the other partitions and re-establish them,then do a clean install of the latest Ubuntu release.

I'm thinking if Windows is in a NTFS or FAT32 partition, using GParted you can create an EXTENDED partition with a logical partition (NTFS or FAT32) in the extended partition.  Windows will load from the C: drive and will see that as a D: drive.  Windows will NOT see ext3 partitions you create, which is the format where Ubuntu will be installed.

It is FAR easier in my opinion to see this using a GParted Live disk than the Ubuntu installer.

More about booting Linux from Windows later.

Best wishes.

---

### Post by Charles-2007 on 2008-01-08
Here's a reference
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/BootMenu](http://ubuntuguide.org/wiki/Ubuntu:Feisty/BootMenu)

My desktop PC with a single drive was running Windows XP.  I used the GParted Live disk to create a separate ext3 partition and then used the regular Ubuntu Live disk to do an install.  When the partitioner started I used the "manual" option and told it to install Linux in that partition at "/".  After that selection, the final menu before the installation has an "advanced" option and I told it to install the bootloader GRUB in the same partition as Ubuntu.

After a reboot, I was back in Windows.  Next, you will find various HOWTO pointers on editing the Windows boot to offer you the option of booting Linux via GRUB (Psychocats, Hermanzone, or the above).  You may need to run a command line to make boot.ini editable:
Start --> Run --> CMD --> terminal window...
attrib -r -h -s boot.ini

I then edited boot.ini just adding a line at the end of the file
C:\loader\Ubuntu.mbr="Ubuntu"

This makes the Windows boot offer you Windows vs Ubuntu.  But you'll need to create the folder C:\loader (easy) and the file Ubuntu.mbr (less easy).  To generate the file Ubuntu.mbr I used a FAT formatted floppy to move it around as I struggled with the subsequent syntax to generate the file.

BUt first you have to get back into Ubuntu.  As everything is installed on the Ubuntu partition, it is invisible on a normal boot.  You can download a "GRUB super disk" and burn it to CD and boot with that.  You will be opting for manual boot and pointing the CD to the Ubuntu partition.

Are you sick of this yet?

In Ubuntu, open a terminal window and type the following (I had to run "sudo su" to enter my root password first)

dd if=/dev/sda3 of=/dev/fd0/Ubuntu.mbr bs=512 count=1

The "sda3" is the partition where my Ubuntu is; yours may be hda2 or something different.  That's the source of the code to be compiled and fd0 (that's a zero) is my floppy drive.

That generated the file Ubuntu.mbr on my floppy.  Back in Windows I put it in that C:\loader folder.

This is way too much work; just using GRUB in the MBR is way easier but then I'm stubborn.

Best wishes.

---

### Post by picard12 on 2008-01-08
does GPart require user to format the whole HD before partitioning?

Can GPart partition the HD while it still has Linux ?

ok. I tried to use the GPart live CD without success. The CD ask me to run ForceVideo script at command line. It indicates video is required to load GPart.

I chose autoconfiguration method for partitioning HD at the start of live CD boot up screen. 
[I]I don't know the command line for ForceVideo script.
[/I]

---

### Post by momist on 2008-01-09
> **momist said:**
> OK, so I found this:
[http://gparted-livecd.tuxfamily.org/larry/livecd/livecd.htm](http://gparted-livecd.tuxfamily.org/larry/livecd/livecd.htm)
but it says "Once this is done, the graphical mode will start...", which it doesn't!  I really don't know how to run the Forcevideo script, as everything I try returns "Command not found"

Hi Charles-2007, and thanks for the interest in my problems.  I found later that I was not being careful enough about the 'case' in my attempt to run the Forcevideo script, and if I gave it the capital letter at the front it would work OK.  Having gone into the graphical mode, I managed to fiddle my way through, to find that even GParted live CD would not recognise the old Linux partitions.  My attempts to install from the Gutsy CD had really screwed up the format of that part of the hard drive, and although my use of the WinXP installation disk to re-establish the MBR worked OK for Windows, the Windows partition is no longer recognisable by GParted.  I had a try with SuperGrub, but that also wouldn't find the old partition structure, and didn't correctly recognise the windows partition.  When (inevitably, one day) I have to re-install windows again, I'll format the whole of hd0 and start that one from scratch.

I have solved the problem by removing my redundant CD drive, (I have a DVD drive as well) and fitting an old 20GB hard drive in it's place, so now I have 3 IDE hard drives, and one external USB!.  I've installed Gutsy on hd2, but in doing so discovered that I did indeed have a "bad" CD, even though I had checked the MD5Sum of the ISO file before burning!  Luckily, I had the "Alternate" CD as well, and that saved the day.  So, I've formatted the whole of the third hard drive to give a clean install of Ubuntu 7.10, with /,  /usr, /home and swap.  

The / partition is now getting rather full, and the /usr is mainly empty.  I'm going to have to start again, and give more room to root.  I don't suppose I can change the partition sizes without starting from scratch again?  I am simply ignoring the wasted space on hd0 that used to be my Dapper installation.

Thanks again for the advice offered.

---

### Post by momist on 2008-01-09
> **picard12 said:**
> does GPart require user to format the whole HD before partitioning?

Can GPart partition the HD while it still has Linux ?

ok. I tried to use the GPart live CD without success. The CD ask me to run ForceVideo script at command line. It indicates video is required to load GPart.

I chose autoconfiguration method for partitioning HD at the start of live CD boot up screen. 
[I]I don't know the command line for ForceVideo script.
[/I]

Hi Picard,

I had the same issues.  I believe that the GParted live CD will let you partition parts of the drive while leaving some other parts alone.  However, any part you do do partition will lose any software already on it, so this will damage any existing system.  The exception is that under certain circumstances, you can shrink the windows partition safely, if it has been defragged and there is room.

To run the script from the command line, I just issued the command at the $ prompt;
Forcevideo
but the trick is to use the exact characters, case sensitive!  YMMV of course.

Good luck

---

### Post by Charles-2007 on 2008-01-10
I've used the GParted Live disk on three PCs and could change partition sizes and add new partitions to freed or emptied space -- without reformatting the existing drive and without data loss.  Telling the program to change format of an existing partition would I presume result in data loss.  For example, changing an existing Windows partition from FAT32 to NTFS would I assume trash the data.

I am in the dark about your issue with the GParted Live disk having an issue with the video driver although I do recall seeing that load when the disk boots.  There are some options presented the initial menu that might overcome that hold-up.  I'm a mere user, not remotely expert in this arena.

Best wishes.

ADDENDUM if you want to change your Windows partition from FAT32 to NTFS, see this Microsoft info:

[http://support.microsoft.com/kb/307881](http://support.microsoft.com/kb/307881)

---

### Post by maechismo on 2008-01-15
hi Charled-2007,

I have been following this thread for couple of days now. I have recently installed Ubuntu on my Windows XP which had only one partition. I partitioned my hard disk using the Gparted tool. 

I have been following your steps and after I completed installation as u say it rebooted to windows XP. 

now, What I did is I rebooted using the Gparted again and made Ubuntu partition bootable(by checking the bootflag in Gparted tool) and i chose the swapon option on Linux_swap partition, applied the changes and it works.

When I reboot the system it asks me to chose between Ubuntu and Windows XP and it works.

But if I make windows XP bootable( by checking boot flag in Gparted tool) and even if I swapon Linux-swap partition it doesnt give me option to chose between the two OS.

I did not have to follow these steps where I was unsuccessful when I did :(...im a dumbhooo....but am happy with those changes making Ubuntu partition bootable.

Do u think is this the right way to do!? any suggestions please and also I was not able to successfully created the boot.ini on my windows it says file not found:(......

Can you please advise on this!?

thanks!

---

### Post by louieb on 2008-01-15
I have trouble using the GParted live CD on certain computers. 
The way I get around it is to use the [SystemRescueCd]("http://www.sysresccd.org/Main_Page"). It has GParted on it and other tools that are really nice to have around when you need them.

---

