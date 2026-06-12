---
title: "Trouble installing 12.10 64-bit on a RAID 0 configuration P8Z77-V PRO"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by sdsdsd2 on 2012-12-01
Hi everyone.

I have a ~1.9TB RAID 0 set up comprised of 3 640 GB HDs. I created a ~1.5 TB partition for Windows 7, which is running flawlessly, and was going to split the remaining space half and half with an Ubuntu and ArchLinux installation. Right now I'm trying to install Ubuntu and am having a very hard time doing so.

I created a bootable Ubuntu flash drive. The iso did match hashes with the expected hash value.

If I boot from the flash drive I get to the window that asks me if I want to try Ubuntu or install. Upon pressing install I then navigate to the "Installation type" window which shows absolutely no devices. At the bottom there's /dev/sda selected for "device for boot loader installation:" and if I press on the drop down that device is the only thing shown. If I press "Install now" I get an error and it then goes to a black screen.

Upon reboot I then press "Try now" and am able to get in the Ubuntu desktop. I downloaded gparted with the kparted add-on and when I open it it shows only my 3 HDs and the flashdrive, but no RAID. It says all 3 HDs have their full capacitance unallocated and doesn't detect any partitions. If I open Disks it shows one hard drive as having a partition but the other 3 are completely blank.

I then open Terminal and type the follow, which gives me the following:

$ sudo dmraid -tay
>isw_djejjcdice_The Future: 0 3750769920 striped 3 256 /dev/sda 0 /dev/sdc 0
$ sudo dmraid -ay
>RAID set "isw_djejjcdice_The Future" active
>ERROR: opening "/dev/mapper/isw_djejjcdice_The Future"

I then open gparted which gives me this error: "Could not stat device /dev/mapper/isw_djejjcdice_The Future - No such file or directory."

I then open Disks and it shows the RAID as "1.9 TB Block Device /dev/dm-0". It shows I have a 1.6 TB NTFS partition and 315 GB of free space.

I then hit Install Ubuntu 12.10, get to the "Installation type" screen and it shows 4 RAID set ups:
-/dev/mapper/isw_djejjcdice_The\x20Future
    -/dev/mapper/isw_djejjcdice_The type=ntfs size=104 MB used=unknown
    -/dev/mapper/isw_djejjcdice_The type=ntfs size=1605713 MB used=unknown
    -free space size=314574 MB
-/dev/mapper/isw_djejjcdice_The\x20Future1
    -/dev/mapper/isw_djejjcdice_The\x20Future1 type=ntfs size=104 MB used=unknown
-/dev/mapper/isw_djejjcdice_The\x20Future2 type=ntfs size=104 MB used=unknown
    -/dev/mapper/isw_djejjcdice_The\x20Future2 type=ntfs size=1605713 MB used=unknown
-/dev/mapper/isw_djejjcdice_The\x20Future3
-/dev/mapper/isw_djejjcdice_The\x20Future4

I then choose the Device for boot loader installation:
/dev/mapper/isw_djejjcdice_The\x20Future3 Linux device-mapper (linear) (314.6 GB)
and press "Install Now"

Which gives me this:

"
Sorry, Ubuntu 12.10 has experience an internal error.

If you notice further problems, try restarting the computer.

ExecutablePath
    /usr/lib/ubiquity/bin/ubiquity
Package
    ubiquity 2.12.16
ProblemType
    Crash
Title
    ubiquity crashed with KeyError in plugin_on_next_clicked(): 'use_device'
Traceback
ApportVersion
    2.6.1-0ubuntu3
Architecture
    amd64
Casper
CasperVersion
    1.328
CrashCounter
    1
Date
    Sat Dec 1 23:36:45 2012
Dependencies
DistroRelease
    Ubuntu 12.10
