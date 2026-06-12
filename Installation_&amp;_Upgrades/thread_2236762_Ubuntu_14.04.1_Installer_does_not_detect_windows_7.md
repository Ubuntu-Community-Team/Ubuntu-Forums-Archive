---
title: "Ubuntu 14.04.1 Installer does not detect windows 7"
date: 2014-07-28
forum: Installation &amp; Upgrades
---

### Post by user50 on 2014-07-28
I recently did a clean installation of windows 7 onto my computer and now I'm trying to install ubuntu 14.04.1 as a dual-boot from a USB drive. The problem is that ubuntu does not recognize windows 7 during the installation process. Specifically, it states that "The computer has no detected operating systems" and gives me the options to erase the disk and install ubuntu or do something else. Clicking on the "do something else" button brings up a window showing the windows 7 partition (ntfs) on /dev/sda1 and about 500GB of free space, which I was planning to put ubuntu on.

My boot info is here: [http://paste.ubuntu.com/7889578/](http://paste.ubuntu.com/7889578/)

I tried using fixparts, but no success.

Thanks in advance. I don't really know much about linux. If you need more info, let me know.

---

### Post by mastablasta on 2014-07-29
create free unformatted disk space (where you plan to put Ubuntu) using windows disk manager and then try again with the install.

Also is window using dynamic partition? A screenshot from windows disk manager would be helpful.

---

### Post by oldfred on 2014-07-29
It does not look like it is dynamic as fdisk shows SFS not NTFS even thought inside the dynamic it still is NTFS. And it just shows NTFS.

Was drive gpt before. If you ran fixparts and wrote with w the update that would have erased the backup gpt partition table. But if you did not write the change then it may still have gpt data that causes issues.

Otherwise it could be Windows is hibernated or needs chkdsk.
       Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by user50 on 2014-07-29
I wrote the updates with "w" after running fixparts and confirmed that I wanted to overwrite the partition table. I ran chkdsk and it found no errors. I also tried using the windows recovery cd to do startup repair and it found no errors as well. As far as I know, the computer is not hibernated, but I just disabled hibernation completely and will try again.

A screenshot of windows disk manager is attached.

EDIT 1:
Still no luck after disabling hibernation. Attached is also a screenshot from gparted if it helps at all.

---

### Post by user50 on 2014-07-29
I just tried running fixparts again and it gave me the following warning:

"Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes."

Not sure if this is relevant or not. The full output of fixparts is below:

```
ubuntu@ubuntu:~$ sudo fixparts /dev/sda
FixParts 0.8.8

Loading MBR data from /dev/sda

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 3907029168 sectors (1.8 TiB)
MBR disk identifier: 0x65DD4E77
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048   2662402047   primary     Y        Y      0x07

MBR command (? for help): 


```

---

### Post by oldfred on 2014-07-29
All that looks normal and gparted has no little yellow or red warning icons, so it now mounts it. 
Not sure why installer would not see it.

I might just create partitions in gparted and use Something Else to choose / (root), /home and swap and formats.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
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

### Post by user50 on 2014-07-29
So I tried this and now the computer is booting directly inot ubuntu with no option for windows, but windows partition still seems to be there with a boot flag. Gparted screenshot is attached and fdisk -lu output is below. Please help.

```

lab127@lab127-DX4870:~$ sudo fdisk -lu

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x65dd4e77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  2662402047  1331200000    7  HPFS/NTFS/exFAT
/dev/sda2      2662402048  2691698687    14648320   82  Linux swap / Solaris
/dev/sda3      2691700734  3814746111   561522689    5  Extended
/dev/sda5      2691700736  2740527103    24413184   83  Linux
/dev/sda6      2740529152  3814746111   537108480   83  Linux
lab127@lab127-DX4870:~$ 


```

---

### Post by user50 on 2014-07-29
Fixed it. I used the command ```
sudo os-prober
``` which showed there was a windows 7 boot sector on /dev/sda1 followed by ```
[FONT=Ubuntu Mono]sudo update-grub[/FONT]
``` to update grub. Now I get an option on startup to choose which OS to boot into.

Thanks for all the help.

---

### Post by yancek on 2014-07-29
Have you tried booting Ubuntu and running:  sudo update-grub?
Watch the output to see if windows is detected, if so reboot and try.

---

### Post by ramesh5 on 2015-01-31
Somewhat similar issue for me, but on a different node.

I want to remove all the Windows files, partitions and data. Recover the disk space for ubuntu user. Complete details of my post can be seen here.
[http://askubuntu.com/questions/580204/lost-disk-space-after-switching-to-ubuntu-from-windows](http://askubuntu.com/questions/580204/lost-disk-space-after-switching-to-ubuntu-from-windows)

---

### Post by grahammechanical on 2015-01-31
@ramesh5

What you want to do is completely different from the problem that the original poster had. This thread is marked as solved. To get help create a new thread of your own with a thread title that clearly indentifies your request.

Regards.

---

### Post by red19 on 2015-06-15
> **user50 said:**
> I recently did a clean installation of windows 7 onto my computer and now I'm trying to install ubuntu 14.04.1 as a dual-boot from a USB drive. The problem is that ubuntu does not recognize windows 7 during the installation process. Specifically, it states that "The computer has no detected operating systems" and gives me the options to erase the disk and install ubuntu or do something else. Clicking on the "do something else" button brings up a window showing the windows 7 partition (ntfs) on /dev/sda1 and about 500GB of free space, which I was planning to put ubuntu on.

My boot info is here: [http://paste.ubuntu.com/7889578/](http://paste.ubuntu.com/7889578/)

I tried using fixparts, but no success.

Thanks in advance. I don't really know much about linux. If you need more info, let me know.

Hello all, I had the same problem. The problem, at least for me, appears because the BIOS of PC starts the UEFI boot of the usb live install (Ubuntu MATE 14.04.2) and Win 7 use the legacy mode, just tell to BIOS to boot the usb live install in the legacy mode (MBR) and Ubuntu recognize the Windows 7 OS.

Hope this helps.

Cya all,

Red.

---

### Post by kirantalla on 2015-06-19
Nothing happens when I try to use 
sudo os-prober:rolleyes::rolleyes::rolleyes:

---

### Post by oldfred on 2015-06-19
@kirantalla
See post #11, better to start your own thread and post partition info or link to report from Boot-Repair.
Actual command is:
sudo update-grub

and that runs the os-prober as part of its update of grub. Normally we do not run os-prober by itself.

---

