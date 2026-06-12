---
title: "All partitions gone while trying to install Lubuntu"
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by Knutung on 2013-12-22
I hope someone is able to help me with this, because the prospects of loosing my windows partition aren't making me feel optimistic.. :/

A few days ago I installed Kubuntu, dual-booting with Win7 on my Eee1215B. Realizing Kubuntu is a bit heavy on my old netbook, I decided to try Lubuntu today. When I started the installation from the USB stick, I was asked whether I wanted to overwrite the previous Kubuntu installation. I accepted that, not touching any of the partitionin alternatives. Then suddenly, the installation program produced an error message stating that there was an unencrypted swap drive active, and aborted.

Now I am not able to boot anything, and all my partitions are apparently gone... 

I am now accessing the web using a Boot-repair-disk USB-stick that I made as a precaution before the installation, but the standard boot-repair option doesn't do anything for me. It does, however make a **boot info summary:** [http://paste.ubuntu.com/6618196/](http://paste.ubuntu.com/6618196/)

For example, it states that *'According to the info in the boot sector, sdb1 starts at sector 0. But according to the info from fdisk, sdb1 starts at sector 2048', *indicating that the stuff is still there - _I just have to restore the partition information somehow._

Does anyone have a suggestion as to how I can do this?

---

### Post by Knutung on 2013-12-22
I am going to try **testdisk**:
- [https://apps.ubuntu.com/cat/applications/testdisk/](https://apps.ubuntu.com/cat/applications/testdisk/)
- [https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

Still hoping for guidance, though..

---

### Post by Knutung on 2013-12-22
Apparently, I am not able to install testdisk when using the Boot-Repair-Disk USB-stick (I can't add any repositories and I can't find anything using apt-get..)

And the Lubuntu-live-USB suddenly doesn't work. I have no idea what happened there, so the Boot-Repair-Disk is the only access I have to using my computer.. ](*,)

---

### Post by Knutung on 2013-12-22
Would it help to set boot-repair to "Restore MBR"? I do not dare selecting this option without anyone actually recommending it. I do not want to ruin anything more. There is also an option to "Repair file systems", but naturally I am afraid of touching anything...

---

### Post by oldfred on 2013-12-22
Your BootInfo report is showing no installs at all, neither Windows nor Lubuntu. So Boot-Repair cannot fix anything.

BootInfo report is showing the 1GB drive as FAT16?? And as sda. Some BIOS will promote a flash drive to sda and that always messes with install as grub default installs its boot loader to sda which normally is the internal drive. But the normally installer is FAT32 formatted.

You also are showing sdb, the 500GB drive as gpt partitioned. Windows only boots from gpt with UEFI. Ubuntu will boot from a gpt partitioned drive with UEFI or BIOS, but Ubuntu & Windows need to be installed in the same boot mode to easily dual boot.

It could be that your Lubuntu install is in sdb3, but Boot-Repair cannot mount it to see what is inside. It may offer to run fsck which may fix it but I suggest running the full e2fsck from your live installer if you can get it to boot.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb3 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb3
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb3

You also have a sdb2 as ext2? If intended as a separate /boot, it does not show any boot or grub files. Usually better not to have a separate /boot but use a smaller / (root) partition and have /home or a data partition as another partition.

If using testdisk to see if your NTFS partitions may still be found, you need to be in MBR(msdos) not gpt mode?

---

### Post by Knutung on 2013-12-23
Thank you very much for your reply!

> **oldfred said:**
> Your BootInfo report is showing no installs at all, neither Windows nor Lubuntu. So Boot-Repair cannot fix anything.

BootInfo report is showing the 1GB drive as FAT16?? And as sda. Some BIOS will promote a flash drive to sda and that always messes with install as grub default installs its boot loader to sda which normally is the internal drive. But the normally installer is FAT32 formatted.

You also are showing sdb, the 500GB drive as gpt partitioned. Windows only boots from gpt with UEFI. Ubuntu will boot from a gpt partitioned drive with UEFI or BIOS, but Ubuntu & Windows need to be installed in the same boot mode to easily dual boot.

(...)

You also have a sdb2 as ext2? If intended as a separate /boot, it does not show any boot or grub files. Usually better not to have a separate /boot but use a smaller / (root) partition and have /home or a data partition as another partition.



I don't really get this myself. I only have one physical hard drive except for the live-USB, so why this thing report a large sdb, I don't know. Before I started the Lubuntu install, I had the following list of partitions:
[LIST]
[*]an sda1 (Win7 and /boot);
[*]a small sda2 (I believe this was the recovery partition for Windows);
[*]sda3 (for storage), and finally;
[*]an sda4, which was made by reducing the size of sda3 three days ago to install Kubuntu. 
[/LIST]

Here is a bootinfo-report from the Kubuntu-installation just a few days before the Lubuntu-installation (the Kubuntu-installation just booted directly into windows, so I used this to get Grub up and going): [http://paste.ubuntu.com/6613181/](http://paste.ubuntu.com/6613181/)

The strange thing is that the Lubuntu-installation didn't really even get to start before this happened, so I was a bit surprised anything was changed..

> **oldfred said:**
>  It could be that your Lubuntu install is in sdb3, but Boot-Repair cannot mount it to see what is inside. It may offer to run fsck which may fix it but I suggest running the full e2fsck from your live installer if you can get it to boot.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb3 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb3
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb3


I tried these commands, only getting for response that e2fsck can't find the drive, which makes sense, since there is (in theory) no sdb3 here. 

Opening Gparted I get the following list of partitions:
[LIST]
[*]sda1, fat32, 487MB
[*]sda2, ext2, 244MB
[*]sda3, unknown, 465MB
[*]unallocated, 1,02MB
[/LIST]

So I tried the commands, but for other partitions, and I get a similar response for all partitions:
```
lubuntu@lubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda3
e2fsck: Bad magic number in super-block while trying to open /dev/sda3
/dev/sda3: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```



> **oldfred said:**
> 
If using testdisk to see if your NTFS partitions may still be found, you need to be in MBR(msdos) not gpt mode?


I didn't get to run testdisk yesterday, but I'm able to use the live-USB now, so I'll try that today.

I have been trying to set Gparted to "Attempt data rescue" (under "Device" in the menu), but although the disk seems to be spinning, I think it has just stopped working and spends loads of time.. The GUI is all blanked out..

---

### Post by oldfred on 2013-12-23
Your older BootInfo looks like a normal BIOS dual boot With Windows in sda1, I think sda2 is a vendor recovery and an extended partition with your Linux install.

Boot-Repair had these:
 Windows not detected by os-prober on sda1.

   BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
The following packages will be REMOVED:
grub-efi-amd64 grub-efi-amd64-signed
The following NEW packages will be installed:
grub-gfxpayload-lists grub-pc grub-pc-bin

I do not know why os-prober whould not see the Windows boot files. Boot-Repair shows the Windows boot files are there. Normally boot repair might not show them if os-prober does not see them as Windows may have chkdsk flag set after a resize or error or hibernation flag set.

You said older computer but you installed UEFI signed versions of grub? Boot-Repair uninstalled the efi files and installed grub-pc for BIOS boot.

So how did a reinstall overwrite the entire system. If os-prober could not see Windows, did the installer not see Windows? And then only offered to overwrite the entire drive. I always prefer to use Something Else or manual install and with a re-install that seems to be even more important.

Your old BootInfo report shows exact starts & sizes of old partitions, so you can rebuild those partitions. But since data has been overwritten, you will not recover a working system.

---

### Post by Knutung on 2013-12-23
> **oldfred said:**
> Your old BootInfo report shows exact starts & sizes of old partitions, so you can rebuild those partitions. But since data has been overwritten, you will not recover a working system.

It seems you are right. Testdisk did not provide me with any reasonable outcomes.. Thank you for your assistance.

---