DuplicateOf
    [https://bugs.launchpad.net/bugs/727842](https://bugs.launchpad.net/bugs/727842)
InstallCmdLine
    noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed                     
    boot=casper persistent initrd=/casper/initrd.lz splash - maybe-ubiquity
InterpreterParth
    /usr/bin/python3.2mu
KnownReport
    [https://bugs.launchpad.net/bugs/727842](https://bugs.launchpad.net/bugs/727842)
LiveMediaBuild
"
(I'm stopping it there because I don't want to type any more of it, if there's a part you want of it just let me know.)

What can I do?

Thank you very much.

---

### Post by darkod on 2012-12-02
1. You don't use the standard live cd to install on fakeraid. You use the Alternate Install CD (different ISO). It has better raid support to install the bootloader correctly. The live cd will fail installing the grub2 bootloader.

2. You seem to have named the array 'The Future'. It might look cute, but it's not a good idea to have spaces in the name. I don't know whether it could create issues in linux or not, but I wouldn't use it personally.

3. The grub2 location can't be a partition, like you tried to install it on partition #3. How do you plan to boot ubuntu if you put grub2 on a partition and not the MBR? Windows bootloader can't boot it.

4. Are you using UEFI boot or legacy boot? With uefi boot you have to be careful to install in uefi mode, not legacy.

---

### Post by sdsdsd2 on 2012-12-02
> **darkod said:**
> 1. You don't use the standard live cd to install on fakeraid. You use the Alternate Install CD (different ISO). It has better raid support to install the bootloader correctly. The live cd will fail installing the grub2 bootloader.

2. You seem to have named the array 'The Future'. It might look cute, but it's not a good idea to have spaces in the name. I don't know whether it could create issues in linux or not, but I wouldn't use it personally.

3. The grub2 location can't be a partition, like you tried to install it on partition #3. How do you plan to boot ubuntu if you put grub2 on a partition and not the MBR? Windows bootloader can't boot it.

4. Are you using UEFI boot or legacy boot? With uefi boot you have to be careful to install in uefi mode, not legacy.

Oh man, how I wish you were here about 12 hours ago!

1. It's funny, because as I read this I was staring at the "Unable to install GRUB in /dev/sda" error on my pc. Thank you! I had no idea.

2. I found out it had problems with that when I ran mdadm and it had some error about there being two RAIDs, so I opened the intel configuration thing and changed the name.

3. I'm a complete noob, as you can probably already tell, so thank you!

4. Not sure. I assume UEFI boot is how my BIOS looks when I go into it? If I try to load my flashdrive in UEFI mode it just stays in the BIOS and doesn't do anything... If you're talking about what it looks like when the "which OS would you like to boot into" screen is up, that's not UEFI (at least, I don't think it is). I need to scroll with the keyboard and the mouse isn't active.

Edit: I went to the alternate CD page and saw an alternate .iso for 12.04.1, but no alternate for 12.10 . I was trying to install 12.10 . Does that CD not exist and I have to use 12.04.1?
Edit 2: So apparently they dropped support for the alternate 12.10 CD? So how am I supposed to install Ubuntu on a RAID for 12.10 then?...
Edit 3: So, from what I'm reading, I can install the alternate CD for 12.04.1 and then update it to 12.10 . Here's the link to a .torrent of the alternate amd64 12.04.1 .iso for anyone reading this: [releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-amd64.iso.torrent]("http://ubuntuforums.org/releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-amd64.iso.torrent")

---

### Post by darkod on 2012-12-02
Hm, I didn't know there is no ISO for 12.10. I use LTS releases so I haven't looked into 12.10.

Well, one option is to do the install using the desktop cd. After installation ubuntu will not be able to be booted. You can use the cd and load the live session, and add grub to the MBR of the array.

The only thing I am not sure is whether only grub2 will not be installed on the MBR of the array, or also the grub2 packages and config won't be instaleld. If the package and config is missing, you need a bit longer procedure to add it later, but that an be done too. So, the difference is between running only two commands to add grub2 to the MBR, or 10-15 commands to add grub2 completely.

UEFI is the new type of booting, but it still gives issues especially in dual boot, since it's oriented more towards Microsoft and making it more difficult to install dual boot with linux.

If you already have an existing ubuntu installation without the bootloader, you don't need to reinstall and can try to add grub2. In that case, boot the cd in live session, activate the array with dmraid (just in case it's not active), and post the parted output:
```
sudo dmraid -ay
sudo parted -l (small L)
```

That will give us few details to try adding grub2.

---

### Post by sdsdsd2 on 2012-12-03
> **darkod said:**
> Hm, I didn't know there is no ISO for 12.10. I use LTS releases so I haven't looked into 12.10.

Well, one option is to do the install using the desktop cd. After installation ubuntu will not be able to be booted. You can use the cd and load the live session, and add grub to the MBR of the array.

The only thing I am not sure is whether only grub2 will not be installed on the MBR of the array, or also the grub2 packages and config won't be instaleld. If the package and config is missing, you need a bit longer procedure to add it later, but that an be done too. So, the difference is between running only two commands to add grub2 to the MBR, or 10-15 commands to add grub2 completely.

UEFI is the new type of booting, but it still gives issues especially in dual boot, since it's oriented more towards Microsoft and making it more difficult to install dual boot with linux.

If you already have an existing ubuntu installation without the bootloader, you don't need to reinstall and can try to add grub2. In that case, boot the cd in live session, activate the array with dmraid (just in case it's not active), and post the parted output:
```
sudo dmraid -ay
sudo parted -l (small L)
```That will give us few details to try adding grub2.

So, before I read this I tried to install the alternate 12.04.1 amd 64 iso by setting the windows MBR as the boot directory for Ubuntu... little did I know it would actually overwrite the windows MBR, not add Ubuntu to that. x.x The alternate iso didn't work any better by the way, it still failed to install GRUB and failed to do everything the non-alternate disks failed to do.

Anyway, I checked my BIOS settings and actually found that my mobo has an option to support both UEFI and legacy boots at the same time, so I turned that on.

I remade a 12.10 flash drive and somehow got into the UEFI mode of the ubuntu on that flash drive. I followed this guide: [http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/) It installed great, no errors whatsoever (first time that ever happened). However, the Ubuntu selection isn't working in the boot menu (it just shows a blinking white underscore).

Here's the information you requested:

root@ubuntu:/home/ubuntu# dmraid -ay
RAID set "isw_djejjcdice_thefuture" already active
RAID set "isw_djejjcdice_thefuture1" already active
RAID set "isw_djejjcdice_thefuture2" already active
RAID set "isw_djejjcdice_thefuture5" already active
RAID set "isw_djejjcdice_thefuture6" already active
RAID set "isw_djejjcdice_thefuture7" already active
root@ubuntu:/home/ubuntu# sudo parted -l
Error: Can't have a partition outside the disk!                           

Error: /dev/sdb: unrecognised disk label                                  

Error: /dev/sdc: unrecognised disk label                                  

Model: USB 2.0 USB Flash Drive (scsi)
Disk /dev/sdd: 4041MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      65.5kB  4041MB  4041MB  primary  fat32        boot, lba


Error: Invalid partition table on /dev/mapper/isw_djejjcdice_thefuture3 -- wrong
signature ffff.
Ignore/Cancel? i                                                          
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture3: 168GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1024B   10.5GB  10.5GB  primary   fat32
 2      44.0GB  168GB   124GB   extended
 5      44.0GB  168GB   124GB   logical   ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture6: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  124GB  124GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture5: 10.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture7: 33.6GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  33.6GB  33.6GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture2: 1606GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1606GB  1606GB  ntfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture1: 105MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  105MB  105MB  ntfs


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture: 1920GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   1606GB  1606GB  primary   ntfs
 3      1606GB  1774GB  168GB   extended
 5      1606GB  1616GB  10.5GB  logical   fat32
 7      1616GB  1650GB  33.6GB  logical   linux-swap(v1)
 6      1650GB  1774GB  124GB   logical   ext4

---

### Post by darkod on 2012-12-03
You shouldn't have enabled uefi. I said to investigate whether you are using it or not, so that you know in which mode to install ubuntu. But if you are not using it (and from parted results you are not), you can't simpy enable it and start using it because then windows won't work. Once windows is installed, you can't change the boot type.

Go back into bios and disable the uefi setting, or set it to BIOS boot only, if that's how it's called.

After that you will need to reinstall ubuntu since now you installed it in uefi mode according to what you say. I am not sure if it will work without reinstalling since in uefi it would install the uefi version of grub.

In general, you can see at the bottom of the parted results that your ubuntu root is partition #6. So, to add grub2 to the MBR of the array from live session (note that you might need to reinstall ubuntu in bios mode before this as explained above), you would do:
```
sudo mount /dev/mapper/isw_blahblah_thefuture6 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_blahblah_thefuture
```

That will install it onto the MBR of the array, that's why the second command doesn't have the 6 at end of the array name.

Now, this is the shorter procedure and note that it might not work 100% if the grub package is not installed. If this doesn't work, you will need to boot into live session again and do the longer procedure.

---

