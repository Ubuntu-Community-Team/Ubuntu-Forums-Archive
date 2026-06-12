---
title: "Problems mounting partitions while installing Ubuntu"
date: 2015-03-27
forum: Installation &amp; Upgrades
---

### Post by JohnNicks on 2015-03-27
Hi all,

I'm trying to install Ubuntu  14.10 alongside Windows 7 on my computer.

My problems comes during the mounting of my Windows 7 partition which is NTFS standard. During that part of the install it says it can't mount it when I have tried it with mounting with /  /dos and ;/windows. If I don't mount it It comes with an error that that partition would noit be used at all.  

Is there a way that I am missing to get this to get Ubuntu and Win 7 to run side by side on different partitions of my hard drive? 

If I install it without mounting that partition, will I be able to acess that partition after I install, like another piece of software and settings in the GRUB or LILO boot loader? I would really like to have some help with this.

---

### Post by v3.xx on 2015-03-27
Careful, sounds like your removing windows.

---

### Post by ajgreeny on 2015-03-27
On the assumption that you are still able to boot into your Windows system, do so and defrag it twice, then shrink the windows partition using its own disk-management utility and finally run chkdisk a couple of times to be certain all is OK.  Now when you install ubuntu you can choose the Something Else option and point your installation to the free space that will now show.

---

### Post by JohnNicks on 2015-03-27
My problem is that I can't get back into Windows 7. The partition isn't be removed and still there but have gotten un-mounted and I don't know how to get it mounted to work right. I have tried the GParted Live CD to go in to no avail. It recognized the partition as ntfs, but in the info area it said it was unmounted, I tried to copy, resize, and all to no avail.

---

### Post by ajgreeny on 2015-03-27
Why do you (or did you) need to mount the windows partition when installing Ubuntu?  It's a long time since I used Windows of any version, but when I dual booted ubuntu and WinXP the latter was never mounted as I installed the Ubuntu OS.

I do hope you have not damaged the Windows OS while attempting to install Ubuntu.  What happens and what do you see when you try to boot Windows either normally or in safe mode?

---

### Post by Mark Phelps on 2015-03-27
You do NOT want the Windows partition mounted while trying to install Ubuntu.  If you are trying to install Ubuntu from INSIDE Windows, do NOT do that!  That was known as WUBI (Windows Ubuntu Installer) and has not been supported since Ubuntu 12.04.

The proper way to install Ubuntu is to boot from the live media and install to unallocated space on the drive.  The installer will then create and format any needed partitions.

---

### Post by JohnNicks on 2015-03-28
Mark Phelps, How do I then access Win 7 and setup GRUB after the install if it's not-mounted? I am installing it from the live media.

ajgreeny, It comes up Disk Read Error message, if I try to boot off my hard drive.

---

### Post by Mark Phelps on 2015-03-28
> How do I then access Win 7 and setup GRUB after the install if it's not-mounted?

GRUB is used to boot Linux, not Windows.  All GRUB does is hand over control to the Windows boot loader in the partition identified for Windows in the GRUB configuration file.  The Windows boot loader boots Windows.

You don't use Windows to install or configure GRUB.  GRUB is automatically installed when you install Ubuntu.

---

### Post by yancek on 2015-03-28
> Mark Phelps, How do I then access Win 7 and setup GRUB after the install if it's not-mounted?

As stated above, you do not need to mount windows partitions and generally is a bad idea.  You get an entry for windows in the Ubuntu Grub boot menu by making the proper selection during installation.  Before selecting "Install Now", you will see an option "Device for bootloader installation".  It will likely show "/dev/sda" as the default.  If you have only one drive and are using MBR to boot then leave it and it will install the Grub bootloader to the master boot record and will create boot entries for Ubuntu and windows.

 If you are using the "Install Alongside windows" option, you may not see this, I don't know as I've never used it.  If you select the Manual method, referred to as "Something Else" in the installation options, you will see it.

Also, you don't want the partition to be used during the install as it will overwrite everything on your windows partition.

