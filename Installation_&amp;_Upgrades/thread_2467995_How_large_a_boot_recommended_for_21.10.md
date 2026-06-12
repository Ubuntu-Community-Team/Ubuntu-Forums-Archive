---
title: "How large a /boot recommended for 21.10?"
date: 2021-10-15
forum: Installation &amp; Upgrades
---

### Post by raif on 2021-10-15
How large a /boot partition is now recommended for Ubunutu?

I set my boot partition at 500M as that seemed ample when I bought my laptop a couple of years ago and various internet searches said 300M was fine. But now when I try to upgrade I get the message:

```
The upgrade needs a total of 376 M free space on disk '/boot'.
```

I have removed all but the current kernel, set compression to xz but even then I'm nearly 50Mb short. So it seems like I'll need to resize to be able to upgrade rather than do a fresh install. What size boot is now sensible to have, as I don't want to need to resize again in a year or two?

NB it's a dual boot machine with W10 and encrypted using:

[https://help.ubuntu.com/community/ManualFullSystemEncryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption")

thanks!

---

### Post by yancek on 2021-10-15
If it's a dual boot with windows 10, it should be an EFI system, is that correct?

Do you also have a separate /boot partition in addition to the EFI partition?  If so, why?

Post the output of the 2 following commands here as they will list useful information so you can get some help.

```
sudo parted -l
df -h
```

---

### Post by raif on 2021-10-15
many thanks - NB I followed the advice in the link above on manual encryption.

```
odel: ATA HFS512G39MND-351 (scsi)
Disk /dev/sda: 512GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  274MB   273MB   fat32        EFI System Partition          boot, esp
 2      274MB   290MB   16.8MB               Microsoft reserved partition  msftres
 3      290MB   64.9GB  64.6GB  ntfs         Basic data partition          msftdata
 4      64.9GB  91.1GB  26.2GB               system
 5      91.1GB  512GB   421GB                data


Model: SMI USB DISK (scsi)
Disk /dev/sdb: 8053MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name       Flags
 1      32.8kB  3112MB  3112MB               ISO9660    hidden, msftdata
 2      3112MB  3116MB  4334kB               Appended2  boot, esp
 3      3116MB  3116MB  307kB                Gap1       hidden, msftdata
 4      3118MB  8053MB  4935MB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/data-home: 421GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  421GB  421GB  ext4


Error: /dev/mapper/data: unrecognised disk label
Model: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/data: 421GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/system-boot: 537MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  537MB  537MB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/system-root: 25.7GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  25.7GB  25.7GB  ext4


Error: /dev/mapper/system: unrecognised disk label
Model: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/system: 26.2GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 


```

and then 

```
tmpfs                               1.2G  2.2M  1.2G   1% /run
/dev/mapper/system-root              24G   18G  5.1G  78% /
tmpfs                               5.8G  187M  5.6G   4% /dev/shm
tmpfs                               5.0M  4.0K  5.0M   1% /run/lock
tmpfs                               4.0M     0  4.0M   0% /sys/fs/cgroup
/dev/mapper/system-boot             488M  134M  319M  30% /boot
/dev/sda1                           256M   40M  217M  16% /boot/efi
/dev/mapper/data-home               385G  235G  131G  65% /home
tmpfs                               1.2G  5.4M  1.2G   1% /run/user/1000
cryfs@/home/####/Private  133G  1.4G  131G   1% /home/#####/.SiriKali/Private

```

---

### Post by TheFu on 2021-10-15
There are different needs for different system setups.

/boot/efi is recommended to be 500MB by some respected people. I've never used more than 20MB, so it seems like 10x too much. The more you dual boot and the more different OSes, the larger the efi needs to be.

Most people wouldn't have a separate /boot/ partition.  I use LVM and sometimes I use encrypted LVM. Historically, that required a separate, unencrypted, /boot/ partition.  If that partition is shared between different Linuxen, then it may need to be larger than smaller.  Here's what I've setup on a few different systems:
Systems migrated from 12.04 --> 14.04 ---> 16.04 --> 18.04

```
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      ext2  720M  [COLOR="#008000"]140M[/COLOR]  544M  21% /boot

/dev/sdb1      ext2  720M  [COLOR="#008000"]165M[/COLOR]  519M  25% /boot

/dev/sde2      ext2  237M  [COLOR="#008000"]124M[/COLOR]  101M  56% /boot

```
20.04 system - no separate /boot needed:
```
/dev/mapper/vgubuntu--mate-root ext4   19G   11G  7.6G  58% /
/dev/vda1                       vfat  511M  [COLOR="#008000"]7.1M[/COLOR]  504M   2% /boot/efi
```

I've been planning to load up a 21.10 play VM today.  I'll do that now. Give me a 30 minutes.

---

### Post by ActionParsnip on 2021-10-15
What is the output of:
```

uname -a
dpkg -l | grep linux-image

```
Thanks

---

### Post by TheFu on 2021-10-15
Fresh 21.10 full Ubuntu Gnome4 DE install, where I selected LVM onto a 29G storage area:

```
$ df -Th
Filesystem                Type   Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu-root ext4    27G  6.5G   20G  26% /
/dev/vda2                 vfat   512M  5.3M  507M   2% /boot/efi
```

No separate boot needed or used by default.
```
$ sudo lvs
LV     VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
root   vgubuntu -wi-ao---- <27.54g                          
swap_1 vgubuntu -wi-ao---- 980.00m
```

```
$ du -shc /boot
du: cannot read directory '/boot/efi': Permission denied
71M     /boot
71M     total

```
If you clean up old kernels and only patch weekly, then 500MB should fine to hold 4 kernels (that 1 per week, for 1 month of kernels).  Just run **sudo apt autoremove** at least monthly. Every other week, if you want to be more cautious.  If you patch daily and get 7 new kernels a week, you'll either want a larger /boot/ or need to run the autoremove every 4 days or so.

---

### Post by GhX6GZMB on 2021-10-15
Interesting discussion.
I just checked my /boot, it's 207 MiB in size. CORRECTION: that's the directory. I don't have a /boot partition.
I've never done anything with it, so this is the size defined by the Lubuntu 20.04 installer (single-boot machine).

---

### Post by raif on 2021-10-16
Thanks, yes this is a useful discussion. I still don't understand why I'm getting the message that I need 376Mb in boot to install 21.10 though, that seems a lot based on the posts above. 

Using LVM shouldn't make a difference to space requirements surely? Though of course it might mean you need to partition differently and, as a result, might come up against partition size issues more often.

In terms of why I have a separate /boot, it's what I understood was needed for full manual encryption. If there's an simpler way to install Ubuntu on an encrypted hard drive, I'll do it when I get my next laptop. But hoping the performance benefits of 21.10 mean that date is further away ;)

uname -r gives

```

5.11.0-37-generic #41-Ubuntu SMP Mon Sep 20 16:39:20 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux 
```

and dpkg

```

ii  linux-image-5.11.0-37-generic                 5.11.0-37.41                                                         amd64        Signed kernel image generic
rc  linux-image-5.8.0-50-generic                  5.8.0-50.56                                                          amd64        Signed kernel image generic
ii  linux-image-generic                           5.11.0.37.39                                                         amd64        Generic Linux kernel image
rc  linux-image-unsigned-5.11.0-34-generic        5.11.0-34.36                                                         amd64        Linux kernel image for version 5.11.0 on 64 bit x86 SMP
rc  linux-image-unsigned-5.11.0-37-generic        5.11.0-37.41                                                         amd64        Linux kernel image for version 5.11.0 on 64 bit x86 SMP 

```

---

### Post by TheFu on 2021-10-16
What files are actually in /boot/?  Have any old kernels been abandoned there? Not removed?
Removed and purged aren't the same to the package manager.  It could be that the system has 4 kernels using space.  Purged kernels don't show up in the APT/dpkg lists.  Removed kernels may not remove headers and modules and extra-module packages as well.
For example:
```
$ dpkg -l linux-image*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version      Architecture Description
+++-=====================================-============-============-=================================
un  linux-image                           <none>       <none>       (no description available)
ii  linux-image-5.4.0-86-generic          5.4.0-86.97  amd64        Signed kernel image generic
ii  linux-image-5.4.0-88-generic          5.4.0-88.99  amd64        Signed kernel image generic
ii  linux-image-generic                   5.4.0.88.92  amd64        Generic Linux kernel image
un  linux-image-unsigned-5.4.0-86-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-88-generic <none>       <none>       (no description available)
```
Shows that there are only 2 kernels installed on this 20.04 (non-HWE) system. If I check /boot/, there are just 2 kernels:
```
-rw-------  1 root root    11776256 Sep 17 14:51 vmlinuz-5.4.0-86-generic
-rw-------  1 root root    11776256 Sep 23 12:41 vmlinuz-5.4.0-88-generic
```
There are some symbolic links to current and old, but those hit those 2 files above. Same for the initrd.img for each kernel.

By keeping 2 separate kernel lines, the package manager will plan to upgrade both of those lines with each upgrade command. Haven't both 5.8.x and 5.11.x kernel lines, effectively doubles the amount of storage in /boot/ required for an new kernel upgrade if both lines have updates.  By purging the 5.8.x line and all modules, headers, and other dependencies, you'll half the /boot storage needed.  [B]Did you do an do-release-upgrade or a fresh install? I think I know the answer.

[/B]I know nothing about manual encryption. It appears to me that there is an unsupported encryption mode being used, not LUKs, which is supported.
LVM lets us have 50 LVs, inside 1 partition, so that would actually help with the constraints and difficulties in altering partitions. Also, the entire PV is often placed inside a single encrypted container when LUKs is used, so we get the benefits of having the entire OS and data inside that PV, VG and all LVs encrypted.

I've never seen the point of manually encrypting the OS.  The only reason I can see that as a need would be in a dual boot setup, which I solve by using virtualization, so the VMs are all encrypted under the storage managed by the hostOS running the hypervisor.  

Manually encrypting external storage does have a place too, but that is relatively simple with LUKs to setup to allow automatic decryption when connected to our systems, but manual decryption when connected to foreign computers. [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it) has a guide for this.

---

### Post by hk42 on 2021-10-16
The most I have seen is three kernels plus two low latency kernels if you use ubuntu studio.
If you want to compile your own kernels you must have room to test them.
IMHO it doesn't deserve a separate partition.

---