### Post by sdsdsd2 on 2012-12-03
> **darkod said:**
> You shouldn't have enabled uefi. I said to investigate whether you are using it or not, so that you know in which mode to install ubuntu. But if you are not using it (and from parted results you are not), you can't simpy enable it and start using it because then windows won't work. Once windows is installed, you can't change the boot type.

Go back into bios and disable the uefi setting, or set it to BIOS boot only, if that's how it's called.

After that you will need to reinstall ubuntu since now you installed it in uefi mode according to what you say. I am not sure if it will work without reinstalling since in uefi it would install the uefi version of grub.

In general, you can see at the bottom of the parted results that your ubuntu root is partition #6. So, to add grub2 to the MBR of the array from live session (note that you might need to reinstall ubuntu in bios mode before this as explained above), you would do:
```
sudo mount /dev/mapper/isw_blahblah_thefuture6 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_blahblah_thefuture
```That will install it onto the MBR of the array, that's why the second command doesn't have the 6 at end of the array name.

Now, this is the shorter procedure and note that it might not work 100% if the grub package is not installed. If this doesn't work, you will need to boot into live session again and do the longer procedure.

So, because my BIOS's option was both UEFI and legacy boot I went ahead and tried to add it to the MBR with the commands above, assuming there might be some option like "switch to legacy/uefi boot" at the boot menu. Upon rebooting, it went into the GRUB uefi with no option of starting windows, only of starting Ubuntu. However, when I tried to start Ubuntu it would go to the black screen with the blinking white underscore and after about 30 seconds would give me an error message saying, essentially, that it had given up trying to find some files. I went ahead and remade a windows recovery usb drive and fixed the mbr so I could get back into windows. Looking back at it, I probably could've gone into the BIOS and changed some settings since my BIOS does have settings along the lines of "boot both uefi and legacy, but uefi/legacy first" and likely could've just switched that without writing over the mbr.

I've disabled all mentions of uefi boot in my BIOS and am in the process of recreating the 12.10 Ubuntu flash drive.

Edit 1: The Ubuntu installer failed at the "Running 'grub-install /dev/sda'..." step with error message:
"
Unable to install GRUB in /dev/sda
Executing 'grub-install /dev/sda' failed.

This is a fatal error.
"
Other than that, the installation went well.

I then reran the commands you had posted, which reported they completed successfully with no errors.

Upon rebooting, I am brought to the GNU GRUB terminal with no prior menu of selecting Windows or Ubuntu.

---

### Post by darkod on 2012-12-03
Post the parted results again so see the current setup. After that we will try to completely reinstall grub2.

---

### Post by sdsdsd2 on 2012-12-03
> **darkod said:**
> Post the parted results again so see the current setup. After that we will try to completely reinstall grub2.
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# dmraid -ay
RAID set "isw_djejjcdice_thefuture" already active
RAID set "isw_djejjcdice_thefuture1" already active
RAID set "isw_djejjcdice_thefuture2" already active
RAID set "isw_djejjcdice_thefuture5" already active
RAID set "isw_djejjcdice_thefuture6" already active
RAID set "isw_djejjcdice_thefuture7" already active
root@ubuntu:/home/ubuntu# parted -l
Error: Can't have a partition outside the disk!                           

Error: /dev/sdb: unrecognised disk label                                  

Error: /dev/sdc: unrecognised disk label                                  

Model: USB 2.0 USB Flash Drive (scsi)
Disk /dev/sdd: 4041MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      65.5kB  4041MB  4041MB  primary  fat32        boot, lba


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture2: 1606GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1606GB  1606GB  ntfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture7: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  124GB  124GB  ext4


Error: Invalid partition table on /dev/mapper/isw_djejjcdice_thefuture3 -- wrong
signature ffff.
Ignore/Cancel? i                                                          
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture3: 168GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1024B   10.5GB  10.5GB  primary   fat32
 2      10.5GB  44.0GB  33.6GB  extended
 5      10.5GB  44.0GB  33.6GB  logical   linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture5: 10.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture6: 33.6GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  33.6GB  33.6GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture1: 105MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  105MB  105MB  ntfs


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_djejjcdice_thefuture: 1920GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   1606GB  1606GB  primary   ntfs
 3      1606GB  1774GB  168GB   extended
 5      1606GB  1616GB  10.5GB  logical   fat32
 6      1616GB  1650GB  33.6GB  logical   linux-swap(v1)
 7      1650GB  1774GB  124GB   logical   ext4

---

### Post by darkod on 2012-12-03
OK, so the root partition is #7. Lets use chroot to enter the installation from the live session:
```
sudo mount /dev/mapper/isw_blahblah_thefuture7 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are like inside the installation. Lets completely remove grub2, install it again, create the config files and install it onto the MBR of the array:
```
apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/mapper/isw_blahblah_thefuture
```

Exit the chroot and unmount everything:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Reboot without the cd and with little bit of luck, you should see a functioning grub menu. Try to boot both OSs to see if they work.

---

### Post by sdsdsd2 on 2012-12-03
> **darkod said:**
> OK, so the root partition is #7. Lets use chroot to enter the installation from the live session:
```
sudo mount /dev/mapper/isw_blahblah_thefuture7 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```Now you are like inside the installation. Lets completely remove grub2, install it again, create the config files and install it onto the MBR of the array:
```
apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/mapper/isw_blahblah_thefuture
```Exit the chroot and unmount everything:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```Reboot without the cd and with little bit of luck, you should see a functioning grub menu. Try to boot both OSs to see if they work.


I ran into an error, so I'm just going to post the whole terminal so far.

ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_djejjcdice_thefuture7 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get remove --purge grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-gfxpayload-lists* grub-pc* grub-pc-bin* grub2-common*
  ubiquity* ubiquity-frontend-gtk*
