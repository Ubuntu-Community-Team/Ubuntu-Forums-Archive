---
title: "install Ubuntu(Linux) along side Windows7 so that the computer could dual boot with e"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by nani2 on 2014-07-15
[COLOR=#000000][FONT=monospace]I wanted to install Ubuntu(Linux) along side Windows7 so that the computer could dual boot with either operating system. Since Windows7 was already installed on the laptop. Then tried to install Ubuntu version14 but it doesn't give the option of installing it alongside windows. It only sees the entire hard disk volume as a single partition (it doesn't recognize the windows partition on the hard disk).[/FONT][/COLOR]

---

### Post by grahammechanical on 2014-07-15
My suggestion is to run Ubuntu as a live session and when you get to a desktop click on the Ubuntu icon at the top of the launcher on the left. That will open the Dash. In the search panel type Gparted and load that application and let it examine the hard disk. Write down the information about the hard disk and the partitions and post the information in this thread. Another utility to use is called Disks. 

You could use a Windows 7 utility to examine the hard disk and take a screen shot of what that utility is showing about the hard disk and post that image here. We need a clear knowledge of the partition layout of that hard disk. Otherwise we are just guessing.

Regards.

---

### Post by yancek on 2014-07-15
The most likely scenario is that windows is occupying the entire hard disk and there is no free or unallocated space on which to install Ubuntu.  Posting the information requested above should confirm this.

---

### Post by Mark Phelps on 2014-07-15
> Since Windows7 was already installed on the laptop.An unfortunate common practice amongst OEMs is to install 4 partitions on a Windows laptop, and since that is the max you can have (using MBR formatting), Linux can't create any more.  It's not a matter of the drive being full; it's a matter of too many existing partitions.

To see what you have, boot from the Ubuntu install media, open a terminal, enter "sudo fdisk -lu" (lowercase L, not a one) and post the results back here.

If you already have the 4 partitions limit, I will reply with a post containing details about how you can address that.

---

### Post by nani2 on 2014-07-16
I ran the Gparted utility and here is what I got.

I clicked yes and here is the partition table.

It doesn't recognize the windows partition and sees the whole hard disk volume as unallocated.


[ATTACH=CONFIG]254761[/ATTACH][ATTACH=CONFIG]254762[/ATTACH]

---

### Post by oldfred on 2014-07-16
Still do not know how many partitions you have, but did you install Windows 7 over Windows 8.
Windows 8 would have been UEFI with gpt partitioning. 
Default install of Windows 7 from DVD is BIOS boot with MBR(msdos) partitioning, but the Windows installer only converts primary gpt partition table and leaves a backup gpt partition table.
Then Linux tools see both MBR & gpt partitioning and does not know what to do other than install to entire drive.

If Windows is BIOS boot with MBR, remove backup gpt partition table using live installer.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by nani2 on 2014-07-16
Yes, the laptop previously had Windows 8 OS. I tried to install FixParts from a live Ubuntu session using the package manager. After downloading the FixParts package [http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.7/fixparts-binaries/fixparts_0.8.7-2_amd64.deb/download](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.7/fixparts-binaries/fixparts_0.8.7-2_amd64.deb/download), I attempted to install it but I got a message that read &#8220;failed to install properly&#8221; or something to that effect.
 I am a bit confused of where to go from here :-(

---

### Post by oldfred on 2014-07-16
Were you using a 64 bit version of Ubuntu's live installer? I have not had issues installing fixparts and many others have used it. Not sure then why you would have issue.

You can also use gdisk, but it is a bit more complicated than fixparts. And you have to then be sure that you are not converting to gpt from MBR. You want just the MBR configuration.
gdisk is more for use with gpt drives. (see caution on fixparts page).

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

gdisk is in repository so it should install without issue.
sudo apt-get install gdisk

---

### Post by nani2 on 2014-07-16
Does the conversion from GPT to MBR result in data loss and re installation of Windows7? It seems that the procedure is complicated for a novice like me. There might be a good chance that I could inadvertently corrupt my hard disk! I wanted to install Ubuntu because I'm taking an introductory Linux course.

Would installing Ubuntu first and re install Windows 7 afterwards be possible? Or would make matters even worse?

---

### Post by oldfred on 2014-07-16
Normally converting from one partition scheme to another totally erases drive. But gdisk can do a convert in some cases. But required partitions for booting are a lot different. And Windows would then require total reinstall as it only boots one way from each.

Good backups always required.

But Windows only boots from a gpt drive with UEFI and only boots from MBR with BIOS partitioning.

Linux will boot from gpt with either BIOS or UEFI, but grub can only dual boot systems installed in same boot mode.

---

### Post by nani2 on 2014-07-18
I installed Ubuntu on another laptop, and will be using that for the Linux course.

Thanks for all the folks who helped me!

---

