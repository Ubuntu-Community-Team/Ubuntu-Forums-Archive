---
title: "Installing dual-boot Ubuntu 16.04 on Dell XPS 15 9550 - problem with Grub install"
date: 2017-01-09
forum: Installation &amp; Upgrades
---

### Post by schanlin on 2017-01-09
I'm trying to install a dual-boot Ubuntu 16.04 with my Windows 10 Pro
  I've tried some of the suggested solutions, but nothing seems to  work. 
The whole install process goes smooth until it gets to the grub  configuration part, 
and no matter which partition I choose for the  bootloader earlier, it ends up with a similar error: 
```
Unable to install GRUB in /dev/nvme. 
```
(The /dev/nvme part differs, depending on the partition chosen)
  In the detailed info I can see that it tries to run the grub install command but fails with:
```
error: cannot open '/boot/efi/EFI/ubuntu/shimx64.efi:Read-only file system 
```
any suggestions?

---

### Post by ajgreeny on 2017-01-09
You have not given us enough information to help you much.

First you should shrink your Windows partition using its own disk management tools, which I will leave you to work out as I no longer use Windows. Do not create a partition; simply leave unallocated space, but then reboot to Windows and allow it to run chkdsk a couple of times.

Next you must, assuming your machine uses UEFI, install by booting to a USB, not DVD, and choose the UEFI version of the USB that should show in the boot menu that you get to from pressing a key at power-on. (F# or Esc or Del; you should see the key to use in the first screen that appears during POST.)

Third step is to choose **Something Else** at partitioning stage and point your installation to the free space, and you should not need to choose where grub goes as it will be put in the ESP or EFI partition that already exists.

Try doing the installation that way and come back again if that does not help.

---

### Post by schanlin on 2017-01-09
> **ajgreeny said:**
> You have not given us enough information to help you much.

Third step is to choose **Something Else** at partitioning stage and point your installation to the free space, and you should not need to choose where grub goes as it will be put in the ESP or EFI partition that already exists.

Try doing the installation that way and come back again if that does not help.

I did all the steps as described when I tried to install Ubuntu before I wrote the post.
It was supposed to be a standard ubuntu install, did this a couple of times before.
Re-did  it just now, at the partitioning stage under "Something Else" I've  selected the free space, clicked on + sign and set it as / mounting  point.
The installation broke while installing grub with error:
```
grub-efi-amd64-signed failed to install into /target/
```
If you need any additional info please specify what can I add.

From my perspective it looks like everything except installing grub works because for some reason it doesn't have access to the EFI partition?

---

### Post by oldfred on 2017-01-09
Ubuntu/grub does suppoet NMVe drives.
But was this system using RAID setting on drive. Desktop installer does not yet fully support install to drives seen as RAID. Many high end system use Intel SRT which is seen as RAID. 
You probably need to change drives from RAID to AHCI.
And may have to remove RAID meta-data from drives.

 Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241) 
   XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)
Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/) 
   Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)
Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)

---

### Post by schanlin on 2017-01-09
> **oldfred said:**
> 
You probably need to change drives from RAID to AHCI.
And may have to remove RAID meta-data from drives.


