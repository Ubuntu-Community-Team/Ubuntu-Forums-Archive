---
title: "Ubuntu 22.04 suddenly won't boot"
date: 2023-07-07
forum: Installation &amp; Upgrades
---

### Post by mvinsky on 2023-07-07
Ran some updates yesterday and rebooted with no problems. I turned off the computer because it said updates couldn't be installed because there wasn't enough disk space (~20GB). I didn't realize I had made the partition too small when I installed the OS. I just so happened to have a couple of 2TB NVME SSD to install so I turned off the computer and tried to edit the partitions using a live copy of Ubuntu. Turned out I couldn't resize the partition because there isn't room on either side of it to expand so I didn't make any changes. I thought I would install the new SSD's first to backup the system before I make any changes. I installed the new SSD's and when I tried to boot it went to a dell diagnostic mode, said it could't find the OS and turned the computer off.

I pulled the new SSD's out and that didn't help, so I put them back in for now. I have no idea what went wrong, can anyone help? I have the log created by boot-repair which I can send as text, but its about 8 pages. I'm including the link for it here.

[https://paste.ubuntu.com/p/2NZTfSNY9Z/](https://paste.ubuntu.com/p/2NZTfSNY9Z/)

When I try to run the repair using boot-repair it says "GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again."

I have no idea what this means.

[ATTACH]292454[/ATTACH]

---

### Post by MAFoElffen on 2023-07-07
What version of Windows is installed? When was it originally installed?

When was Ubuntu originally installed?

What brand and model is this computer?

Looking at this report and I see some big problems. Too many to post in just a short post. Am currently writing what I see in an editor so I can post that. 

Go into your BIOS Settings and tell me which boot mode this is set to: UEFI or Legacy/CSM? Then tell me what disk the primary boot order is set to... While there, disable "SecureBoot"

---

### Post by MAFoElffen on 2023-07-07
Reading your reports. While I'm doing that...

First, go into your BIOS settings. Ensure the Boot mode is set to UEFI, with SecureBoot disabled.

Line #89 says it is set to 'enabled'.
```

SecureBoot enabled.

```
Okay... I looked at your report. There are some problems (now).

Lines 93-94
```

Boot0000* ubuntu    HD(1,GPT,83120407-83cc-471f-84d9-a4bb649a8341,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Linux Firmware Updater    HD(1,GPT,83120407-83cc-471f-84d9-a4bb649a8341,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)\.f.w.u.p.d.x.6.4...e.f.i...

```
But,
```

# fstab showing root, Lines 215-216:
# / was on /dev/nvme0n1p1 during installation
UUID=9da9b39b-558e-4b6f-af56-67394b9e94c3 /               ext4    errors=remount-ro 0       1
# Lines 198-203
=================== nvme0n1p1/boot/grub/grub.cfg (filtered) ====================

Ubuntu   9da9b39b-558e-4b6f-af56-67394b9e94c3
Ubuntu, with Linux 5.19.0-46-generic   9da9b39b-558e-4b6f-af56-67394b9e94c3
Ubuntu, with Linux 5.19.0-45-generic   9da9b39b-558e-4b6f-af56-67394b9e94c3
#Lines 182-185
nvme0n1                                                                                                    
&#9500;&#9472;nvme0n1p1 ext4     9da9b39b-558e-4b6f-af56-67394b9e94c3 7f73a78f-ac5b-4e51-84be-eb9990712ee5              
&#9500;&#9472;nvme0n1p2 swap     eb614349-49e9-4194-bb4a-c0f4096af724 5296fc18-c07f-41ea-9b5c-902808262d14              
&#9492;&#9472;nvme0n1p3 ext4     f11c1d8a-098e-4cb4-9596-9910e66de233 34365703-c714-4f55-a29c-222e950aedb3              

```
So the EFI entries are wrong for the UUID of where it is located... (compared the UUID's of nvme0np1, 9da9b39b-558e-4b6f-af56-67394b9e94c3)

But for that partition:
# But lines 189-190
```

                           Avail Use% Mounted on
/dev/nvme0n1p1                 0  95% /mnt/boot-sav/nvme0n1p1

```
Says that partition is "FULL".

Then for the only (suspected by me) ESP on the system
```

# Lines 175-177
nvme2n1                                                                                                    
&#9500;&#9472;nvme2n1p1 vfat     87A1-8FC0                            41b29006-19c7-4769-9ed0-e36c3337757c              Microsoft reserved partition
&#9492;&#9472;nvme2n1p2 ext4     a75eed71-ac40-415a-922a-115d2ed6a3be 05ffd5d3-7493-456f-83d3-8ce9b3378e32              WD_Blue1TB

```
That partition is not mentioned anywhere in the fstab, rather
```

# Lines 217-218
# /boot/efi was on /dev/sda1 during installation
UUID=DB55-20A2  /boot/efi       vfat    umask=0077      0       1

```
/dev/sda1 that the comment in /dev/nvme0np1/etc/fstab refers to doesn't exist on your system, nor does UUID=DB55-20A2... The current /dev/sda is a LiveUSB Ubuntu Install media, right?

That is why this:
```

# Line 115
nvme0n1p1    : isnotESP,    fstab-has-bad-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

```

*** Nothing on your system has a partiton with an ESP flag.

Somewhere in time, someone tried to install things as MBR partitioned, 
```

# Line 5-12
 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/nvme2n1.
 => No boot loader is installed in the MBR of /dev/nvme3n1.
 => No boot loader is installed in the MBR of /dev/nvme4n1.
 => No boot loader is installed in the MBR of /dev/nvme5n1.
 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:

```
but Grub will not boot a GPT partitioned disk, without a bios_boot partition, which it does have. So that was not how it was running.

The recommended repair will not work without some major changes:
```

# Lines 284-303
Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge (in order to remove grub-efi) and reinstall the grub2 of
nvme0n1p1 into the MBR of nvme0n1.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s

Blockers in case of suggested repair: __________________________________________

 GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

Confirmation request before suggested repair: __________________________________

The boot of your PC is in EFI mode, but no ESP partition was detected. You may want to retry after creating a ESP partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Are you sure you want to continue anyway?

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your BIOS boot on nvme0n1 (Samsung SSD 980 1TB) disk!
The boot of your PC is in UEFI mode. You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode.


```

*** This post is long and does not contain a recommendation for a repair yet. I will post that separately...

---

### Post by MAFoElffen on 2023-07-07
First, from the Ubuntu LiveUSB that you are booted from, from "try" > open a terminal...
```

sudo mkdir /mnt/esp_test
sudo mount UUID=87A1-8FC0 /mnt/esp_test

```
Post the output of this in a post, within CODE Tags
```

ls -lah /mnt/esp_test/*
sudo sgisk -p /dev/nvme2n1p1

```

---

### Post by mvinsky on 2023-07-10
No version of windows is installed.

Ubuntu 22.04 was installed in March 2023.

This is a Dell Precision 7920.

Boot mode is currently UEFI with SecureBoot enabled. I did disable SecureBoot it to try running Boot-Repair off a USB but it seemed to hang so I just restarted and enabled SureBoot. I'm currently running Ubuntu off a USB to try and troubleshoot. I'm wondering if a fresh install would be better.

I don't have access to the computer today but I hope to work on it Wednesday. I'll let you know what happens, and thanks for all the support!

---

### Post by mvinsky on 2023-07-12
Hey there, I tried what you said but it doesn't seem to work. So long as I don't reboot the computer I can connect to it remotely for the time being, so I won't change the secure boot options right now.

ubuntu@ubuntu:~$ sudo mkdir /mnt/esp_test
ubuntu@ubuntu:~$ sudo mount UUID=87A1-8FC0 /mnt/esp_test
ubuntu@ubuntu:~$ ls -lah /mnt/esp_test/*
ls: cannot access '/mnt/esp_test/*': No such file or directory
ubuntu@ubuntu:~$ sudo sgisk -p /dev/nvme2n1p1



ubuntu@ubuntu:~$ sudo sgisk -p /dev/nvme2n1p1
sudo: sgisk: command not found

Also, I think the one hard drive with the windows partition was an attempt to install a virtual machine but I'd need to look into that.


Alternatively I could install ubuntu on a different drive and start over. I just need to transfer the home accounts over.

---

### Post by mvinsky on 2023-07-12
Just tried something different. 

ls -lah /mnt/esp_test/
total 512
drwxr-xr-x 2 root root 512 Jan  1  1970 .
drwxr-xr-x 1 root root 100 Jul 12 19:33 

Also found the typo in the "sgdisk" command

***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory.
***************************************************************


Disk /dev/nvme2n1p1: 262144 sectors, 128.0 MiB
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): A7A4D494-6565-401B-946C-B582ABDB7020
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 262110
Partitions will be aligned on 2048-sector boundaries
Total free space is 262077 sectors (128.0 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name

What now?

---

### Post by MAFoElffen on 2023-07-14
Sorry. I did have a typo there:
```

sudo sgdisk /dev/nvme2n1

```

---

### Post by mvinsky on 2023-07-18
Right, so what now? Should I reboot the computer or are there more problems to fix? I'll be rebooting it remotely so if the problem isn't fixed I won't be able to get back in.

I think the issue is the partition for the root directory is 20GB and its not enough space. I swear I followed an online guide to setting up the partition sizes but obviously 20GB isn't enough. Thoughts?

---

### Post by MAFoElffen on 2023-07-18
I had a typo in that post, which I corrected. But since I corrected it, you still are using the same... Please do:
```

sudo sgdisk -p /dev/nvme2n1

```
The reason I need to see that out from that command is to see the partition table type and the partition type codes...

After that, also while booted from the LiveUSB, your root partition is full, and will need to have some room, even to be able to make a repair. Some the places you could make room, is in /tmp (you can delete all from that directory), /var/log/ (all that contain ".3" or higher in the file name), then whatever you choose from your Home folder...


While you have that partition mounted, I need to see the contents of file /etc/fstab... That was not in that report.

The reason I need to see that information, it to give you instructions to be able to mount and chroot into your install system so that you can clean up some things, like purge some some old contents from journalctl, and to be able to purge and reinstall your boot loader.

---

### Post by mvinsky on 2023-07-18
Sorry, I thought the correction was to "sgdisk" I missed that the hard disk had changed to. Here you go:

```
ubuntu@ubuntu:/$ sudo sgdisk -p /dev/nvme2n1
Disk /dev/nvme2n1: 1953525168 sectors, 931.5 GiB
Model: Samsung SSD 970 EVO 1TB
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 970AEE5C-A4AF-400F-AEE4-1E0D43CCAECB
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 3437 sectors (1.7 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved ...
   2          264192      1953523711   931.4 GiB   0700  WD_Blue1TB



```

This hard drive might have a microsoft partition on it because I was trying to set up a virtual machine to run windows 10. If you could tell me how to mount the OS hard drive to access the fstab file that would be a big help.

---

### Post by MAFoElffen on 2023-07-18
Dang. That is worse than i expected...

Please do:
```

sudo lsblk -e7 -o, name. label,size,fstype,fsuse%,UUID

```
Do tell... please explain this statement further:
[quote=mvinsky]
This hard drive might have a microsoft partition on it because I was trying to set up a virtual machine to run windows 10
[/quote]
Because, initially, without further investigation, what I see there may be toast.

And did you remove an SSD or SATA drive since your original install of Ubuntu? Because the fstab says it originally used an EFI mounted from /dev/sda
```

# /boot/efi was on /dev/sda1 during installation

```

---

### Post by MAFoElffen on 2023-07-18
You PM'ed me, mentioning that you might go with a re-install if that was quicker...

First, when did you originally install this? Do you have good backups?

You need this for work... Tell me about the Virtual machine venture and what goals you have with this machine. Meaning, what kinds of things do you need to do?

It may be faster to reinstall Ubuntu... With all the things I see wrong with this existing installation. What is would like to know is what things do you need to recovery from what is there, and what is it's job, so we can recommend how to install this in a way that will prevent this from happening to you again...

Or if you need to recover what is there, which would take quite some work.

That is your main two options.

Next, is... I work nights = Swing shift. And my timezone is UTC/GMT -8. I have more time before I go to work, than after. After for me is 2am. I leave for work at 1:30pm my time.

If you can work around that, we can forge ahead with a plan. I will just post instructions for you to follow, then wait for your response with how they went, or if there were a problem.

---

### Post by MAFoElffen on 2023-07-18
What I see is 9TB of storage on 6 NVMe drives, with a clean slate to plan out how to manage that storage wisely... This came about because the original plan faced running out of space for the OS partition container... And something happened to a drive, when you tried to install a VM of Windows.

What VM Hosting system did you use? It took some work to overwrite a physical disk while installing a VM, so I would like to ensure that doesn't happen to you again.

That, and the orginal system said it was installed with UEFI, but parts of that original installation are "missing".

---

### Post by MAFoElffen on 2023-07-18
I see the original install here:
```

Disk nvme0n1: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: D891D22A-BA54-4D69-BEDC-1C147D56F06E
              Start        End    Sectors   Size Type
nvme0n1p1 289062912  328124415   39061504  18.6G Linux filesystem
nvme0n1p2  39063552  289062911  249999360 119.2G Linux swap
nvme0n1p3 328124416 1953523711 1625399296 775.1G Linux filesystem

```
What is missing is the EFI partition with it's ESP, and boot flags.

I can see that your second drive was your backup drive (/devnvme1n1), then your third drive is the one that got wacked (dev/nvme2n1)... 

What I am about to propose is risky, so we are going to take a backup image of /dev/nvme0n1 over your 3rd disk (/dev/ncme2n1).

In a terminal from the LiveUSB, do
```

sudo dd if=/dev/nmve0n1 of=/dev/nvme2n1 bs=64K conv=noerror,sync

```
That disk got wacked, so why not put it to good use, right? Wait for that to finish...

After it finishes, then start GParted from the LiveUSB... For /dev/nvme0n1... Shrink /dev/nvme0n1p2 to from 119G to twice the size of your system RAM. 119G is way too big!!! That will give you room to expand your system partition to Max minus 1GiB. 

Why minus 1 GiB? Because you are going to leave room for a new EFI partition... Grow it to that size, while leaving 1GiB ahead of it (1000MiB).

After that is through, then add a new partition in from of it, formatted with Fat32, with a lable of "EFI". After that is created, add flags, ESP and boot. Change the partition of nvme0n1 to ROOT. Change the partition label of nvme0n1p2 to SWAP and nvme0n1 to HOME (or label it to makes sense with what is there). Make sure all the drives have GPT partition tables. If not stop there and tell me which ones do not...

After that is done, and all things are applied... Exit GPARTED. note what the new partition id is (most likely will be /dev/nvme0n1p4)

Then in a terminal you are going to mount and chroot into the installed system
```

sudo su -
lsblk -e7 -o name,label,size,fstype,UUID

```
Cut and paste this output to an editor...

Then do:
```

mount /dev/nvme0n1p1 /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
cd /mnt
chroot /mnt /bin/bash --login

nano /etc/fstab

```
Post the contents of that file...

---

### Post by MAFoElffen on 2023-07-18
From there, if all went well to that point, then I will give you instructions to purge the old Grub, and to install the new, while populating the new EFI partition.

---

### Post by mvinsky on 2023-07-18
I'll answer everything in order.

> ubuntu@ubuntu:/etc$ sudo lsblk -e7 -o, name. label,size,fstype,fsuse%,UUID
lsblk: unknown column: ,


I was trying to set up a virtual machine using VMWARE player on one of the hard drives because there is a program that only runs in windows we wanted to run on this machine because it has more RAM than a typical desktop. I wasn't able to get it running because of some issue with the video card. I recently found the correct drivers for the card but haven't gone back to see if the virtual machine will install properly now. If it's too complicated we don't need to run a virtual machine.

> [COLOR=#000000]And did you remove an SSD or SATA drive since your original install of Ubuntu? Because the fstab says it originally used an EFI mounted from /dev/sda[/COLOR]

Yes I removed an old SATA drive. I discovered the OS (18.04) was installed ordinally on a 2.5" 7200RPM HDD and the system was very slow. I installed a new copy of Ubuntu 22.04 on a NVME SSD, re-created the user accounts,  and copied the home directories to the new OS. I didn't realize they didn't have the correct read write permissions (I believe this might have been to a reconstruction of the file system on the old HDD which had crashed) so I played around with the file system to try and fix before I found the permissions were incorrect. This may have contributed to some of the issues you are seeing.

> [COLOR=#000000]First, when did you originally install this? Do you have good backups?[/COLOR]

I installed this in April but I don't have good backups. 3 of the hard drives you see (2TB) are new and I was planning on creating automatic backups when this problem happened. 

> [COLOR=#000000]t may be faster to reinstall Ubuntu... With all the things I see wrong with this existing installation. What is would like to know is what things do you need to recovery from what is there, and what is it's job, so we can recommend how to install this in a way that will prevent this from happening to you again...[/COLOR]

[COLOR=#000000]Or if you need to recover what is there, which would take quite some work.[/COLOR]

[COLOR=#000000]That is your main two options.[/COLOR]

[COLOR=#000000]Next, is... I work nights = Swing shift. And my timezone is UTC/GMT -8. I have more time before I go to work, than after. After for me is 2am. I leave for work at 1:30pm my time.[/COLOR]

[COLOR=#000000]If you can work around that, we can forge ahead with a plan. I will just post instructions for you to follow, then wait for your response with how they went, or if there were a problem.[/COLOR]

I'm MDT so we could chat before you leave for work as that is my afternoon here. However if we can do it with just instructions that might be better use of our time.

> ubuntu@ubuntu:/$ sudo dd if=/dev/nmve0n1 of=/dev/nvme2n1 bs=64K conv=noerror,sync
dd: failed to open '/dev/nmve0n1': No such file or directory


Do we have to mount it first?

> [COLOR=#000000]Shrink /dev/nvme0n1p2 to from 119G to twice the size of your system RAM. 119G is way too big!!![/COLOR]

Maybe that is my issue. I seem to recall reading advice on how big to make that partition based on the amount of RAM. This system has 128 GB of RAM, so how big should the partition be?

---

### Post by MAFoElffen on 2023-07-19
This is my own current personal server:
```

mafoelffen@Mikes-B460M:~$ lsblk -e7 -o name,label,size,fstype
NAME        LABEL      SIZE FSTYPE
sda                    1.8T 
&#9492;&#9472;sda1      datapool   1.8T zfs_member
sdb                    1.8T 
&#9492;&#9472;sdb1      datapool   1.8T zfs_member
sdc                    1.8T 
&#9492;&#9472;sdc1      datapool   1.8T zfs_member
sdd                  476.9G 
&#9500;&#9472;sdd1                  16M ext4
&#9500;&#9472;sdd2               476.3G ntfs
&#9492;&#9472;sdd3                 607M ntfs
sde                    1.8T 
&#9492;&#9472;sde1      datapool   1.8T zfs_member
sdf                    1.8T 
&#9492;&#9472;sdf1      datapool   1.8T zfs_member
nvme0n1                1.8T 
&#9492;&#9472;nvme0n1p1 kpool      1.8T zfs_member
nvme1n1                1.8T 
&#9492;&#9472;nvme1n1p1 kpool      1.8T zfs_member
nvme2n1                1.8T 
&#9492;&#9472;nvme2n1p1 kpool      1.8T zfs_member
nvme3n1                1.8T 
&#9492;&#9472;nvme3n1p1 kpool      1.8T zfs_member
nvme4n1              931.5G 
&#9500;&#9472;nvme4n1p1            512M vfat
&#9500;&#9472;nvme4n1p2              2G swap
&#9500;&#9472;nvme4n1p3 bpool        2G zfs_member
&#9492;&#9472;nvme4n1p4 rpool      927G zfs_member
nvme6n1                1.8T 
&#9492;&#9472;nvme6n1p1 datapool  1000G zfs_member
nvme5n1     datapool   1.8T zfs_member
&#9500;&#9472;nvme5n1p1            1.3T zfs_member
&#9492;&#9472;nvme5n1p2 datapool    10G zfs_member

mafoelffen@Mikes-B460M:~$ free
               total        used        free      shared  buff/cache   available
Mem:       131757384    85367752    44667280      446668     1722352    44735888
Swap:        2097148           0     2097148

```
You do not have it too big based on your memory for a desktop... It could be 128GB to 256GB, but you said server, so could be 0GB to 128GB. Server is okay not to have a swap, though, I like to have at least some buffer, You can see my server above. Is is 128GB RAM, and has a swap of 2GB. I am not worried about it running out of memory, Since it is a Server, I have it set not to be able to suspend or go to sleep.

You need some space near your OS partitions, so can afford to give up some from your swap. I would maybe shrink it to 64BG, give 1GB as an EFI partition, and the rest to your root partition.

When you are provisioning a VM in VMware Player, you could give a VM Guest a wholw raw disk, but it is more customary to give it a VM disk that is really just a virtual disk file *.vmdk). VMware player is a Type 2 hypervisor. I used to use VMware player, and virtualbox over a decade ago.  Why not Why not use KVM?

That same server of mine, is mainly for running KVM guests as a test-suite to test OS'es (I beta test for Ubuntu, Windows/Windows Server Insider & VMware vSphere(, and test my code Ubuntu 'system-info' Script & the Ama-Gi Project) on differing OS'es
```

mafoelffen@Mikes-B460M:~$ sudo zfs list
[sudo] password for mafoelffen: 
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              293M  1.46G       96K  /boot
bpool/BOOT                                         291M  1.46G       96K  none
bpool/BOOT/ubuntu_2cwpns                           291M  1.46G      291M  /boot
datapool                                           907G  3.84T      307K  /data
datapool/DATA                                      907G  3.84T      307K  none
datapool/DATA/ubuntu_2cwpns                        907G  3.84T     10.0G  /data
datapool/DATA/ubuntu_2cwpns/ISO                    398G  3.84T      398G  /data/ISO
datapool/DATA/ubuntu_2cwpns/KVM-VM                 499G  3.84T      499G  /data/KVM-VM
kpool                                             1.56T  1.85T      279K  /KVM_Pool
kpool/KVM                                         1.56T  1.85T      279K  none
kpool/KVM/ubuntu_2cwpns                           1.56T  1.85T     1.56T  /KVM_Pool
rpool                                             16.0G   876G       96K  /
rpool/ROOT                                        14.0G   876G       96K  none
rpool/ROOT/ubuntu_2cwpns                          14.0G   876G     7.05G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   876G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   876G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   876G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      6.97G   876G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   876G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  6.73G   876G     6.58G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   876G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    180K   876G      180K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt               113M   876G      113M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             46.1M   876G     46.1M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   241M   876G      241M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   876G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.48M   876G     1.48M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   876G      120K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   876G       96K  /var/www
rpool/USERDATA                                    1.93G   876G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  1.93G   876G     1.93G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        2.49M   876G     2.49M  /root

mafoelffen@Mikes-B460M:~$ virsh list --all
 Id   Name                          State
----------------------------------------------
 26   ubuntu22.04                   running
 35   zentyal-20.04.6-test01        running
 37   lvm-tes-22.04-svr1            running
 -    btrfs-01                      shut off
 -    console01                     shut off
 -    fedora37                      shut off
 -    fedora38                      shut off
 -    freebsd13.1                   shut off
 -    iso-tester-01                 shut off
 -    kaisenrollingrino-23.04-03    shut off
 -    kaisenrollingrino22.04-1      shut off
 -    linux2020-2                   shut off
 -    lunar-efi-01                  shut off
 -    lunar-lander-00               shut off
 -    lunar-lander-01               shut off
 -    lunar-lander-01-01            shut off
 -    lunar-lander-04               shut off
 -    lunar-lander-05               shut off
 -    lunar-lander-07               shut off
 -    lunar-lander-07-01            shut off
 -    lunar-lander-08               shut off
 -    lunar-lander-10               shut off
 -    lunar-lander-zfs              shut off
 -    lunar-server-01               shut off
 -    lunar-server-03               shut off
 -    lunar-server-04               shut off
 -    lunar-server-06               shut off
 -    lunar-server-22.04-zfs        shut off
 -    lunar-server-cloudimg-amd64   shut off
 -    lunar-server-lightvnc         shut off
 -    lunar-server-template         shut off
 -    lunar-server-zfs-23.04        shut off
 -    lunar23.04-2                  shut off
 -    lunar23.04-3                  shut off
 -    penryn-01                     shut off
 -    proxmox-7.3-1                 shut off
 -    prt-003-01-1604               shut off
 -    prt-003-02                    shut off
 -    prt-003-02-1604               shut off
 -    prt_001                       shut off
 -    prt_002                       shut off
 -    risc64-01                     shut off
 -    rollingrino22.04-1            shut off
 -    solaris11                     shut off
 -    tiny11-01                     shut off
 -    ubuntu-core22-20221218        shut off
 -    ubuntu-guest                  shut off
 -    ubuntu-server-22.04.2         shut off
 -    ubuntu14.04                   shut off
 -    ubuntu14.04-2                 shut off
 -    ubuntu14.04-3                 shut off
 -    ubuntu16.04                   shut off
 -    ubuntu18.04                   shut off
 -    ubuntu2-lvm2-luks-00          shut off
 -    ubuntu20.04                   shut off
 -    ubuntu20.04-2                 shut off
 -    ubuntu20.04-s390x-2           shut off
 -    ubuntu22.04-10                shut off
 -    ubuntu22.04-11                shut off
 -    ubuntu22.04-12                shut off
 -    ubuntu22.04-13                shut off
 -    ubuntu22.04-14                shut off
 -    ubuntu22.04-2                 shut off
 -    ubuntu22.04-3                 shut off
 -    ubuntu22.04-4                 shut off
 -    ubuntu22.04-5                 shut off
 -    ubuntu22.04-6                 shut off
 -    ubuntu22.04-7                 shut off
 -    ubuntu22.04-8                 shut off
 -    ubuntu22.04-9                 shut off
 -    ubuntu22.04.2-xrdp-test       shut off
 -    ubuntu23.04-4-zfs-luks2       shut off
[COLOR=#ff0000] -    win11-RMS                     shut off
 -    win2k22                       shut off
[/COLOR] -    xubuntu20.04-2                shut off
 -    xubuntu22.04-01               shut off
 -    Zentyal-22.04-test            shut off

```
Highlighted in Red are Windows 11 Desktop and Windows 2k22 Server Guests... All of my KVM Guests are stored in 2 ZFS RAIDz2 storage pools.

If you are wanting to do VM's and want to do a backup stategy with the ability to do snapshots, I would recommend learning about LVM2 and/or ZFS.

You do not need to mount the drive to write to it via dd. You would be writing to it bit-by-bit, including the partition table, and the partitions. You would have a mirror image copy to fall back to... For the just-in-cases.

---

### Post by mvinsky on 2023-07-19
I realized there was a typo in the command and fixed it myself. I'll try to pay closer attention to that but as you can probably guess I'm pretty inexperienced. I used one of the new 2TB drives I just put in. I formatted it to ext4 then copied the files over.

> 
sudo dd if=/dev/nvme0n1 of=/dev/nvme3n1 bs=64K conv=noerror,sync
15261915+1 records in
15261916+0 records out
1000204926976 bytes (1.0 TB, 932 GiB) copied, 1255.66 s, 797 MB/s

lsblk -f
nvme3n1
&#9500;&#9472;nvme3n1p1 ext4     1.0                9da9b39b-558e-4b6f-af56-67394b9e94c3
&#9500;&#9472;nvme3n1p2 swap     1                  eb614349-49e9-4194-bb4a-c0f4096af724
&#9492;&#9472;nvme3n1p3 ext4     1.0                f11c1d8a-098e-4cb4-9596-9910e66de233


So it looks like it worked. Then I used parted to change the partition size

> ubuntu@ubuntu:/$ sudo parted /dev/nvme0n1
GNU Parted 3.4
Using /dev/nvme0n1
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) resizepart
Partition number? 2
End?  [148GB]? 64GB
Warning: Shrinking a partition can cause data loss, are you sure you want to continue?
Yes/No? Yes


Then looking at the partition size:

> Model: Samsung SSD 980 1TB (nvme)
Disk /dev/nvme0n1: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system     Name  Flags
 2      20.0GB  64.0GB  44.0GB  linux-swap(v1)        swap
 1      148GB   168GB   20.0GB  ext4
 3      168GB   1000GB  832GB   ext4




How do I resize partition #1 to make it start at 64GB?

---

### Post by MAFoElffen on 2023-07-19
'parted' used to be able to move partitions and resize (certain) file systems, but that feature was removed from 'parted' in version 3.0. I use 'gparted' for that...

That is why I asked you to use 'gparted' to do that.

Note that I usually have done these things a few hundred times. If I am unclear about something 'specifically', that has been a while since, then I will test & confirm doing that on a VM. If you do things I didn't recommend, then you are on your own with the what-might-happen's of consequences. There has been users who were on their way to recovery, then went western (on their own) and destroyed their installation. I try to recommend a sound solution that has a high rate of success.

I can't look over your shoulder, nor can I stop you from doing things. Please... Just be careful.

---

### Post by mvinsky on 2023-07-20
I've really appreciated all your advice and I'm doing my best to follow these instructions. I couldn't use gparted from the command line so I thought it was another typo and you meant to say "parted". Last time I was in front of the computer I tried to use gparted to resize the partitions but there wasn't space in front of partition 2 to resize it. Now there appears to be space but I'm not sure how to do this from the command line. Any advice?

---

### Post by MAFoElffen on 2023-07-20
Why are you doing "commandline" if you booted from an Ubuntu Desktop 22.04.2 LTS LiveUSB? <-- Use that and make things much easier on yourself. 

That way you can also just start up FireFox from it to get back to the Forum, and cut-paste from one to another in a graphical terminal session. Doesn't that sound a lot easier and faster for you?

I do the same with the Server Edition Live Installer LiveUSB, if I want to stay Console, but remote into the Live Session with ssh, from a graphical terminal on my laptop.

As a technician, my laptop is part of my toolkit, as well as some USB flash drives that I can boot and diagnose 'things' from.

---

### Post by mvinsky on 2023-07-20
I'm not physically in the same location as the computer and I can't figure out a way to remotely connect to the GUI. 
I'll make some time to go where the computer is and try using gparted and get back to you. Thanks!

---

### Post by MAFoElffen on 2023-07-20
I have xorg xserver installed on my server, so I can do remote XForwarding to do management on it...

I have ssh keys generated for the root user. I used these basic instructions for the hint: [https://askubuntu.com/questions/477732/run-gparted-over-ssh](https://askubuntu.com/questions/477732/run-gparted-over-ssh)

I use this command:
```

sudo ssh -X -i /root/.ssh/groot-key-ecdsa root@10.0.0.3 sudo -E gparted

```
Attached is the screenshot of it running remotely to my server, from my laptop.

Though it would be much safer running it directly booted from a Desktop LiveUSB, and then you wouldn't have to install anything to your server.

---

