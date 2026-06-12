---
title: "Installing ubuntu 14.04 beside other Linux Partitions"
date: 2014-05-21
forum: Installation &amp; Upgrades
---

### Post by sam-c on 2014-05-21
today I barely managed to recover from Re-Installing 14.04 on My Lenovo Desktop
Along side Ubuntu Studio Linuxmint etc,, Partitions Opensuse does a Recovary but Again seemed to clash with Ubuntu!
Thanks
Uncle Sam:)

---

### Post by Bashing-om on 2014-05-21
sam-c; Hello :

It is unclear what your objective is. Be aware there can only be one operating system controlling the boot process. Which ever system installs the boot code last is that controlling operating system. (your primary operating system).

So, show us what we are working with:
```

sudo fdisk -lu
sudo parted -l
sudo blkid
cat /etc/fstab ##from each operating system installed##

```
And tell us what is to be that "primary" operating system that all others are slaved to.

We will get this all sorted out ->
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by sam-c on 2014-05-21
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00021e30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    61441501    30719727   83  Linux
/dev/sda2        61442048    63075330      816641+  82  Linux swap / Solaris
/dev/sda3   *    63076350   312580347   124751999    5  Extended
/dev/sda5        69947392   108267519    19160064   8e  Linux LVM
/dev/sda6       147472384   183412797    17970207   83  Linux
/dev/sda7       247747269   267386879     9819805+  8e  Linux LVM
/dev/sda8       311531520   312580347      524414   82  Linux swap / Solaris
/dev/sda9       291813376   311530172     9858398+  8e  Linux LVM
/dev/sda10      267388928   291811327    12211200   8e  Linux LVM
/dev/sda11      211668992   247745220    18038114+  8e  Linux LVM
/dev/sda12      108269568   127423892     9577162+  83  Linux
/dev/sda13       63076352    69525503     3224576   8e  Linux LVM
/dev/sda14       69529383    69673914       72266   83  Linux
/dev/sda15       69673968    69947009      136521   8e  Linux LVM
/dev/sda16      127424512   139846199     6210844   83  Linux
/dev/sda17      139847680   147460095     3806208   82  Linux swap / Solaris
/dev/sda18      183414784   211656703    14120960   83  Linux

Partition table entries are not in disk order
sudo parted -l
Model: ATA ST3160815AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  31.5GB  31.5GB  primary   ext4
 2      31.5GB  32.3GB  836MB   primary   linux-swap(v1)
 3      32.3GB  160GB   128GB   extended                  boot
13      32.3GB  35.6GB  3302MB  logical                   lvm
14      35.6GB  35.7GB  74.0MB  logical   ext4
15      35.7GB  35.8GB  140MB   logical                   lvm
 5      35.8GB  55.4GB  19.6GB  logical                   lvm
12      55.4GB  65.2GB  9807MB  logical   ext4
16      65.2GB  71.6GB  6360MB  logical   ext4
17      71.6GB  75.5GB  3898MB  logical   linux-swap(v1)
 6      75.5GB  93.9GB  18.4GB  logical   ext4
18      93.9GB  108GB   14.5GB  logical   ext4
11      108GB   127GB   18.5GB  logical                   lvm
 7      127GB   137GB   10.1GB  logical                   lvm
10      137GB   149GB   12.5GB  logical                   lvm
 9      149GB   160GB   10.1GB  logical                   lvm
 8      160GB   160GB   537MB   logical   linux-swap(v1)

sudo blkid
/dev/sda1: UUID="6cc84b91-e819-4534-b804-9775faaf1235" TYPE="ext4" 
/dev/sda2: UUID="f19039c1-b59f-49a5-a015-2ffe4fe22d8c" TYPE="swap" 
/dev/sda5: UUID="JJwl2L-7TpQ-BjrY-74Dx-LzzX-vlba-v4fKOS" TYPE="LVM2_member" 
/dev/sda6: UUID="ca4fe93d-03f8-4c9e-8b7f-f181c56bceb2" TYPE="ext4" 
/dev/sda7: UUID="5n2mVB-LPMW-2hkE-iPEp-CMOt-de9A-bw8rBo" TYPE="LVM2_member" 
/dev/sda8: UUID="d20a4e4e-288e-4122-8e05-0cf92162e4fc" TYPE="swap" 
/dev/sda9: UUID="Lcfv2T-jKLd-8eLP-X8sH-FzUZ-xJ61-4oE3PO" TYPE="LVM2_member" 
/dev/sda10: UUID="L688Zs-XZZr-jg7f-Ob26-Dm0V-u0Q1-0jYrYs" TYPE="LVM2_member" 
/dev/sda11: UUID="3zUYHK-Qiiu-csO6-a7Sy-Z1YS-ZVZO-R0XHdU" TYPE="LVM2_member" 
/dev/sda12: UUID="7378c1c1-4ca8-4795-98ec-226ffa6e9fe8" TYPE="ext4" 
/dev/sda13: UUID="rJ6JoA-Wa4C-ZprC-7SQv-dvKX-6Fp0-OfP6Ew" TYPE="LVM2_member" 
/dev/sda14: UUID="c242a289-0a46-4b63-a5fe-cd98bfcedf69" TYPE="ext4" 
/dev/sda15: UUID="BsHXbH-mm8X-MjLh-pzdy-Nfdr-Nfyz-PWFkRl" TYPE="LVM2_member" 
/dev/sda16: UUID="f58aedc2-1e50-4354-bacc-0e8ed1b56e4d" TYPE="ext4" 
/dev/sda17: UUID="a2961922-37ce-472c-b8c6-1d669c28f318" TYPE="swap" 
/dev/sda18: UUID="6afbb0af-c909-4a7a-94ae-757b489a90a2" TYPE="ext4" 