0 upgraded, 0 newly installed, 7 to remove and 151 not upgraded.
After this operation, 25.6 MB disk space will be freed.
Do you want to continue [Y/n]? Y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 156616 files and directories currently installed.)
Removing ubiquity-frontend-gtk ...
Removing grub-gfxpayload-lists ...
Removing ubiquity ...
Purging configuration files for ubiquity ...
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub2-common ...
Removing grub-pc-bin ...
Removing grub-common ...
invoke-rc.d: policy-rc.d denied execution of stop.
Purging configuration files for grub-common ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-common grub-gfxpayload-lists grub-pc-bin grub2-common
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
0 upgraded, 5 newly installed, 0 to remove and 151 not upgraded.
Need to get 2,368 kB of archives.
After this operation, 9,283 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main grub-common amd64 2.00-7ubuntu11
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main grub2-common amd64 2.00-7ubuntu11
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main grub-pc-bin amd64 2.00-7ubuntu11
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main grub-pc amd64 2.00-7ubuntu11
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main grub-gfxpayload-lists amd64 0.6
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_2.00-7ubuntu11_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_2.00-7ubuntu11_amd64.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub2-common_2.00-7ubuntu11_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub2-common_2.00-7ubuntu11_amd64.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc-bin_2.00-7ubuntu11_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc-bin_2.00-7ubuntu11_amd64.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_2.00-7ubuntu11_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_2.00-7ubuntu11_amd64.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub-gfxpayload-lists/grub-gfxpayload-lists_0.6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub-gfxpayload-lists/grub-gfxpayload-lists_0.6_amd64.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by darkod on 2012-12-03
Looks like the internet is not working, or only the DNS resolving. So it can't download the packages from the repositories.

Do you have fully working internet in the live session? And often it's better to use a wired connection at least temporarily, since wi-fi sometimes doesn't work in live session.

Test pinging both IP and domain to see if it's general internet problem or only dns:
ping 8.8.8.8
ping google.com

---

### Post by sdsdsd2 on 2012-12-03
> **darkod said:**
> Looks like the internet is not working, or only the DNS resolving. So it can't download the packages from the repositories.

Do you have fully working internet in the live session? And often it's better to use a wired connection at least temporarily, since wi-fi sometimes doesn't work in live session.

Test pinging both IP and domain to see if it's general internet problem or only dns:
ping 8.8.8.8
ping google.com

8.8.8.8 works fine but google.com ping doesn't. It's strange though, because I'm typing all of this on the Live CD and I can open a new tab and go to youtube.com

Edit: I'm going to try rebooting the live cd.

---

### Post by darkod on 2012-12-03
Definitely weird. Click the Network Manager icon top right, then Edit Connections. Select the correct wired or wireless connection, then Edit.

On the IPv4 tab, change the option from Automatic (DHCP) to Automatic DHCP address only. In the field below for DNS servers, put: 8.8.8.8 8.8.4.4

Save the changes.
Try the ping google.com again and if it works continue the procedure. If you didn't reboot and still have the chroot open, you can continue. If you rebooted you will need to start from the beginning only this time you don't have to repeat the apt-get remove --purge line since it was done succssfully.

---

### Post by sdsdsd2 on 2012-12-03
> **darkod said:**
> Definitely weird. Click the Network Manager icon top right, then Edit Connections. Select the correct wired or wireless connection, then Edit.

On the IPv4 tab, change the option from Automatic (DHCP) to Automatic DHCP address only. In the field below for DNS servers, put: 8.8.8.8 8.8.4.4

Save the changes.
Try the ping google.com again and if it works continue the procedure. If you didn't reboot and still have the chroot open, you can continue. If you rebooted you will need to start from the beginning only this time you don't have to repeat the apt-get remove --purge line since it was done succssfully.

Still not working. 8.8.8.8 works but [www.google.com]("http://www.google.com") doesn't. Is it possible to install GRUB somewhere else and move it over to the desired location? Or possible to manually enter the ip of the place we'd be getting the grub installation from?

It's a wired connection, by the way.

---

### Post by darkod on 2012-12-03
I haven't tried it before, but in theory if you open Software Centre and find the Software Sources menu, you should be able to add the cd as a source. So it should be able to pick it up from there.

Otherwise I don't know of another way. The error message might be coming from within the chroot, maybe the hdd installation doesn't have a correct dns setting. But usually as long as it works in the live session, it should be fine. The ping google.com doesn't work in the live session but opening websites seems to work.

Give the cd-rom as a repository a go, and lets see.

PS. Also you can try changing the preferred server in Software Sources. Then try with using another server.

---

### Post by sdsdsd2 on 2012-12-03
> **darkod said:**
> I haven't tried it before, but in theory if you open Software Centre and find the Software Sources menu, you should be able to add the cd as a source. So it should be able to pick it up from there.

Otherwise I don't know of another way. The error message might be coming from within the chroot, maybe the hdd installation doesn't have a correct dns setting. But usually as long as it works in the live session, it should be fine. The ping google.com doesn't work in the live session but opening websites seems to work.

Give the cd-rom as a repository a go, and lets see.

PS. Also you can try changing the preferred server in Software Sources. Then try with using another server.

ubuntu@ubuntu:~$ ping google.com
PING google.com (74.125.225.72) 56(84) bytes of data.
64 bytes from ord08s07-in-f8.1e100.net (74.125.225.72): icmp_req=1 ttl=56 time=12.9 ms
64 bytes from ord08s07-in-f8.1e100.net (74.125.225.72): icmp_req=2 ttl=56 time=12.2 ms
64 bytes from ord08s07-in-f8.1e100.net (74.125.225.72): icmp_req=3 ttl=56 time=12.6 ms
^C
--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 12.298/12.653/12.968/0.304 ms


It works when outside the chroot.

