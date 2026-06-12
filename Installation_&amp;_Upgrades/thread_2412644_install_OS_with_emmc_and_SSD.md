---
title: "install OS with emmc and SSD"
date: 2019-02-15
forum: Installation &amp; Upgrades
---

### Post by windowsfree on 2019-02-15
Hello,

Looking for assistance with partitioning.
[COLOR=#333333][FONT=&amp]I was able to obtain an Acer Swift 1 laptop. It had MS Windows installed. [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp][Windows 10 Home in S mode[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Intel® Pentium® Silver N5000 processor Quad-core 1.10 GHz[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Intel® UHD Graphics 605 with Shared Memory[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]14" Full HD (1920 x 1080) 16:9 IPS[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]4 GB, DDR4 SDRAM[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]64 GB Flash Memory][/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I added a 256gig SSD. [Samsung 860 EVO 250GB M.2 SATA Internal SSD (MZ-N6E250BW)][/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I used Samsung software to move the OS from the emmc to the SSD.

(sdb is the live linux USB disk )

[/FONT][/COLOR][ATTACH=CONFIG]282528[/ATTACH]

I want to install Linux as the only OS.  I want the install to go to the SSD.  I would probably use the EMMC for storage if needed.

Can anyone suggest a good partitioning scheme?

Thank you.

---

### Post by oldfred on 2019-02-15
This may be interesting. 
Ubuntu's grub only installs to the first drive it sees. I only have SATA ports and it always installs to sda. And users with MMC or NVMe drives also seem to work, not sure if users have multiple MMC or NVMe drives what grub does.
So not sure if grub will correctly install to ssd, or want to install to MMC drive. If installed to MMC drive we either would manually reinstall forcing grub into sda or use Boot-Repair. Or manually copy files from ESP on MMC to ESP on SSD drive.

Default install is just / (root) on ext4 partition. If UEFI boot it also has to have the ESP - efi system partition with gpt partitioning. But if you have Windows in UEFI boot mode, you already have the ESP (only one per drive).
Do you want separate /home partition (ext4)? Or perhaps a shared data partition that would be NTFS.

Any issues of duplicate UUIDs? Post this just to check. Some tools image copy and may copy UUID and that is not allowed. Assumption is you will remove old drive or repartition it.
Post this in code tags to preserve formatting, so we can compare UUIDs. Do not use screen shots for terminal output. just copy & paste. Easy to add code tags in forum's advanced editor and # icon.

       lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

 Acer Swift 3
[https://ubuntuforums.org/showthread.php?t=2370998](https://ubuntuforums.org/showthread.php?t=2370998)
[https://askubuntu.com/questions/1047065/fail-to-install-ubuntu-18-04-from-usb-to-a-brand-new-acer-swift-1](https://askubuntu.com/questions/1047065/fail-to-install-ubuntu-18-04-from-usb-to-a-brand-new-acer-swift-1)

---

### Post by qyot27 on 2019-02-15
I have a Byte3 (which comes with an eMMC for storage, as here), added a 512GB SSD, moved Windows to the SSD, and then installed Ubuntu beside it on the SSD as a dual boot.  Any consideration of dual booting (or simply overriding the partition locations, as per an SSD) here requires using the manual partitioning option in the installer.  Other than that, it didn't really require anything special¹.

The SSD needs an EFI partition (or maybe not, it might've just been copied over when the other Windows partitions were migrated, but I'm pretty sure it's still necessary).  IIRC, Grub works just fine installed to the SSD.  The eMMC also needs an EFI partition, because I can't quite remember whether that was a hard requirement due to the eMMC drive being the first storage the device itself looks at - you know, since it's embedded in the motherboard.

¹Where this can potentially get hairy is if we're dealing with 32-bit UEFI firmware, like when I had Ubuntu booting from an external USB drive with the original Quantum Byte (Windows stayed on the eMMC storage on that device).  64-bit Linux distros are generally fine with being installed/boot from such devices since the kernel has supported mixed-mode booting for a few years now, but it requires some finagling with Grub and you may have to get comfortable issuing the boot commands to Grub yourself.

---

### Post by windowsfree on 2019-02-15
Thank you for the reply, so other than having EFI on both the emmc and ssd, I should just put / on the SSD.

If I mis-understood, please reply, I would like to do this in 2 days.

Thank you,

---

### Post by oldfred on 2019-02-15
Yes, / should be on SSD.

I like to use smaller / of 25 or 30 GB and then large partition for data where I have my folder.
If not allocating a lot of space for Ubuntu, the having just / for all the space is ok.

If a newer user and wanting to separate system from data,  having separate /home is easier to configure as that auto configures mount in fstab and ownership & permissions. If just a data partition you have to do all that yourself.

---

### Post by windowsfree on 2019-02-16
I removed all but the EFI partitionn from both the EMMC and SSD and installed.  The installer asked where  to install so I pointed it to the SSD drive and everything installed without issue.

Thank you to all who replied.

---

### Post by oldfred on 2019-02-16
That is great.

Did grub install to ESP on MMC or SSD?
cat /etc/fstab
lsblk -f

---

### Post by windowsfree on 2019-02-16
bob@Acer1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=fbbbd1ae-0d51-4326-a53a-7d261e5712d2 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/mmcblk0p1 during installation
UUID=DA2E-B3E2  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
bob@Acer1:~$ lsblk -f
NAME         FSTYPE LABEL UUID                                 MOUNTPOINT
loop0                                                          
&#9492;&#9472;cryptswap1 swap         b09e62d2-6209-40d6-b0ba-35072c0bad2a [SWAP]
sda                                                            
&#9500;&#9472;sda1       vfat         B3F7-41C5                            
&#9492;&#9472;sda2       ext4         fbbbd1ae-0d51-4326-a53a-7d261e5712d2 /
mmcblk0                                                        
&#9500;&#9472;mmcblk0p1  vfat   ESP   DA2E-B3E2                            /boot/efi
&#9492;&#9472;mmcblk0p2  ext4         fb3d0ea7-9852-4221-934d-7a24ce46a5e3 
mmcblk0boot0                                                   
mmcblk0boot1

---

### Post by oldfred on 2019-02-16
I see it is using your ESP on the mmc device.
That is ok, unless you want to change it.

---