It isn't clear whether you are trying to install Ubuntu or whether you have already installed it.  If you have installed Ubuntu and are getting the disk read error when you try to boot windows, boot Ubuntu if you can and log in to a terminal and run this command:  sudo update-grub
Watch the output for a windows entry.  If you don't see it, then you will need to post more drive/partition info using:  sudo fdisk -l(Lower Case Letter L in the command)

You might also take a look at the detailed tutorial below which explains installing Ubuntu in a dual-boot situation:

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by oldfred on 2015-03-28
Also the Linux NTFS driver exposes all the normally hidden files & folders in Windows. I used to always change my Windows settings to show those, but often created issues.

So better to shrink Windows some and create a separate shared NTFS data partition. Then you can mount the Windows system partition as read only and the NTFS data partition as read/write.

---

### Post by JohnNicks on 2015-03-28
I am using the live CD and haven't installed Ubuntu yet.  My computer doesnt want to recognize my Windows partition, and when I run the Ubuntu installer off the live CD it says it can't find an operating system and in the partition area it can't find it.

I want my Win 7 ntfs partition and Ubuntu on sepreate partitions.

---

### Post by yancek on 2015-03-28
Boot the Ubuntu installation medium and run the following command to display drive/partition information and post it here:  

```
sudo fdisk -l
```  That's a Lower Case Letter L in the command.

---

### Post by JohnNicks on 2015-03-29
[IMG]http://jlnicks.com/linux/Screenshot.png[/IMG]

---

### Post by oldfred on 2015-03-29
Often better to post text or teminal output directly and include in code tags or use # in advanced editor to add tags. Only attach screen shots not in line. Not everyone has high speed Internet and in line can slow them down a lot.

Since you already have Linux partition, just use Something Else and choose the same sda5 as ext4, and / (root). It will find existing swap automatically. 
I think even with BIOS/MBR install you may have issues with any of the auto install options erasing drive even if it says it is overwriting just Ubuntu. Something else is a safer way to install.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by JohnNicks on 2015-03-29
OldFred, I didn't know how to copy the terminal text.  

If I do that something else will I lose my Win 7 partition?  After install how can I get it back?

---

### Post by Vladlenin5000 on 2015-03-29
"Something else" is for manually/explicitly managing partitions, instead of the automatisms programmed in the other options that doesn't require user input.
Do as oldfred told you and you won't loose any partitions. However, you should ALWAYS have a current backup and ANYTHING you don't want to loose.

---

### Post by JohnNicks on 2015-03-29
Okay, how do I get my Win 7 partition working after install? Just as a refresh, I can't access it when I boot without the live CD it comes up with a Disk Read Error message as I stated earlier in this post.

---

### Post by JohnNicks on 2015-03-29
I know the GParted app on the live cd has this under the info of the partition:
> Failed to load runlist for $MFT/$DATA.
highest_vcn = 0x6a, last_vcn - 1 = 0x138ff
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.

Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfsprogs / ntfs-3g.

---

### Post by Vladlenin5000 on 2015-03-29
Why do you need to access your Windows partition from Ubuntu? I mean, there could be several reasons but generally it ISN'T advisable. Also, if you're having issue booting into Windows (that partition), Ubuntu won't magically solve that for you.
The error message mentions a problem with reading that partition and that can have many causes. The usual ones are a) an hibernated file system or b) a corrupted file system. Neither situation is "solvable" from another OS. You MUST boot Windows and, for a) just make sure you shutdown the OS properly, or, for b) use Windows tools to check/correct its own file system.
It should be so hard to understand...
```
[COLOR=#ff0000]NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE![/COLOR]
```

---

### Post by JohnNicks on 2015-03-29
My problem like I have said before, I can't boot into Windows.

---

### Post by Vladlenin5000 on 2015-03-29
You can, if you use a Windows installation media or any other bootable CD with Windows tools, and hopefully you can recover from there.
The errors you posted are consistent with the problem I already mentioned and you just confirmed.
*If* you're trying to install Ubuntu in order to *fix* Windows, then forget it and move on. In previous posts this was implicitly suggested but you didn't get that, those subtle hints...

My blunt, in-your-face, approach hopefully will make you realize how pointless it is. And yes, you may have to reinstall Windows and if you need help for that there are plenty of Windows fora, blogs, tech support sites, whatever... We're NOT a Windows recovery service.

---