Edit: Here's a picture of the software sources I think you're talking about? 
[http://imgur.com/8wsYK](http://imgur.com/8wsYK)
[IMG]http://imgur.com/8wsYK[/IMG][IMG]http://imgur.com/8wsYK[/IMG]
It seems to already be a source. In case it isn't, when I click "add" this window pops up:
"
Enter the complete APT line of the repository that you want to add as source
"

Edit 2: I changed the server to US server and it still doesn't work. This is the directory it's accessing to get all the files: [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/) Can we just manually download the necessary files and then do a grub-install procedure?

Edit 3: I tried to add the [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/) as a source and it still doesn't work. Perhaps I added it incorrectly?

Edit 4: Is this worth giving a shot? [https://wiki.archlinux.org/index.php/BIND_%28chroot%29](https://wiki.archlinux.org/index.php/BIND_%28chroot%29)

---

### Post by darkod on 2012-12-03
It might be easier to try boot-repair in that case. You can do it from live session:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Note that you have to be careful and install grub2 onto the MBR of the array. In the main boot-repair window click on Advanced options.

In the Main options tab, make sure Reinstall Grub is selected.

After that, in the Grub Location tab select Place Grub into: and the array device (without any partition number).

In the grub options tab, select Purge Grub before reinstalling it.

That should be all the options you need. See if that can sort it out.

---

### Post by sdsdsd2 on 2012-12-03
> **darkod said:**
> It might be easier to try boot-repair in that case. You can do it from live session:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Note that you have to be careful and install grub2 onto the MBR of the array. In the main boot-repair window click on Advanced options.

In the Main options tab, make sure Reinstall Grub is selected.

After that, in the Grub Location tab select Place Grub into: and the array device (without any partition number).

In the grub options tab, select Purge Grub before reinstalling it.

That should be all the options you need. See if that can sort it out.

Here's what it told me:
"
Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1407986/](http://paste.ubuntu.com/1407986/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on mapper/isw_djejjcdice_thefuture (1920GB) disk!

A broken Wubi has been detected. Please fix it this way:
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)
"

---

### Post by darkod on 2012-12-03
Looks good. Did you try if it's working after rebooting?

---

### Post by sdsdsd2 on 2012-12-03
> **darkod said:**
> Looks good. Did you try if it's working after rebooting?

I tried to boot into Ubuntu. My monitors told me "there's no connection" and went black. I waited about a minute and nothing happened so I rebooted.

There are two options for Windows 7 in GRUB. I tried one of them out and it worked great! I'm in Windows right now.

I assume that Wubi problem was what was causing that black screen, so I'm trying to run a chkdsk on the drive that Ubuntu is installed on. Unfortunately, the drives aren't mapped or something because they don't have a path.

Here's a picture of what I'm seeing (they just don't show up despite being recognized as partitions in Disk Management):
[http://i.imgur.com/oyIME.png](http://i.imgur.com/oyIME.png)

So I'm not really sure how to run a chkdsk on a drive that I can't reference...

I'm trying to google it now.

Edit 1: I tried to run chkdsk on the drive letters despite them not appearing and it didn't work.

Edit 2: Ugh. This is terrible... I downloaded Ext2Read because I saw a person was able to get windows to recognize ext drives and assign them letters. I ran the program and used it to permanently set drive letters to them, however, Windows still doesn't know how to read Ext4 format and so it detects the drives as RAW format. When I try to chkdsk it I get this message:
"
The type of the file system is RAW.
CHKDSK is not available for RAW drives.
"

I have the sector range from the partition, why can't I just run a chkdsk on those sectors? :'(

Edit 3: So I read that fsck.ext4 is the linux version of chkdsk for ext4 partitions. I ran it and now when I select Ubuntu from GRUB I get to the purple and white Ubuntu loading screen but it just stays there loading. I've waited about four minutes now, I'll wait a few more minutes before I do a manual reboot... Any ideas on what to do after that?

Edit 4: Got back into the splash screen and [tried]("http://ubuntuforums.org/showthread.php?t=2003282") to get into a tty via cntrl+alt+f1 so I could run sudo dpkg-reconfigure lightdm. Upon pressing cntrl+alt+f1 I went to a black screen with a tiny white underscore that blinked rapidly. Pressing keys did nothing.

Edit 5: I ran the Recovery Mode after reading [this]("http://askubuntu.com/questions/120096/ubuntu-hangs-at-purple-screen") (I have a 7000 series). Upon selecting any option a fsck.ext4 run appears beneath the menu with a blinking white underscore which I can type into. Typing commands does nothing, but upon pressing cntrl+c I'm brought to the following screen:
"
Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.

Warning: Fake initct1 called, doing nothing.
The disk drive for / is not ready yet or not present.
keys: Continue to wait, or Press S to skip mounting or M for manual recovery
"
No key press does anything except for esc, which switches to a white and purple loading screen that says the same warning message. Pressing esc again switches back to the white and black command prompt-looking screen.

Edit 6: I just ran the system information option in the recovery mode and under the property "=== Software RAID state ===" it says:
No software RAID detected (mdstat)
Perhaps that's causing this?

---

### Post by darkod on 2012-12-03
chkdsk is for ntfs partitions. Forget about reading linux partitions from windows, it can only get you into problems. I wouldn't try it.

If you want to run a check of the ubuntu partition, all you need to do from live session is:
```
sudo fsck /dev/mapper/isw_blahblah_thefuture7
```

That will run the fsck on partition #7.

The black screen or stucking at the purple screen might be a video issue. I didn't understand whether you did run the commands to install fglrx or not? They need to be run from ubuntu recovery mode, not from windows command prompt.
In the grub boot menu, select the ubuntu recovery mode. In the menu that shows up, select Network to activate networking (internet).
After that it will return you to the same menu, now select Drop to root shell.

That will open command prompt as root. Start executing the commands in that link:
```
apt-get install fglrx
aticonfig --initial
reboot
```

You don't need the sudo in front since in the root shell you are already as root.

See if something like that can help. Usually the nvidia cards were the ones giving problems, not ATI but it seems lately there was a change in the drivers included in ubuntu so you have to do some additional steps for ATI cards too.

You can also try downloading the driver from the AMD website and putting it onto a usb stick. Then you can try installing it in recovery mode. But try the above procedure first.

PS. About your Edit6, the message about software raid. The message is correct, you don't have software raid. Linux software raid is different from the bios fakeraid, even though fakeraid is also software based in a way. But it's not linux software raid. So, the message saying you don't have one is correct and that's not a problem.

---

### Post by sdsdsd2 on 2012-12-03
> **darkod said:**
> chkdsk is for ntfs partitions. Forget about reading linux partitions from windows, it can only get you into problems. I wouldn't try it.

If you want to run a check of the ubuntu partition, all you need to do from live session is:
```
sudo fsck /dev/mapper/isw_blahblah_thefuture7
```That will run the fsck on partition #7.

The black screen or stucking at the purple screen might be a video issue. I didn't understand whether you did run the commands to install fglrx or not? They need to be run from ubuntu recovery mode, not from windows command prompt.
In the grub boot menu, select the ubuntu recovery mode. In the menu that shows up, select Network to activate networking (internet).
After that it will return you to the same menu, now select Drop to root shell.

That will open command prompt as root. Start executing the commands in that link:
```
apt-get install fglrx
aticonfig --initial
reboot
```You don't need the sudo in front since in the root shell you are already as root.

See if something like that can help. Usually the nvidia cards were the ones giving problems, not ATI but it seems lately there was a change in the drivers included in ubuntu so you have to do some additional steps for ATI cards too.

You can also try downloading the driver from the AMD website and putting it onto a usb stick. Then you can try installing it in recovery mode. But try the above procedure first.

PS. About your Edit6, the message about software raid. The message is correct, you don't have software raid. Linux software raid is different from the bios fakeraid, even though fakeraid is also software based in a way. But it's not linux software raid. So, the message saying you don't have one is correct and that's not a problem.

That's the thing though. I can't activate network in recovery mode because it does the problem I described in Edit 5. I can drop to root shell, though. The commands don't work without internet, though...

Edit 1: I get stuck on the splash screen but the orbs below "ubuntu" still turn red/white. It's not frozen.

Edit 2: HEY!!!! I just found something cool!

So I did a google search to see if there was a way to set up a network connection via the root shell, and there's a command dhclient eth0 which can do it. It didn't work out in the recovery mode root shell, but I figured I'd try it out in that chroot shell we were having trouble with earlier, and it worked! So right now I'm installing GRUB with your installation guide.

Edit 3: So I followed what you told me to do and there's a problem, a device which isn't supposed to be being used (at least I don't think it is) IS being used and I'm unable to unmount it. I'll post the full terminal so you can see exactly what happened, but the problem is at the end of it. Is it safe to reboot?

Here it is:

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mount /dev/mapper/isw_djejjcdice_thefuture7 /mnt
root@ubuntu:/home/ubuntu# mount --bind /proc /mnt/proc
root@ubuntu:/home/ubuntu# mount --bind /dev /mnt/dev
root@ubuntu:/home/ubuntu# mount --bind /sys /mnt/sys
root@ubuntu:/home/ubuntu# chroot /mnt
root@ubuntu:/# dhclient eth0
root@ubuntu:/# apt-get remove --purge grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-gfxpayload-lists* grub-pc* grub-pc-bin* grub2-common*
0 upgraded, 0 newly installed, 5 to remove and 150 not upgraded.
After this operation, 9,283 kB disk space will be freed.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 155942 files and directories currently installed.)
Removing grub-gfxpayload-lists ...
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub2-common ...
Removing grub-pc-bin ...
Removing grub-common ...
invoke-rc.d: policy-rc.d denied execution of stop.
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-common grub-gfxpayload-lists grub-pc-bin grub2-common
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
0 upgraded, 5 newly installed, 0 to remove and 150 not upgraded.
Need to get 0 B/2,368 kB of archives.
After this operation, 9,283 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously unselected package grub-common.
(Reading database ... 155591 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_2.00-7ubuntu11_amd64.deb) ...
Selecting previously unselected package grub2-common.
Unpacking grub2-common (from .../grub2-common_2.00-7ubuntu11_amd64.deb) ...
Selecting previously unselected package grub-pc-bin.
Unpacking grub-pc-bin (from .../grub-pc-bin_2.00-7ubuntu11_amd64.deb) ...
Selecting previously unselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_2.00-7ubuntu11_amd64.deb) ...
Selecting previously unselected package grub-gfxpayload-lists.
Unpacking grub-gfxpayload-lists (from .../grub-gfxpayload-lists_0.6_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-common (2.00-7ubuntu11) ...
invoke-rc.d: policy-rc.d denied execution of start.
Processing triggers for ureadahead ...
Setting up grub2-common (2.00-7ubuntu11) ...
Setting up grub-pc-bin (2.00-7ubuntu11) ...
Setting up grub-gfxpayload-lists (0.6) ...
Setting up grub-pc (2.00-7ubuntu11) ...

Creating config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
  No volume groups found
Found Windows 7 (loader) on /dev/mapper/isw_djejjcdice_thefuture1
Found Windows 7 (loader) on /dev/mapper/isw_djejjcdice_thefuture2
done
root@ubuntu:/# grub-mkconfig
Generating grub.cfg ...
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root  20a44ca8-89ba-40fc-a51e-33423e1784a7
else
  search --no-floppy --fs-uuid --set=root 20a44ca8-89ba-40fc-a51e-33423e1784a7
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-20a44ca8-89ba-40fc-a51e-33423e1784a7' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  20a44ca8-89ba-40fc-a51e-33423e1784a7
    else
      search --no-floppy --fs-uuid --set=root 20a44ca8-89ba-40fc-a51e-33423e1784a7
    fi
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=20a44ca8-89ba-40fc-a51e-33423e1784a7 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-20a44ca8-89ba-40fc-a51e-33423e1784a7' {
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-20a44ca8-89ba-40fc-a51e-33423e1784a7' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  20a44ca8-89ba-40fc-a51e-33423e1784a7
        else
          search --no-floppy --fs-uuid --set=root 20a44ca8-89ba-40fc-a51e-33423e1784a7
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=20a44ca8-89ba-40fc-a51e-33423e1784a7 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-20a44ca8-89ba-40fc-a51e-33423e1784a7' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  20a44ca8-89ba-40fc-a51e-33423e1784a7
        else
          search --no-floppy --fs-uuid --set=root 20a44ca8-89ba-40fc-a51e-33423e1784a7
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=20a44ca8-89ba-40fc-a51e-33423e1784a7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
  No volume groups found
Found Windows 7 (loader) on /dev/mapper/isw_djejjcdice_thefuture1
menuentry 'Windows 7 (loader) (on /dev/mapper/isw_djejjcdice_thefuture1)' --class windows --class os $menuentry_id_option 'osprober-chain-38CC659FCC6557E0' {
    insmod part_msdos
    insmod ntfs
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  38CC659FCC6557E0
    else
      search --no-floppy --fs-uuid --set=root 38CC659FCC6557E0
    fi
    chainloader +1
}
Found Windows 7 (loader) on /dev/mapper/isw_djejjcdice_thefuture2
menuentry 'Windows 7 (loader) (on /dev/mapper/isw_djejjcdice_thefuture2)' --class windows --class os $menuentry_id_option 'osprober-chain-3CA44133A440F0C6' {
    insmod part_msdos
    insmod ntfs
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  3CA44133A440F0C6
    else
      search --no-floppy --fs-uuid --set=root 3CA44133A440F0C6
    fi
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
done
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
  No volume groups found
Found Windows 7 (loader) on /dev/mapper/isw_djejjcdice_thefuture1
Found Windows 7 (loader) on /dev/mapper/isw_djejjcdice_thefuture2
done
root@ubuntu:/# grub-install /dev/mapper/isw_djejjcdice_thefuture
Installation finished. No error reported.
root@ubuntu:/# exit
exit
root@ubuntu:/home/ubuntu# sudo umount /mnt/sys
root@ubuntu:/home/ubuntu# sudo umount /mnt/dev
umount: /mnt/dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
root@ubuntu:/home/ubuntu# sudo umount /mnt/proc
root@ubuntu:/home/ubuntu# sudo umount /mnt/dev
umount: /mnt/dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
root@ubuntu:/home/ubuntu# sudo umount /mnt/dev
umount: /mnt/dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

Edit 4: So I just found out about fuser. Here's the terminal log:

root@ubuntu:/home/ubuntu# fuser -mu /mnt/dev
/mnt/dev:                1(root)  3565(root)  3576(root)  3602(messagebus)  3685(root)  3932(avahi)  3937(avahi)  3945(root)  4264(root)  4304(root)  4388(root)  4401(root)  4407(root)  4418(root)  4419(root)  4421(root)  4440(root)  4447(daemon)  4451(root)  4519(root)  4714(root)  4844(ubuntu)  4845(ubuntu)  4846(ubuntu)  4847(ubuntu)  4848(ubuntu)  4852(whoopsie)  5182(root)  5332(root)  5497(ubuntu)  5716(root)  5922(root)  5923(root)  5938(ubuntu)  5940(rtkit)  5958(colord)  5977(ubuntu)  5984(nobody)  7832(root)  7845m(root)  7858(root)  7871(root)  7893(ubuntu)  7928(ubuntu)  7931(ubuntu)  7932(ubuntu)  7934(ubuntu)  7938(ubuntu)  7941(ubuntu)  7952(ubuntu)  7961(ubuntu)  7973(ubuntu)  7979(ubuntu)  7985(ubuntu)  7989(ubuntu)  7997(ubuntu)  8007(ubuntu)  8008(ubuntu)  8009(ubuntu)  8012(ubuntu)  8014(ubuntu)  8022(ubuntu)  8028(root)  8035(ubuntu)  8039(ubuntu)  8067(ubuntu)  8073(ubuntu)  8077(ubuntu)  8086(ubuntu)  8090(ubuntu)  8091(ubuntu)  8103(ubuntu)  8105(ubuntu)  8114(ubuntu)  8116(ubuntu)  8118(ubuntu)  8120(ubuntu)  8124(ubuntu)  8126(ubuntu)  8154(ubuntu)  8159(ubuntu)  8171(ubuntu)  8187(ubuntu)  8189(ubuntu)  8191(ubuntu)  8193(ubuntu)  8195(ubuntu)  8197(ubuntu)  8199(ubuntu)  8234(ubuntu)  8244(ubuntu)  8246(ubuntu)  8291(ubuntu)  8293(ubuntu)  8315(ubuntu)  8324(ubuntu)  8329(ubuntu)  8380(ubuntu)  8386(ubuntu)  8392(ubuntu)  8426(ubuntu)  8475(root)  9059(ubuntu)  9063(ubuntu)  9140(ubuntu) 13713(root) 13762(root) 14681(ubuntu) 14705(ubuntu)

---

### Post by darkod on 2012-12-03
That's cool, but the boot-repair process already reinstalled grub2 and now you can see the boot menu and boot win7. My procedure will do the same thing as boot-repair, you already did that.

I assume you will still have the problem when loading ubuntu.

I wonder if it's somehow connected to the fakeraid array, and whether it's not loading the array correctly. So subsequently it doesn't have the system root partition to mount.

---

### Post by sdsdsd2 on 2012-12-03
> **darkod said:**
> That's cool, but the boot-repair process already reinstalled grub2 and now you can see the boot menu and boot win7. My procedure will do the same thing as boot-repair, you already did that.

I assume you will still have the problem when loading ubuntu.

I wonder if it's somehow connected to the fakeraid array, and whether it's not loading the array correctly. So subsequently it doesn't have the system root partition to mount.

Now that we can get internet in chroots, though, can't we install those packages we wanted to before but couldn't because of the problem in edit 5? Also, is it safe to unmount that drive?

---

### Post by darkod on 2012-12-03
I'm not sure which packages are you referring to. It failed when you tried reinstalling grub2, but now that is done. There were not other packages that failed installing.

I wonder if all of this is consequence of using the live cd, although in theory it should work.

Are you willing to give alternate 12.04 a try? That should work start to finish, without needing to additionally add grub2. Just remember the array name in case it gets confused in the last install step and asks you to confirm the full array device name which is /dev/mapper/isw_...._thefuture.

If you decide to reinstall with the alternate 12.04 cd you can use manual partitioning and reuse the existing partitions. Simply select them and set the correct mount points. Format the root partition so that it deletes all old files.

In fact, if installing 12.04 LTS works fine, I wouldn't even try to upgrade it to 12.10. 12.04 is LTS and is supported 5 years, while 12.10 is standard release and is supported only 18 months.

---

### Post by sdsdsd2 on 2012-12-03
> **darkod said:**
> I'm not sure which packages are you referring to. It failed when you tried reinstalling grub2, but now that is done. There were not other packages that failed installing.

I wonder if all of this is consequence of using the live cd, although in theory it should work.

Are you willing to give alternate 12.04 a try? That should work start to finish, without needing to additionally add grub2. Just remember the array name in case it gets confused in the last install step and asks you to confirm the full array device name which is /dev/mapper/isw_...._thefuture.

If you decide to reinstall with the alternate 12.04 cd you can use manual partitioning and reuse the existing partitions. Simply select them and set the correct mount points. Format the root partition so that it deletes all old files.

In fact, if installing 12.04 LTS works fine, I wouldn't even try to upgrade it to 12.10. 12.04 is LTS and is supported 5 years, while 12.10 is standard release and is supported only 18 months.


The packages I'm referring to are the missing files from the ubuntu installation which might've been causing the hang on the splash screen. Maybe we could install the graphics drivers or whatever?

I can try 12.04, sure. But first I need to know if it's safe to unmount /mnt/dev, even though it's in use by ~30 different files/programs, because I don't want to mess anything up.

---

### Post by darkod on 2012-12-03
Ah, OK. You mean installing the fglrx driver. Yes, you can try that.

Unmounting /mnt/dev should be fine, we only mounted it to use the chroot procedure. Once you are done inside the chroot and exit it, unmounting /mnt/dev should be fine.

---

### Post by sdsdsd2 on 2012-12-03
> **darkod said:**
> Ah, OK. You mean installing the fglrx driver. Yes, you can try that.

Unmounting /mnt/dev should be fine, we only mounted it to use the chroot procedure. Once you are done inside the chroot and exit it, unmounting /mnt/dev should be fine.

I couldn't get an internet connection established in the chroot.

I installed 12.04.1 alternate amd 64 bit and it's failed on the "Select and install software" step. I didn't choose the option to install a GRUB. Upon rebooting I got to a screen which had this:

error: unknown filesystem.
grub rescue>_


I relaunched the 12.04.1 installer and ran the rescue mode. When it got to the menu that said "Enter rescue mode" and wanted me to choose what would be the "device to use as root file system" I had 3 options:
-/dev/sdd1
-Assemble RAID array
-Do not use a root file system

I selected assemble raid array and it wanted me to select which "partitions to assemble" which had 2 options:
-Automatic
-/dev/sdd1
with a "continue" button in the bottom right.
I tried selecting automatic and hit continue but it brought me back to the "choose a root file system" menu. I went back in and tried /dev/sdd1 but the same thing happened. Selecting both at the same time had the same outcome. I then chose /dev/sdd1 to be the root file system and it said "Mount failed An error occurred while mounting the device you entered for your root file system (/dev/sdd1) on /target. Please check the syslog for more information." I then chose the only remaining option...

The next menu showed three options:
1. open a shell
2. load another root file system
3. quit

I opened the shell but it's pretty much the same thing as when we had 12.10 installed...

---

### Post by darkod on 2012-12-03
/dev/sdd1 is your usb stick I believe. You can't use it as root partition.

If the 12.04 install failed, maybe the ISO is corrupted or the cd/usb.

I'm running out of ideas, you can rarely find so many problems when installing. If you have a good ISO and a good cd/usb, installing the alternate 12.04 on your fakeraid should go just fine.
Stopping at the install software step means something is bothering it. It's not the same like not being able to install grub at the end, it doesn't even continue to that step.

I don't know what to recommend any more.

---

### Post by sdsdsd2 on 2012-12-04
> **darkod said:**
> /dev/sdd1 is your usb stick I believe. You can't use it as root partition.

If the 12.04 install failed, maybe the ISO is corrupted or the cd/usb.

I'm running out of ideas, you can rarely find so many problems when installing. If you have a good ISO and a good cd/usb, installing the alternate 12.04 on your fakeraid should go just fine.
Stopping at the install software step means something is bothering it. It's not the same like not being able to install grub at the end, it doesn't even continue to that step.

I don't know what to recommend any more.

The ISOs for every Ubuntu installation I have installed have matched hashes with the expected values, so it's definitely not the ISOs (unless a file can be corrupt even if the hashes match...).

How can I check if my flashdrive has poor data quality? A chkdsk?

So, since we're having all these problems, and the problems are likely due to the fakeraid, I was thinking perhaps it would be better for me to get rid of the fakeraid and instead put 2 of the 3 hard drives into a RAID 0. That would leave me with a lone hard drive for the Ubuntu installations. I have some questions about doing this and would like to get your opinion:
1. Would it be better for me to install Ubuntu or Windows 7 first?
2. Would it be better for me to use GRUB or Windows bootloader?
3. Is there a flavor of Ubuntu/linux that would be worth trying out before I do this (perhaps Xubuntu alternate 12.10 would work? [http://cdimage.ubuntu.com/xubuntu/daily/current/](http://cdimage.ubuntu.com/xubuntu/daily/current/) )
4. What do you think about this idea?

---

### Post by darkod on 2012-12-04
When you say 'get rid of the fakeraid and put 2 disks in RAID0', what do you mean exactly?

If you want both windows and ubuntu to access the data on those disks, the only choice is fakeraid. If you were using only linux, then software raid is recommended and works much better, but windows can't read that.

So, if you want both OSs to be able to use the array, you will still need to have fakeraid only it will be made up of 2 disks instead of 3.

To be honest running the 3 disk raid0 is probably a bad idea. I hope you are aware that if one disk dies, the data on all 3 disks is completely gone. That's how raid0 works.
You get a slightly faster transfer speed but the risk to the data is much bigger.

You can consider simply having all 3 disks as separate. You still have the same total storage space, but there is less risk for the data. If a disk dies, you lose only the data on that disk.

And by installing on a single disk instead of raid array, your install problems might go away.

The choice is yours whether you want to run 3 separate disks, or one disk for the OSs and a two disk raid0 array.

In any case, it's better to install win7 first and make the partition with the size you want to allocate to it. Leave the rest of the space as unallocated for ubuntu. After that install ubuntu.

For bootloader, I would use grub2 since windows bootloader can't boot ubuntu. It's much simpler, provided the installation goes fine of course. :)

---

### Post by sdsdsd2 on 2012-12-04
> **darkod said:**
> When you say 'get rid of the fakeraid and put 2 disks in RAID0', what do you mean exactly?

If you want both windows and ubuntu to access the data on those disks, the only choice is fakeraid. If you were using only linux, then software raid is recommended and works much better, but windows can't read that.

So, if you want both OSs to be able to use the array, you will still need to have fakeraid only it will be made up of 2 disks instead of 3.

To be honest running the 3 disk raid0 is probably a bad idea. I hope you are aware that if one disk dies, the data on all 3 disks is completely gone. That's how raid0 works.
You get a slightly faster transfer speed but the risk to the data is much bigger.

You can consider simply having all 3 disks as separate. You still have the same total storage space, but there is less risk for the data. If a disk dies, you lose only the data on that disk.

And by installing on a single disk instead of raid array, your install problems might go away.

The choice is yours whether you want to run 3 separate disks, or one disk for the OSs and a two disk raid0 array.

In any case, it's better to install win7 first and make the partition with the size you want to allocate to it. Leave the rest of the space as unallocated for ubuntu. After that install ubuntu.

For bootloader, I would use grub2 since windows bootloader can't boot ubuntu. It's much simpler, provided the installation goes fine of course. :)

I ended up putting 2 drives into a fakeraid and installed Windows 7 on them. I put a 100gb FAT32 partition on the fakeraid to share files between the OSes. I installed 12.10 on the drive not in the fakeraid and then installed GRUB. It's working great! I can get into both Ubuntu and Windows 7 no problem.

Thank you for your help.

PS. The original read speed of the three hard drives in RAID 0 was 240 mb/s. A lone drive (not in RAID 0) had read speeds of 110 mb/s, that's why I had three drives in RAID 0. I am aware of the implications of RAID 0.

---

### Post by darkod on 2012-12-05
Glad it works now. But you should have made the shared partition NTFS, uubntu can read and write to ntfs just fine. FAT32 will have limitations, like not supporting files over 4GB (if you have some big files), etc.

If the partition is still empty you can consider reformatting it as ntfs.

---

