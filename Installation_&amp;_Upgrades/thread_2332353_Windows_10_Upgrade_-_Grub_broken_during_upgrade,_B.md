---
title: "Windows 10 Upgrade - Grub broken during upgrade, Boot Repair does not fix"
date: 2016-07-30
forum: Installation &amp; Upgrades
---

### Post by Andrew F in Australia on 2016-07-30
HI All,

Looking at the forum, it seems as though Windows 10 breaks a lot of grub issues.

Couldn't find anything similar to this one on a search.

I've ran a machine for 10 years on dual boot - Ubuntu 8 I think was where it started.

Just upgraded windows 7 to windows 10 on the machine, now the grub menu is broken (grub rescue prompt)

Downloaded the upgrade fine, installed, rebooted once, fine, logged back  in OK, continued the upgrade, rebooted itself and broke the GRUB menue.


Grub repair does not fix this one.

ls (hd0,msdos1) etc returned an error on each one, didn't seem to find an operating system on any drive ("Filesystem is unknown")

Pastebin link from boot repair
[http://paste.ubuntu.com/21573112/](http://paste.ubuntu.com/21573112/)

Had a look at the GRUB wiki, no success:

Looking at the log, it looks as though there is an issue with the bootmgr.

I tried the steps in here, gave directory errors ("no such file or directory," or /mnt/sys does not exist, etc..):

[http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows) important part below.

```

I never got in trouble by using these instructions:
[https://wiki.ubuntu.com/Grub2#Recover](https://wiki.ubuntu.com/Grub2#Recover) 
  First of all, you must start your system from a live cd. Then
  "**METHOD 3 - CHROOT**
  This method of installation uses the chroot command to gain access to   the broken system's files. Once the chroot command is issued, the   LiveCD treats the broken system's / as its own. Commands run in a  chroot  environment will affect the broken systems filesystems and not  those of  the LiveCD.
  **1)** Boot to the LiveCD Desktop (Ubuntu 9.10 or   later). Please note that the Live CD must be the same as the system you   are fixing - either 32-bit or 64-bit (if not then the chroot will  fail).
  **2)** Open a terminal (Applications > Accessories > Terminal).  
  **3)** Determine your normal system partition - (the switch is a lowercase "L")
  sudo fdisk -l
 If you aren't sure, run  
  df -Th  
  Look for the correct disk size and ext3 or ext4 format.  
  **4)** Mount your normal system partition:
  Substitute the correct partition: sda1, sdb5, etc.  
  sudo mount /dev/sdXX /mnt  
  *Example: sudo mount /dev/sda1 /mnt*  
  **5)** Only if you have a separate boot partition: sdYY is the /boot partition designation (for example sdb3)  
sudo mount /dev/sdYY /mnt/boot  **6)** Mount the critical virtual filesystems:  sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys  **7)** Chroot into your normal system device:  sudo chroot /mnt   **8)** If there is no /boot/grub/grub.cfg or it's not correct, create one using
  update-grub   **9)** Reinstall GRUB 2:
  Substitute the correct device - sda, sdb, etc. Do not specify a partition number.
  grub-install /dev/sdX   **10)** Verify the install (use the correct device, for example sda. Do not specify a partition):  
sudo grub-install --recheck /dev/sdX     **11)** Exit chroot: CTRL-D on keyboard  
  **12)** Unmount virtual filesystems:
  sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys   **13)** If you mounted a separate /boot partition:
  sudo umount /mnt/boot   **14)** Unmount the LiveCD's /usr directory:
  sudo umount /mnt/usr   **15)** Unmount last device:
  sudo umount /mnt   **16)** Reboot. 
sudo reboot "

```

Similar post was this one: [http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)

At the moment, I can't break into it.

Have just checked the bios order as well as hinted at in another post.  No change.

Any and all assistance that anyone could provide would be greatly appreciated.

With best regards,

Andrew F

WIndows 10 has deleted the Linux ext4 partition as well. My backup's a  couple of months old, so I won't lose a lot of information if it's gone.  Separate question, I assume it may be recoverable following the steps  in the linked post below, but initially, I'm just looking at getting a  computer to boot again.
[http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by yancek on 2016-07-30
It looks like the windows upgrade rewrote the partition table and did not include you Ubuntu partition.  Best way to resolve this is with testdisk so read through the step by step tutorial on their site for instructions.
You can see below the start of the Extended partition which would have included Ubuntu.  The space between the start of sdb3 and sdb5 is where your Ubuntu was.

> /dev/sdb3         234,504,190 1,465,147,391 1,230,643,202   5 Extended
/dev/sdb5       1,431,633,920 1,465,147,391    33,513,472  82 Linux swap / Solaris

---

### Post by Andrew F in Australia on 2016-07-30
Thanks yancek

how would I actually get Windows booted up?

I can't get past Grub Rescue.

(or is there a Linux version of testdisk that I can run off a live CD?)

Many thanks for your speedy response,

A

---

### Post by oldfred on 2016-07-31
You can run testdisk from your Ubuntu live installer.
Some also found parted rescue to be easier if just restoring one partition and you know start & end sectors, which you do know from start of extended to start of swap.

       [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[URL="http://ubuntuforums.org/showthread.php?t=2290190"]http://ubuntuforums.org/showthread.php?t=2290190
[/URL]
 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462) 

[URL="http://ubuntuforums.org/showthread.php?t=2290190"]
[/URL] This has been a bug in Windows for many years. Even re-install of Windows 7 or major upgrade, Windows would forget to rewrite Linux partitions to partition table.

With multiple drives often better to have Windows on one drive and Ubuntu on another drive.
You show a new sda 3TB drive, but it does not show if gpt partitioned. It must be gpt, but you can install Ubuntu to boot in either UEFI or BIOS Boot mode from gpt partitioned drives if you have an ESP - efi system partition for UEFI boot and/or bios_grub for BIOS boot.

I started adding both partitions to all new drives & even larger flash drives before I go a newer system with UEFI as I thought I might move drive to a new system that was UEFI.
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Andrew F in Australia on 2016-08-26
Thanks Fred and Yancek.

It turned out that the Windows installation had seriously affected the linux kernel as well.  

Testdisk recovered the partitions, so I could get data back

I ended up rsync-ing off a live CD to get as much data as possible since the last backup, then just reformatting the drive and installing Windows onto it as a brand new install (which still took 3 attempts to get it to work properly.)

Installed Linux (Ubuntu 16.04) onto it today, and the install went fine, but the GRUB menu wasn't installed.  Had to put that on manually with Boot Repair.  

Seems to be working (finally)

Many thanks, 

A

---