cat /etc/fstab ##from each operating system installed##cat /etc/fstab ##from each operating system installed##
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda18 during installation
# swap was on /dev/sda8 during installation
UUID=d20a4e4e-288e-4122-8e05-0cf92162e4fc none            swap    sw              0       0
UUID=6afbb0af-c909-4a7a-94ae-757b489a90a2 /                    ext4       defaults              1 1
```

---

### Post by sam-c on 2014-05-21
this is the present situation NOT as it was before Trouble Started
Thanks
Uncle Sam

---

### Post by Bashing-om on 2014-05-21
sam-c; Welp;

There is bunches I do not know, but
> 
/dev/sda3   *    63076350   312580347   124751999    5  Extended

I do not see how this can possibly work, installing the boot code to an extended partition ! Do not see how the boot code could redirect to load an operating system.

The provided 'fstab' file shows booting as sda18, is 'sda18' outside the LVM(s)? 
What we might consider is to install the boot code to the MBR of 'sda' from the liveDVD, reboot into the install ( most likely to a grub prompt)
And from the grub prompt boot to the install on 'sda18' and complete the boot code installation.

Given that the install on 'sda18' is to be that "primary" operating system.

Please bear in mind I have limited experience with LVM, and this may turn out to be a learning experience for me also.

Just do not know about LVM, but ?????

---

### Post by coffeecat on 2014-05-21
Appears to be a support question, therefore not suitable for Ubuntu, Linux and Other OS Chat.

*Thread moved to **Installation & Upgrades**.*

---

### Post by oldfred on 2014-05-21
Grub does not use boot flag. Windows & Lilo boot loaders do use boot flag and a few BIOS want to see a boot flag on a primary partition. The extended partition is also a primary partition so having boot flag on it is ok, just very unusual.

If you installed Ubuntu with standard partitions not LVM, it un-installs the LVM driver. You need to reinstall that, and mount your other installs in LVMs. Then run this in Ubuntu.
 sudo apt-get install lvm2
Mount all the LVM installs the run this:

sudo update-grub

---

### Post by sam-c on 2014-06-02
WHAT IS THIS???
After doing sudo aptitude update and similar commands
I got this message:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7274A4DAE80D6BF5

Uncle Sam
Thanks:mad::guitar:

---

### Post by sam-c on 2014-06-02
sudo blkid
/dev/sda1: UUID="0b1529d0-3043-4381-8f9f-14d4886339a4" TYPE="ext4" 
/dev/sda2: UUID="f19039c1-b59f-49a5-a015-2ffe4fe22d8c" TYPE="swap" 
/dev/sda5: UUID="JJwl2L-7TpQ-BjrY-74Dx-LzzX-vlba-v4fKOS" TYPE="LVM2_member" 
/dev/sda6: UUID="ca4fe93d-03f8-4c9e-8b7f-f181c56bceb2" TYPE="ext4" 
/dev/sda7: UUID="5n2mVB-LPMW-2hkE-iPEp-CMOt-de9A-bw8rBo" TYPE="LVM2_member" 
/dev/sda8: UUID="d20a4e4e-288e-4122-8e05-0cf92162e4fc" TYPE="swap" 
/dev/sda9: UUID="Lcfv2T-jKLd-8eLP-X8sH-FzUZ-xJ61-4oE3PO" TYPE="LVM2_member" 
/dev/sda10: UUID="L688Zs-XZZr-jg7f-Ob26-Dm0V-u0Q1-0jYrYs" TYPE="LVM2_member" 
/dev/sda11: UUID="3zUYHK-Qiiu-csO6-a7Sy-Z1YS-ZVZO-R0XHdU" TYPE="LVM2_member" 
/dev/sda12: UUID="7378c1c1-4ca8-4795-98ec-226ffa6e9fe8" TYPE="ext4" 
/dev/sda13: UUID="rJ6JoA-Wa4C-ZprC-7SQv-dvKX-6Fp0-OfP6Ew" TYPE="LVM2_member" 
/dev/sda14: UUID="c242a289-0a46-4b63-a5fe-cd98bfcedf69" TYPE="ext4" 
/dev/sda15: UUID="BsHXbH-mm8X-MjLh-pzdy-Nfdr-Nfyz-PWFkRl" TYPE="LVM2_member" 
/dev/sda16: UUID="996252a4-a472-4ffa-b31d-bf2927526f16" TYPE="ext4" 
/dev/sda17: UUID="a2961922-37ce-472c-b8c6-1d669c28f318" TYPE="swap" 
/dev/sda18: UUID="6afbb0af-c909-4a7a-94ae-757b489a90a2" TYPE="ext4"

---

### Post by oldfred on 2014-06-02
So what ppa is that? Generally when upgrading you have to remove all ppa as they may not exist in the new version.

cat /etc/apt/sources.list
ls -l /etc/apt
ls -l /etc/apt/sources.list.d

---

### Post by sam-c on 2014-06-20
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
This was very Helpfull
Uncle Sam

---

