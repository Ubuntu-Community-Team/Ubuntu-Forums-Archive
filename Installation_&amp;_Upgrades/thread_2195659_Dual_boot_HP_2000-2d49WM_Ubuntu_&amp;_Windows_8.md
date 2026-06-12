---
title: "Dual boot HP 2000-2d49WM Ubuntu &amp; Windows 8"
date: 2013-12-25
forum: Installation &amp; Upgrades
---

### Post by EpicMinerBackup on 2013-12-25
OK so I want to dual boot with my new laptop I got yesterday it has windows 8.
I used my USB to try to install Ubuntu 13.10 but it does not show that win 8 is installed and does not give a option to dual boot install
and I don't know how to do it manually please help me out.

---

### Post by oldfred on 2013-12-25
Did you turn off fastboot or the always on hibernation? Often better to turn off secure boot also.

       Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by EpicMinerBackup on 2013-12-25
How would I back them up

---

### Post by oldfred on 2013-12-25
These are often suggested for Windows.
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)



Often for Ubuntu clonezilla is used for image backups. But with Ubuntu it is easy to reinstall so many of us just backup /home, /etc, list of installed apps, and any thing else we create but not the system.

---

### Post by EpicMinerBackup on 2013-12-26
I'm sorry if this is annoying but I'm very new and a little bit stupid when it comes to this is there at all any videos or simple instructions that I could follow? 
Sorry again.

---

### Post by oldfred on 2013-12-26
There are several videos, now a bit older but the same processes for installing in the link in my signature. Videos are at the bottom of the first post.

---

### Post by bilkay on 2013-12-26
I'm going through much of the same with an HP 2000 I bought for my wife. I tried to install from a 12.04.3 DVD but all I got was a black screen for both install and demo. I also tried with a 12.04.1 DVD and got the same result. I went to HP tech support and got on chat with a technician. He told me:
1. disable secure boot.
2. enable legacy support.
3. my software warranty will be voided.