I did the change to AHCI before my first attempt at the install, all via instructions in some of the posts you provided (read them earlier).
My actions were mostly based on: [https://ubuntuforums.org/showthread.php?t=2317843](https://ubuntuforums.org/showthread.php?t=2317843), also I've read most of those materials before I started the install.
Did all the needed BIOS changes, "fixed" windows after that, updated partitions size 

BTW For some reason I don't have access to: [https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444) :(

Can you tell me a little bit more about removing RAID meta-data from drives?

BTW Looks like there are some ubuntu related entries on the efi drive (EFI/ubuntu/ folder which contains grubx64.efi, shimx64.efi etc files)
Still, the ubuntu install (via the install wizard) fails when it tries to install grub.

---

### Post by oldfred on 2017-01-09
Install in BIOS mode will fail on grub if you do not have bios_grub partition.
But it should install in UEFI mode to ESP if UEFI. But some have had issues with locked FAT32 partition and repairs sometimes are needed.

       Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
Even if raid not used BIOS may have set parameters, Also check BIOS settings should be AHCI
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
[http://askubuntu.com/questions/847470/ubuntu-16-04-installer-cant-see-ssd-drive/847481#847481](http://askubuntu.com/questions/847470/ubuntu-16-04-installer-cant-see-ssd-drive/847481#847481)

---

### Post by schanlin on 2017-01-10
> **oldfred said:**
> Even if raid not used BIOS may have set parameters, Also check BIOS settings should be AHCI
I've set it to AHCI before starting the install
haven't done any bigger changes since I got the laptop

> **oldfred said:**
> sudo dmraid -E -r /dev/sda
my disk is seen by gparted as /dev/nvme0n1
is erasing metadata from the disk any risk? should I backup anything?

---

### Post by oldfred on 2017-01-10
I would not expect the command to do anything that has risk.
But then just about anything has risk, so we always recommend that you update your standard backups before doing anything major on reconfiguration.
You are doing backups?

---

### Post by schanlin on 2017-01-10
> **oldfred said:**
> I would not expect the command to do anything that has risk.
But then just about anything has risk, so we always recommend that you update your standard backups before doing anything major on reconfiguration.
You are doing backups?

It's a clean machine with factory settings, no need for backing up data, just worried about making it unbootable or breaking the existing Windows 10 installation.

I've run the 
```
sudo dmraid -E -r /dev/nvme0n1 
```
command using Live ubuntu version (run from USB), got 
> no block devices found 
in response

---

### Post by oldfred on 2017-01-10
I had read where mdadm had replaced dmraid, but did not know new command.

[http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf](http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf)
First see what this says:
 sudo mdadm --detail-platform 
Then this should delete meta-data

sudo mdadm --zero-superblock /dev/<nvmeXn1>

It says it will not erase user data, but again backups important, even your Windows as reinstall of Windows can be a real hassle.

---

### Post by schanlin on 2017-01-10
> **oldfred said:**
> 
First see what this says:
 sudo mdadm --detail-platform 


```
ubuntu@ubuntu:~$ sudo mdadm --detail-platform 
mdmon: imsm capabilities not found for controller: /sys/devices/pci0000:00/0000:00:17.0 (type SATA)
```

> **oldfred said:**
> 
sudo mdadm --zero-superblock /dev/<nvmeXn1>

OK, I'll fire it up in a couple of minutes and update this post

EDIT:
```
ubuntu@ubuntu:~$ sudo mdadm --zero-superblock /dev/nvme0n1
mdadm: Unrecognised md component device - /dev/nvme0n1
```

---

### Post by oldfred on 2017-01-10
Seems like that is not issue?

Another issue some have had was the read only FAT32 file system.
Then you mount ESP - efi system partition and run chkdsk from Windows or:
       [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted, change example to your ESP, /dev/nvme0n1p1 if first partition is ESP?
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by schanlin on 2017-01-10
forgot to unmount before the first attempt but after the second it went throught.
trying to reinstall right now

```

ubuntu@ubuntu:~$ sudo dosfsck -t -a -w /dev/nvme0n1p1
fsck.fat 3.0.28 (2015-05-16)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
 Automatically removing dirty bit.
/EFI/Microsoft/Boot/BOOT.STL
  File size is 4669 bytes, cluster chain length is > 8192 bytes.
  Truncating file to 4669 bytes.
/EFI/Microsoft/Boot/BOOT.STL  and
/EFI/DELL/LOGS
  share clusters.
  Truncating second to 0 bytes.
Reclaimed 925 unused clusters (3788800 bytes) in 6 chains.
Free cluster summary wrong (110988 vs. really 110989)
  Auto-correcting.
Performing changes.
/dev/nvme0n1p1: 251 files, 15987/126976 clusters
ubuntu@ubuntu:~$ sudo umount /dev/nvme0n1p1
ubuntu@ubuntu:~$ sudo dosfsck -t -a -w /dev/nvme0n1p1
fsck.fat 3.0.28 (2015-05-16)
/EFI/DELL/LOGS
 Start does point to root directory. Deleting dir. 
Performing changes.
/dev/nvme0n1p1: 251 files, 15987/126976 clusters

```

edit:

IT WORKED! THANK YOU SO MUCH!!!

BTW are you able to explain me a little bit about what the problem was here?
Maybe what caused it?

---

### Post by ajgreeny on 2017-01-10
Great news!

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by oldfred on 2017-01-10
Do not know what causes issue.

But similar to Windows needing chkdsk or Linux needing fsck. Usually after abnormal shutdown or powerfailue.
But not sure why the ESP would get corrupted.

---

### Post by schanlin on 2017-01-11
If anybody gets to the bottom of this - I'm all ears! :)

---

### Post by ytxmobile on 2017-02-20
> **oldfred said:**
> Ubuntu/grub does suppoet NMVe drives.
But was this system using RAID setting on drive. Desktop installer does not yet fully support install to drives seen as RAID. Many high end system use Intel SRT which is seen as RAID. 
You probably need to change drives from RAID to AHCI.
And may have to remove RAID meta-data from drives.

 Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241) 
   XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)
Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/) 
   Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)
Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)

[https://samnicholls.net/2016/01/14/h...ows-10-xps-13/]("https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/")
Don't try this. I tried and ended up with unable to enter Windows 10 and needed to use system reset.

---

