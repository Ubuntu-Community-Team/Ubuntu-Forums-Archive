---
title: "two HD, two boot sectors, and grub picks the wrong one"
date: 2012-08-06
forum: Installation &amp; Upgrades
---

### Post by moshuptrail on 2012-08-06
I've got 2 hard drives.  One came with the machine and has windows on it.  The other I added, and it has 12.04 LTS on it.  I've had Linux 8.04 and 10.04 on this for years.  So the grub menu is getting really long and the partition for / is actually too small.  So when I installed 12.04 to a new partition on the second hd, for some reason the install went flawlessly but when I rebooted it it found the old grub on hd0 and booted 8.04.  

I seem to remember that I had to set up a link in the grub menu on hd0 to chain to the grub menu on hd1 in order to make this work because you can't boot from hd1 to windows on hd0.  You have to boot to hd0 first/

Anyway, I need help to customize my grub menus.  The new grub is not the old "menu.list" that I remember :)

---

### Post by oldfred on 2012-08-06
Normally we do suggest changing boot order and that works, but there seem to be some like yours that it does not.

Best to post link from BootInfo, so we know exactly what is where. But it can also reinstall grub2's boot loader to either drive if desired. You can download into Ubuntu's liveCD or download it as a full liveCD.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by moshuptrail on 2012-08-06
Boot-info: [http://paste.ubuntu.com/1133504](http://paste.ubuntu.com/1133504)

I know. It's a freekin' mess.
Long story.  When I got the 200 I thought the 80 (this PC is nearly 10 years old now) was failing.  So I did a sector-by-sector copy from the 80 to the first 80 of the 200.

Anyway.  Boot-repair did a great job.  I was able to boot into 10.04 or 12.04.  There are still about 25 entries for older kernels for 10.04.  Can I get rid of most of those?

Evidently something in 12.04 is totally incompatible with my gnome settings in 10.04 (no surprise there) but I could not log in with my user ID because I think it's trying to read something there and bombs out and drops me back to the login prompt.

Any suggestions what files to delete?

But thanks for the tip on Boot-repair.  I made a CD and it's slick little utility.

---

### Post by oldfred on 2012-08-06
Maybe time for some housecleaning.
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

I use synaptic and keep the current kernel and one older one.
Check current kernel I also keep one older just in case:
uname -a
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

I like to have each system on a separate drive and each boot loader for that system in the MBR of that drive. You currently have the same in both MBRs.

If/when you can boot into 12.04 you can do this to install its boot loader to the MBR of sdb.
sudo grub-install /dev/sdb

You are sharing the same /home which may lead to some issues with the totally different versions.

Your Windows have a couple of issues. The boot.ini in sdb is identical to the one in sda. Drive is hard coded into boot.ini. Windows NTFS partition have the same info as the partition of start sector & size. Script says those settings are not correct. Often chkdsk or chkdsk & fixboot from your XP install disk will fix the size info. Repairs only work on the NTFS partition with the boot flag. But you have that, not sure what it does with two drives. When two installs are on one drive it literally deletes the boot files from the second install and moves them to the install with the boot flag.

XP CD fixboot  - not sure you need all of these, but I just copy the whole thing:
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 
Boot files may need attributes also:
attrib +r c:\filename
attrib +h c:\filename
attrib +s c:\filename

---

### Post by moshuptrail on 2012-08-07
Wow!  Thanks for that analysis.  Not sure I can "read" it, more accurately, I need to "study" it :)

---

