---
title: "No GRUB menu"
date: 2018-07-29
forum: Installation &amp; Upgrades
---

### Post by Olivares on 2018-07-29
I have dual boot Windows (8.1) and Ubuntu. I uninstalled Ubuntu 16.04 on partition sda6 then did an installation of 18.04. As often happens, the GRUB menu disappeared and my PC booted direct into Ubuntu. I then ran boot repair utility. The machine then booted directly into Windows! The boot info script can be viewed here: [https://paste.ubuntu.com/p/DfJnhxvV5J/](https://paste.ubuntu.com/p/DfJnhxvV5J/). Does anybody have any ideas?

---

### Post by gdesilva on 2018-07-29
According to your logs it appears the superblock on sda6 is corrupted - 
"wrong fs type, bad option, bad superblock on /dev/sda6,"

I would boot the system off a LiveCD and try to fix sda6 partition. Check this out for details [https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

Once you get /dev/sda6 fixed then you would need to re-install grub on /dev/sda if you want to get the Grub menu back.

---

### Post by oldfred on 2018-07-29
In addition, you also show Windows is hibernated.
Grub2's os-prober needs to see the NTFS partition to know it is bootable.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Grub only boots working Windows, or Windows that does not need chkdsk nor is hibernated.
And Windows will turn the fast start up/hiberntion back on with updates which may be in back ground and you do not notice it. And then grub will not boot Windows.
So always have the Ubuntu live installer for Ubuntu repairs and a Windows repair/recovery flash drive for Windows repairs.

       
 [http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html](http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html)

---

### Post by Olivares on 2018-07-30
1. Regarding fixing sda6, I ran command dumpe2fs and got the error message: "dumpe2fs: no such file or directory while trying to open /dev/sda6." I tried researching this message and possible remedies with a Google search, but am none the wiser.
2. And regarding Windows being hibernated, the fast start up option was unchecked in control panel, and I also shutdown with the command "shutdown -s -t 00" so I don't understand why boot info says otherwise.

---

### Post by Olivares on 2018-07-30
Apologies. I got the dumpe2fs command wrong. Command executed correctly half an hour ago and file system repaired with the fsck command. I re-ran the boot repair. I get message to unmount partitions befoe proceeding with boot repair. I do this, check that they are unmounted with df -hT, and I get a second message to say there are [still] partitions or drives mounted.

---

### Post by Olivares on 2018-07-30
New boot info created after dumpef2s, fsck processes still shows "wrong fs type, bad option, bad superblock;" see [https://paste.ubuntu.com/p/TZNPc7qWVX/](https://paste.ubuntu.com/p/TZNPc7qWVX/).

---

### Post by oldfred on 2018-07-30
Windows will turn fast start up back on with updates. So even if you originally turned it off, it may have updated?

did you run the full fsck? Should run it on all your ext4 partitions.
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Olivares on 2018-07-31
Once again I ran boot-repair, but this time I ran it off the Ubuntu Live CD, instead of the separate boot repair CD I have. When restarting the PC, it booted into Ubuntu rather than Windows. It also threw up the message "the boot files of Ubuntu 18.04 are far from the start of the disk and your BIOS may not detect them. You may want to retry after creating a boot partition [at the] start of the disk." But as the GParted image below shows, the boot partition _is_ at the start of the disc. 

[IMG]file:///home/barry/Pictures/GParted.png[/IMG]

---

### Post by oldfred on 2018-07-31
Your image is on your system. 
You can just post this:
sudo parted -l

But you also can ignore the far from start of disk warning. 
It is just a warning and really only applies to old IDE drives with BIOS installs. Those often had a 137GB limit on where on drive all boot files had to be. Not seen issue with any newer UEFI system. But some USB drives may have similar type issue, so then often better to have smaller / (root) at beginning of drive and large /home for  rest.

---

### Post by Olivares on 2018-07-31
I thought there were supposed to be grub files at /home/etc/default/ but all I can see there is: /etc/pki and /etc/yum.repos.d. Here is output from sudo parted -l:

[FONT=courier new]barry@barry-desktop:~$ sudo parted -l[/FONT]
[FONT=courier new][sudo] password for barry: [/FONT]
[FONT=courier new]Model: ATA ST1000DM003-1CH1 (scsi)[/FONT]
[FONT=courier new]Disk /dev/sda: 1000GB[/FONT]
[FONT=courier new]Sector size (logical/physical): 512B/4096B[/FONT]
[FONT=courier new]Partition Table: msdos[/FONT]
[FONT=courier new]Disk Flags: [/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Number  Start   End     Size    Type      File system     Flags[/FONT]
[FONT=courier new] 4      1049kB  1075MB  1074MB  primary   ext4[/FONT]
[FONT=courier new] 1      1075MB  1442MB  367MB   primary   ntfs[/FONT]
[FONT=courier new] 2      1442MB  462GB   461GB   primary   ntfs            boot[/FONT]
[FONT=courier new] 3      462GB   1000GB  538GB   extended[/FONT]
[FONT=courier new] 5      462GB   513GB   51.2GB  logical   ntfs[/FONT]
[FONT=courier new] 6      513GB   984GB   470GB   logical   ext4[/FONT]
[FONT=courier new] 7      984GB   1000GB  16.4GB  logical   linux-swap(v1)

Really appreciate the patience and willingness to help.[/FONT]

---

### Post by oldfred on 2018-08-01
From Boot-Repair you can do a full uninstall/reinstall of grub & will will add any missing files, if that is a problem.

Since Windows 8 in BIOS boot mode, be sure to create a Windows repair flash drive.
With BIOS you can only have one boot loader in MBR, and grub then only will boot working Windows. But if Windows is shutdown incorrectly and needs chkdsk or is hibernated/fast start turned back on, then you have to directly boot Windows. Then use Windows to temporarily restore boot loader to MBR, fix Windows, then use Boot-Repair to restore grub to MBR.

Newer Windows 8 or 10 from vendor is required by Microsoft to be UEFI with gpt partitioning. Then both Windows & Ubuntu have boot files in ESP - efi system partition and can both can be booted from UEFI directly.

---