I did 1 and 2, but I still only got a black screen from the .3 disk (install and demo). I then tried with the .1 disk and demo came up fine (didn't try install yet). I'm thinking that the difference may be because the .1 disk is the 32 bit version and the .3 disk is 64 bit.

Reading other posts, I see recommendations that the re-partitioning should be done by windows. I'm not sure how to do that. Windows shows that the disk already has 5 partitions. What's odd about that is there are 2 D: partitions which are identical except the type for one is blank and the other is NTFS. I see an option to shrink the partitions, but I'm unsure how to proceed from there in windows. A concern I have is that if I shrink the C: partition and then add another partition in the empty space, it will have to be an extended partition. I'm not sure if that will be a problem.

---

### Post by bilkay on 2013-12-26
Progress report:

I tried booting from a usb stick (12.04.3 64 bit and 32 bit versions), still getting nothing but black screen. Went back to old 12.04.1 (32 bit) cdrom and got the try/install screen. Presently running "try" (seems to work OK). Next, ran fdisk /dev/sda which only returned one device (/dev/sda1) system: GPT. The man page for fdisk says "fdisk  does  not  understand GUID partition tables (GPTs) and it is not designed for large partitions.  In these cases, use the  more  advanced GNU parted(8)."

Next, ran gparted /dev/sda. It shows 5 partitions (/dev/sda1 ... /dev/sda5).

Partition--------        File System-----      Label----------     Size------------       Used----------       Unused-------      Flags
/dev/sda1------ ntfs--------------- WINRE-------- 400.00 MiB--- 259.06 MiB--- 140.94 Mib-- hidden, diag
/dev/sda2------ fat32------------- ------------------ 260.00 MiB--- 98.67 Mib---- 161.33 Mib-- boot
/dev/sda3-!---- unknown-------- ------------------ 128.00 MiB--- ----------------- ---------------- msftres
/dev/sda4------ ntfs--------------- Windows------ 675.84 GiB--- 36.18 GiB----- 639.66 GiB-- ------------
/dev/sda5------ ntfs--------------- RECOVERY-- 22.03 GiB----- 19.79 GiB----- 2.24 GiB----- hidden

I'm really concerned about what might happen if I try running "Install". All of this wouldn't be a problem with a wubi install, but we're warned against using it in Windows 8. Is this a permanent thing or is there a fix in the works? Anyone know?

---

### Post by oldfred on 2013-12-26
New computers with Windows 8 have UEFI and gpt partitioning. There is no limit on partitions with gpt (well it really is 128 as a default).  And all partitions then are primary.

fdisk is only for MBR(msdos). I think they are working on a new version that also supports gpt, but there already is gdisk which is a fdisk for gpt partitioned drives. gdisk is in the repository and easy to install.

You do need to use Windows to shrink its partition to make unallocated space. And reboot so it runs chkdsk to fix itself to its new size. And you need to make full backups of Windows and the efi partition.

Please review all the collected links and info in the link in my signature. It is a lot but can answer all your questions.

All the new computers really need 13.10 as Intel has offered a lot of updates for its new processors to the kernel & support software. That is in 13.10 and 12.04.4 in Jan will probably even have more updates. UEFI secure boot support only started with 12.04.2 so you should not use any earlier versions.

---

### Post by bilkay on 2013-12-26
I made and ran a 13.10 64 bit install usb and I'm still getting the black screen (after the GRUB try/install menu). Tried with and without secure boot - no luck. Can't find any other settings that might be the problem.

Any reason my subscription to this thread was removed?

---

### Post by bilkay on 2013-12-26
Wow! I just stumbled on the solution. The screen was black because the brightness came on set all the way down! How dumb is that?

---

### Post by bilkay on 2013-12-26
So I have it installed and so far everything looks fine except for one tiny thing (other than that it starts black): It only boots into windows. Then, to get to ubuntu, I have to go to shutdown, hold down the shift key while clicking on restart, and then selecting ubuntu. There's gotta be a better way.

p.s. Same result with secure boot enabled and disabled.

---

### Post by oldfred on 2013-12-26
If you installed in legacy/CSM/BIOS mode you cannot dual boot from grub, only from UEFI menu or one time boot key if your system auto switches from UEFI to BIOS mode. Some require you to turn on/off CSM or UEFI modes to change.
UEFI and BIOS are not really compatible, once you start booting in one mode you cannot change. So if different modes you cannot dual boot from grub.
Also even if Ubuntu is in UEFI mode, there is a bug on booting Windows in UEFI mode if secure boot is on.

---

### Post by bilkay on 2013-12-26
So you're basically saying I'm screwed? Could I create a usb stick that directly boots to the installed ubuntu on HD?

---

### Post by oldfred on 2013-12-26
No, you just will not be able to use new 3TB drive to boot Windows unless you have UEFI.

Install Windows on a smaller drive with MBR and boot in BIOS mode. You can then install Ubuntu on 3TB drive with gpt partitioning to boot in BIOS mode. To get grub to install correctly on gpt drive, you do need the tiny 1 or 2 MB unformatted partition with the bios_grub flag. If you think drive may get transfered to a new system with UEFI, I would also suggest a 200 to 500MB fat32 partition at the beginning of the drive for future use as efi partition. It could be difficult to add later when drive is full and efi partition should be near or at front of drive.
And since drive is huge, I would keep / (root) as a 25GB partition and then use rest of drive as /home and/or NTFS shared data partition(s).

I used to dual boot Ubuntu on gpt drive and XP on MBR drive without issue.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by bilkay on 2013-12-26
That's an awful lot to understand and digest (and do). I'd be happy if I could install grub on a usb stick and use that when I wanted to boot into ubuntu, and leave it out the very infrequent times I'd want to boot into windows. Everything I've found so far on that subject seems to assume I'd be loading linux from the USB.

---

### Post by oldfred on 2013-12-26
If you do not want to update system and only add a few applications you can run the install with persistence. You cannot change the installer or default boot, but persistence lets you save some info.
Or you can do a full install to one USB flash drive to another flash drive.

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by bilkay on 2013-12-27
What about using elilo "Bootloader for systems using EFI-based firmware"?

---

### Post by oldfred on 2013-12-27
As I understand elilo is just another boot loader like grub. I think it was an earlier boot loader that worked with UEFI before grub worked with UEFI.

I have tried installing DUET which is a UEFI boot loader for Windows even though I do not have Windows. I just wanted to try it. I did get it to install to my flash drive and start to load, but version from rodsbook script is not the newest and did not work with Ubuntu, and it looks like it has not been updated since so many new systems now have UEFI. So not much need anymore.

 Duet - UEFI for BIOS:
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

---

### Post by bilkay on 2013-12-27
Thanks for your replies and have a Happy New Year!

---

