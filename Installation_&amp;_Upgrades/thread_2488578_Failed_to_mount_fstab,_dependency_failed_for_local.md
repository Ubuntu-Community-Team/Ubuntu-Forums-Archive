---
title: "Failed to mount fstab, dependency failed for local system"
date: 2023-07-09
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2023-07-09
I had to reinstall my Ubuntu  22.04 system after corruption crept into it. 

I can not work out why I am unable to log into the system and I can not  use the system properly, ie deal with emails etc. 

In order to cut down complications  I simplified the fstab to the following minimum, having removed the btrfs options and extra drives,  which I propose to bring back in once I can log in:

```
&#65279;# /etc/fstab: static file system information.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# SSD drive 

# p1:  /boot/efi was on /dev/nvme0n1p1 during installation
UUID=BD0A-F1F2  /boot/efi vfat    0 0

# p2:  / was on /dev/nvme0n1p2 during installation
UUID=c7a2681d-2d1c-471e-89c0-fc64793db19b /   btrfs rw,subvol=@ 0 0

# p3: /home was on /dev/nvme0n1p3 during installation
UUID=5bb8aa95-b657-4297-be5b-4352a09596b0 /home btrfs rw,subvol=@home 0  0

# p4 /dev/nvme0n1p4 Data
UUID=f5ab46ce-b3da-4e59-8f18-3418fe272a09  /media/robins/data_sdde btrfs  rw   0  0
```

1p4 partition has sub partitions in it.

The errors in the start up log are:

failed to mount etc/ fstab dependency failed for local file system


Here is the blkid:

```
/dev/nvme0n1p1: UUID="BD0A-F1F2" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="bf018dae-136c-554c-9be6-76169b6e7bac"
/dev/nvme0n1p2: UUID="c7a2681d-2d1c-471e-89c0-fc64793db19b" UUID_SUB="3618b3de-06a6-4396-80a8-e1ea66f3b72b" BLOCK_SIZE="4096" TYPE="btrfs" PARTUUID="2857f225-84d9-3844-aa0b-6cce43268fed"
/dev/nvme0n1p3: UUID="5bb8aa95-b657-4297-be5b-4352a09596b0" UUID_SUB="12d8a1ae-9e45-4467-99d1-bae0e01b1c53" BLOCK_SIZE="4096" TYPE="btrfs" PARTUUID="95aab85b-57b6-9742-be5b-4352a09596b0"
/dev/nvme0n1p4: LABEL="Data" UUID="f5ab46ce-b3da-4e59-8f18-3418fe272a09" UUID_SUB="62eb831e-e336-455d-9804-afed243f3c28" BLOCK_SIZE="4096" TYPE="btrfs" PARTUUID="ce46abf5-dab3-594e-8f18-3418fe272a09"
/dev/sda5: LABEL="mydocs" UUID="8d99bfc8-90ab-4488-b7da-87e7676aff19" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="00083267-05"
/dev/sda6: LABEL="Data inc AV" UUID="1a2e8d10-7b93-4de1-b551-31db6a621276" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="00083267-06"
/dev/sdb1: LABEL="hitachi 750gb" UUID="3c4f4688-4bd7-4262-a2b8-86f71bbd6d0b" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="0008ffd0-01"
/dev/sdb2: LABEL="Deju_dup_backup" UUID="c79b648e-48c5-45db-949f-a835928f3816" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="0008ffd0-02"
/dev/sdc1: UUID="32677e49-0894-4d3f-8cc4-7e27b74ac6f0" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="4950cc35-01"
/dev/sdd1: BLOCK_SIZE="2048" UUID="2023-02-23-04-13-44-00" LABEL="Ubuntu 22.04.2 LTS amd64" TYPE="iso9660" PARTLABEL="ISO9660" PARTUUID="a0891d7e-b930-4513-94d8-f629dbd637b2"
/dev/loop1: TYPE="squashfs"
/dev/sdd2: SEC_TYPE="msdos" LABEL_FATBOOT="ESP" LABEL="ESP" UUID="F7DB-4D56" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="Appended2" PARTUUID="a0891d7e-b930-4513-94db-f629dbd637b2"
/dev/sdd3: PARTLABEL="Gap1" PARTUUID="a0891d7e-b930-4513-94da-f629dbd637b2"
/dev/sdd4: LABEL="writable" UUID="d4d3bc52-1db3-11ee-acb8-a3c1c366bbbf" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="5db9e3cc-c98c-b145-847a-d0d988f40280"
/dev/loop8: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop0: TYPE="squashfs"
/dev/sde1: UUID="E0D0-35DF" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="a3aa5e04-01"
/dev/loop7: TYPE="squashfs"
/dev/sda7: UUID="6bbc8a5a-b488-49b6-904a-952e05463815" TYPE="swap" PARTUUID="00083267-07"
/dev/loop5: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
ubuntu@ubuntu:~$ 
```

Can you suggest what I can do to ensure that  fstab is loaded?

Robin

---

### Post by TheFu on 2023-07-10
It would really help if you'd have placed BTRFS into the thread title, so people with that knowledge see it.

I cannot help. I know very little about BRTFS.

---

### Post by Robbyx on 2023-07-10
Whilst waiting for help, I am trying to solve the problem myself.

Working  from the live system disk how do I manually load  those drives listed in the installed  fstab, so that I can see which ones are causing ubuntu not to load at startup?

---

### Post by #&amp;thj^% on 2023-07-10
Robbyx I wish I was behind your keyboard ATM, but I'm not so this makes it harder for both of us...
I recommend and this is something I rarely do but in your live environment install "gnome-disks"
After it's installed run:
```
sudo gnome-disks
```
Look for your missing or non starting disk and just add for now the "nofail" option  to fstab.

Then with the configuration button you can "edit mount options", feel free to give the destination of your mount point and it will be saved into the /etc/fstab automatically 

Note: the "nofail" option will cause the system not to hang if this mount point is not available, could be useful in case of potential unreachable filesystem on boot such as USB, NFS, etc.
[s]Unfortunately I'm super busy today so i won't check back any time soon today. (Sorry maybe tomorrow)[/s]
EDIT:Just like Christmas, I got the day off with pay...doesn't get any better.

---

### Post by Robbyx on 2023-07-10
I am very pleased that you have been able to answer my query. I have spending days trying to understand the fault. 

I went into Gparted, and there shone the error  for the nvmOn1p1 which is my EFI partiton,  I corrected it by installing mtools. That cleared the error when using that instance of the live cd,  but I have just looked again after a fresh login to the live cd and the error is back. 

[B]How can I install mtools on a system that  I can not log into through fstab? 
[/B]
As I am tired of making different variations on the options, rebooting into the main machine, finding it does not work, booting into the liveCD setting it up, making changes or searches. It has gone on for days. Could you give me a sample of the temp options  I should use?

There are two flavour that would help me, if you redrafted the fstab entries:
# p1:  /boot/efi was on /dev/nvme0n1p1 during installation
UUID=BD0A-F1F2  /boot/efi vfat umask=077   0 0

# p2:  / was on /dev/nvme0n1p2 during installation
UUID=c7a2681d-2d1c-471e-89c0-fc64793db19b /   btrfs rw,relatime,ssd,space_cache=v2,subvol=@ 0 0

---

### Post by #&amp;thj^% on 2023-07-10
I'm really not sure who your talking to, it couldn't be me as no where did I mention gparted??? 
Ok this will be a default install of "fstab"
```
/etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/vda2 during installation
UUID=9a97138c-ea15-4f0c-84e0-cd142bedd101 /               btrfs   defaults,subvol=@ 0       1
# /boot/efi was on /dev/vda1 during installation
UUID=7116-913B  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/vda2 during installation
UUID=9a97138c-ea15-4f0c-84e0-cd142bedd101 /home           btrfs   defaults,subvol=@home 0       2
/swapfile                                 none            swap    sw              0       0
```

I mean this in the nicest possible way, but Robbyx is BTRFS a good choice for you?
This is one of the most experience needed to run and maintain formats on Linux at this time.
```
sudo btrfs filesystem show /
Label: none  uuid: 9a97138c-ea15-4f0c-84e0-cd142bedd101
	Total devices 1 FS bytes used 10.93GiB
	devid    1 size 24.45GiB used 14.52GiB path /dev/vda2


```
@Robbyx after just now editing mt "fstab" to add "nofail" all is still good.
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/vda2 during installation
UUID=9a97138c-ea15-4f0c-84e0-cd142bedd101 /               btrfs   defaults,nofail,subvol=@ 0       1
# /boot/efi was on /dev/vda1 during installation
UUID=7116-913B  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/vda2 during installation
UUID=9a97138c-ea15-4f0c-84e0-cd142bedd101 /home           btrfs   default,nofail,s,subvol=@home 0       2
/swapfile                                 none            swap    sw              0       0

```
Nothing fancy just nice and stable, If I want more mount options i will add as needed.
IMPORTANT**
[list]
[*]File /etc/mtab is maintained by the operating system. Don't edit it.

[*]File /etc/fstab defines what should be mounted. It is read at system start.[/list]

When I add an extra disk to a system that should be mounted at system start I add it to /etc/fstab.

To check the correctness of the updated /etc/fstab I use the command mount -a. That reads /etc/fstab as system start, it mounts filesytems that aren'nt yet mounted.
```
 df -T
Filesystem     Type  1K-blocks     Used Available Use% Mounted on
tmpfs          tmpfs    397912     1276    396636   1% /run
/dev/vda2      btrfs  25641984 11662744  12805624  48% /
tmpfs          tmpfs   1989544        0   1989544   0% /dev/shm
tmpfs          tmpfs      5120        8      5112   1% /run/lock
/dev/vda2      btrfs  25641984 11662744  12805624  48% /home
/dev/vda1      vfat     569208     6216    562992   2% /boot/efi
tmpfs          tmpfs    397908       88    397820   1% /run/user/1000

```
It gives an error when the mountpoint is missing or the device is missing.

---

### Post by Robbyx on 2023-07-10
I had run gparted just before you responded to my posting. It was part of my attempt to find a solution to what underlying problems had caused none of my fstab listed drives loading after a reinstall.  It turned out to be a useful tool. No one including you had told me to run it, it was a coincidence and showed up a cause of the problems I have been having. I reported to you so that you may be able to incorporate my finding in your response. 

As from when we originally resolved the installation months ago, which I as sure you  accept  involved underlying  problems  that were  obscure and difficult to resolve.It was not a standard problem, I have been running BTRFS with no problems and no cries for  help.  The reason why I am determined to use btrfs is because it has many features  which are important for the stability of my system. It is also considered by many to be the next file system that will be offered by Ubuntu.   Unfortunately  my current problem did not have any postings I could find, by way of extensive searching,  that would help find a resolution. I am most grateful for your renewed help and hope that your advice will lead to a full resolution. I am now going to try out your suggestion.

---

### Post by #&amp;thj^% on 2023-07-10
That bit of history is good to know, now I'm aware of your driven goal. :)
I'll never fault anyone with such drive and determination, in fact I applaud and support your quest here.

---

### Post by Robbyx on 2023-07-10
I had reinstalled the o/s on a number of occasions during the previous days, but none of them resolved my problem of the fstab not working, even the default fstab would not load the o/s.

---

### Post by Robbyx on 2023-07-10
I will report back tomorrow on the changes you suggested to  change the fstab to the standard format.

---

### Post by Robbyx on 2023-07-11
I decided to do a reinstall of Ubuntu 22.04, on the grounds that it was fairly clear that my trouble was primarily from the loss of the dos tools. I noticed that the other btrfs directories were getting loaded, but not the EFI. Despite running mtools from the live cd it was disappearing on reboot, which is natural because I was installing it on  the live cd. but the fact that it was not appearing to be in the main installation caused me to assume that it should be there, because it was difficult to put mtools  into the main system if the main system  was not running. 

The reinstall went smoothly but for a bug fault towards the end. A report was sent to Ubuntu. 

I then restarted Ubuntu and all loaded. I was able to run Ubuntu normally. All was healed. Clearly fstab had loaded, but what then happened was there was an update of Libreoffice , may be others. I was told to restart, which I did. There after I could not get fully into Ubuntu There was an indication of loading, which just seemed to freeze as indicated by the spinning disk disappearing.  I could not get into the desktop 

The following show no errors:
A full memory test
A non destructive bad blocks test of the BTRFS partitions.

What tests if any should I apply next? An present I am back to working off the live cd, which is a nuisance. Is 23.04 now reliable? It was not when I decided to go back to 22.04 from 23.04 some months ago.

---

### Post by #&amp;thj^% on 2023-07-11
This is now giving me anxiety LOL
Can you get to a terminal booting the real install? Or Advanced Options>>recovery?
Boy I need to put my thinking cap on for this one.

---

### Post by Robbyx on 2023-07-11
> Can you get to a terminal booting the real install? Or Advanced Options>>recovery?

I did get into the real install and as I indicated it worked perfectly until after the update of libreoffice, which I did not even run, because I had to restart the installation. I can still try to login but the freeze happens each time. 

To which advanced option do you refer for recovery?

---

### Post by #&amp;thj^% on 2023-07-11
[IMG]https://i.stack.imgur.com/GCPLl.png[/IMG]
This one
Then this one
[IMG]https://i.stack.imgur.com/6PEl9.png[/IMG]

---

### Post by Robbyx on 2023-07-11
Which advanced options should I try?

---

### Post by Robbyx on 2023-07-11
Which advanced options should I try?

I am able to load Ubuntu, it that it gets stuck as if it trying to install the previous downloads.

---

### Post by #&amp;thj^% on 2023-07-11
recovery, with root shell
```
sudo fsck
```
bless your heart you have no idea how hard this is for me, I need to be you for a few minutes. :)
EDIT: you will have to run that against a certain "/dev/sdda" or what ever the drive is

---

### Post by Robbyx on 2023-07-12
The advanced options was a good idea. There were some faults that did not look important, but I ran the various options and corrected them but I still could not log in.

I decided to reinstall Ub 22.04 without reformating.

I ran the advanced options on the reinstalled drive and got a blank screen with a flashing cursor. I also checked the sha256 codes, for the live-installation usb,   and the internal codes for the actual install.   

Gparted shows the p1 dos partiton for EFI is not readable due to missing mtools (as before). I believe it is possible to go from the live-system to the installed one, as if I were logged into the installed one, but I forget the command lines. 


Reading advice I decided to install boot-repair onto the live system.  I hoping this will give us a better way of correcting the failure to boot. 

paste.ubuntu.com/p/3Q76Dt66p2

---

### Post by #&amp;thj^% on 2023-07-12
Wow this system is very confused as shown by:
```
==================== sdf: Location of files loaded by Grub =====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sdf


BTRFS detected on nvme0n1p3
ls nvme0n1p3:

---
mount /dev/nvme0n1p3 /mnt/boot-sav/nvme0n1p3/ 
MOUNTCODE=0
---
os-prober before @ subvol mount:

---
BTRFS detected on nvme0n1p4
ls nvme0n1p4:

---
mount /dev/nvme0n1p4 /mnt/boot-sav/nvme0n1p4/ 
MOUNTCODE=0
---
os-prober before @ subvol mount:

---


Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.

```
Robbin will you please run the system-info script, I'm going to ask another friend to look here as well.
Short how to run the script:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details
```
The Page if your uncertain is found here: [https://ubuntuforums.org/showthread.php?t=2465764](https://ubuntuforums.org/showthread.php?t=2465764)
Paste back the link again from the script so we can look at it.

---

### Post by Robbyx on 2023-07-12
This is what I also posted  to  MAFoElffen's account

1fallen asked me to post the system report  file to this thread:

[https://paste.ubuntu.com/p/3pfYwqBv52/](https://paste.ubuntu.com/p/3pfYwqBv52/)



This is a repeat of the  boot repair support report:

[https://paste.ubuntu.com/p/ttPp74n44w/](https://paste.ubuntu.com/p/ttPp74n44w/)

Robin

---

### Post by #&amp;thj^% on 2023-07-12
> **Robbyx said:**
> 1fallen asked me to post the boot-repair  report file to this thread:

[https://paste.ubuntu.com/p/3pfYwqBv52/](https://paste.ubuntu.com/p/3pfYwqBv52/)

Good Job Robbyx, and while i go over it please consider with an open mind whats below.

Robbyx like I had mentioned in your first thread for btrfs/fstab The only systems I would run btrfs on is Arch, Synology, and Netgear NAS devices which crucially layer btrfs on top of traditional systems like LVM to avoid these pitfalls.

For Ubuntu I only run ZFS on root, and that's not a suggestion but point of fact.
Or I'll use LVM2 on ext4, and this my attempt to convert you to that. ;)
```
sudo pvs
  PV         VG      Fmt  Attr PSize    PFree
  /dev/sdb2  vglinux lvm2 a--  <465.26g    0 

```
it has a well founded and stable base. (BTRFS reminds me of building a house of cards)

Btrfs' refusal to mount degraded, automatic mounting of stale disks, and lack of automatic stale disk repair/recovery do not add up to a sane way to manage a "redundant" storage system.

I want you to succeed here, without pounding your head against the same brick wall. (Peace and Tranquility should be our goals here.)

---

### Post by #&amp;thj^% on 2023-07-12
This is rather large for a swap
```
_sdb7       39.5G swap                              [SWAP]   
```
I see you still haven't added "nofail" to fstab, but no matter it wouldn't help here.
Also very curious about some installed packages 
```
zfs-initramfs
zfs-zed
zfsutils-linux
zsys
```
Are you playing with ZFS and storage? 
And it looks to me like grub gets lost somewhere. (more on that later)
I can't find a way to help here, this is like putting a jig saw puzzle together blindly.

Could you shed some light on this:
```
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb4            2048 488396799 488394752 232.9G  5 Extended
/dev/sdb5            4096 185479167 185475072  88.4G 83 Linux
/dev/sdb6       268263424 488396799 220133376   105G 83 Linux
/dev/sdb7       185481216 268261375  82780160  39.5G 82 Linux swap / Solaris
```

---

### Post by MAFoElffen on 2023-07-13
I look at this and... What the heck?

I have spent most the day working on a BTRFS-on-Root with a BTRFS internal RAID10 "/" and a BTRFS internal RAID6 /data, and it's having problems just with mounting the subvols for @home, @etc, @opt, and @var back into the filesystem... It boots, but it has problems. I will work at it more another day. Do I expect you to do that? Noooooo. That is advanced thigs that take some tweaking to work out. 

BTRFS is experimental. And it is not stable, especially the internal RAID.

I can tell you that I am a contributor to the 'boot-info' script, and it does not support BTRFS nor BTRFS subvolumes. Heck, I gave Yann how I mounted and rescued LUKS and ZFS systems, and that is the why that is there and worked out for most basic installs of that. I am building more BTRFS systems as test cases, build isn't there yet...

If you need to reinstall grub, it's going to take manually mounting it in /mnt, putting all the jigsaw pieces back together "as you built them"... Which there are some many variables what a User "might" do with that... Astronomical.

I could explain it... But you need to be involved in what you did, and what commands you used when you made the pieces.

Tell what each of these partitions are...
```

nvme0n1     894.3G                                                                                      Force MP510
|_nvme0n1p1   999M vfat                                                                                 
|_nvme0n1p2  51.2G btrfs                             /media/ubuntu/c7a2681d-2d1c-471e-89c0-fc64793db19b 
|_nvme0n1p3 199.1G btrfs                                                                                
|_nvme0n1p4   643G btrfs    Data                                                                        

```
nvme01np1 is EFI in fdisk...
nvme01np2 looks like it might be a /
nvme01np3 looks like it might be a /home
nvme01np4 looks like it is your /data
Is the only other Linux the two USB's you had plugged in at the same time? You should only have one at a time please. Use the Ubuntu 22.04.2 LiveUSB...

Try this booted from it, "Try" and from a terminal... This is just based on the assumptions above
```

sudo su -
apt update
apt install btrfs-progs
mount -t btrfs -o noatime,compress=lzo,space_cache=v2  /dev/nvme0n1p2 /mnt

```
Then do 
```

ls -lah /mnt/*

```
Tell me what you see... Is it "@"?

---

### Post by Robbyx on 2023-07-13
I have been looking at the summary report you quoted from at #19. Are you sure it is so muddled?

sdf is the installation usb drive containing the Ubuntu 22.04.02 image that would not be available if mounting from the hD system. 

I have tried to run the boot repair app again to get a new report. It refuses with no reason other than it can not be done.

As far as I can tell from your extract at #19  the efi system is only on the btrfs a 1p1.

gparted reports on that drive:

[I]Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for fat32 file system support:  dosfstools, mtools.[/I]

Can you remind me how I can install mtools on 1p1 from the live system. 

I have not heard back from your friend. The bastebin times out very quickly. I suspect he did not have a chance to view it. I am unsure if I can upload another copy for him to review, because of the refusal to produce one by boot repair

Robin

---

### Post by Robbyx on 2023-07-13
I believe I can get another report from repair-disk. I needed to turn off csm compatability

Here is a report on the grubs. Can you see a second one on the non usb drives? There was a suggestion that 
1p2 had some boot information but I  can not now see it.


```

boot-repair-4ppa2056                                              [20230713_1111]

============================= Boot Repair Summary ==============================


BTRFS detected on nvme0n1p3
ls nvme0n1p3:

---
mount /dev/nvme0n1p3 /mnt/boot-sav/nvme0n1p3/ 
MOUNTCODE=0
---
os-prober before @ subvol mount:

---
BTRFS detected on nvme0n1p4
ls nvme0n1p4:

---
mount /dev/nvme0n1p4 /mnt/boot-sav/nvme0n1p4/ 
MOUNTCODE=0
---
os-prober before @ subvol mount:

---


Default settings: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.

User settings: _________________________________________________________________

No OS to fix.
The settings chosen by the user will not act on the boot.





============================ Boot Info After Repair ============================

 => Grub2 (v1.99-2.00) is installed in the MBR of /dev/nvme0n1 and looks at 
    sector 1 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /@/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    zstd diskfilter raid6rec crypto lzopio gcry_crc gzio btrfs part_msdos 
    biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid ed0a7043-7cb0-4710-9175-7f53d26bb6d1 root 
    set prefix=($root)'/@/boot/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /@/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    zstd diskfilter raid6rec crypto lzopio gcry_crc gzio btrfs part_msdos 
    biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid ed0a7043-7cb0-4710-9175-7f53d26bb6d1 root 
    set prefix=($root)'/@/boot/grub'
    
    ---------------------------------------------------------------------------
 => libparted MBR boot code is installed in the MBR of /dev/sdc.
 => Syslinux MBR (4.04-4.07) is installed in the MBR of /dev/sdd.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bootx64.efi /efi/BOOT/fbx64.efi 
                       /efi/BOOT/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       btrfs
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

nvme0n1p3: _____________________________________________________________________

    File system:       btrfs
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

nvme0n1p4: _____________________________________________________________________

    File system:       btrfs
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 3238184 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdd1 starts at sector 
                       0. But according to the info from fdisk, sdd1 starts 
                       at sector 32.
    Operating System:  
    Boot files:        /ldlinux.sys

sde: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sde and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sde: /dev/sde already mounted or mount point busy.


================================ 0 OS detected =================================


================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Kaveri [Radeon R7 Graphics] from Advanced Micro Devices, Inc. [AMD/ATI]
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.2 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: P4.20A(4.6) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0015
Timeout: 1 seconds
BootOrder: 0015,0007,0009,0000,0014,0013
Boot0000* ubuntu	HD(1,GPT,bf018dae-136c-554c-9be6-76169b6e7bac,0x800,0x1f3800)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0007* UEFI: Built-in EFI Shell 	VenMedia(5023b95c-db26-429b-a648-bd47664c8012)..BO
Boot0009* UEFI OS	HD(1,GPT,bf018dae-136c-554c-9be6-76169b6e7bac,0x800,0x1f3800)/File(\EFI\BOOT\BOOTX64.EFI)..BO
Boot0013* UEFI: KingstonDataTraveler 2.0PMAP	PciRoot(0x0)/Pci(0x13,0x2)/USB(2,0)/HD(1,MBR,0xa3aa5e04,0x20,0x3d3fe0)..BO
Boot0014* ubuntu	HD(1,GPT,bf018dae-136c-554c-9be6-76169b6e7bac,0x800,0x1f3800)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO
Boot0015* UEFI: KingstonDataTraveler 3.0PMAP	PciRoot(0x0)/Pci(0x10,0x0)/USB(0,0)/USB(1,0)/HD(2,GPT,a0891d7e-b930-4513-94db-f629dbd637b2,0x92b094,0x2754)..BO

64349b3622c65f495a99dbf6102496e3   nvme0n1p1/BOOT/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   nvme0n1p1/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p1/BOOT/mmx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   nvme0n1p1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   nvme0n1p1/ubuntu/shimx64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes
sda	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes
sdb	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes
sdc	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes
sdd	: notGPT,	no-BIOSboot,	has---ESP, 	liveusb,	not-mmc, no-os,	no-wind,	32 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
nvme0n1p2	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
nvme0n1p3	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
nvme0n1p4	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sda5	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda6	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sdb1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sdb2	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sdc1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sdd1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far

Partitions info (2/3): _________________________________________________________

nvme0n1p1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme0n1p2	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme0n1p3	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme0n1p4	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda5	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda6	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdb1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdb2	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdc1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdd1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
nvme0n1p2	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
nvme0n1p3	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
nvme0n1p4	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
sda5	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda6	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sdb1	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdb
sdb2	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdb
sdc1	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdc
sdd1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdd

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 894.25 GiB, 960197124096 bytes, 1875385008 sectors
Disk identifier: 05016608-8366-0455-00C7-041000894402
              Start        End    Sectors   Size Type
nvme0n1p1      2048    2047999    2045952   999M EFI System
nvme0n1p2   2048000  109320191  107272192  51.2G Linux filesystem
nvme0n1p3 109320192  526884863  417564672 199.1G Linux filesystem
nvme0n1p4 526884864 1875384319 1348499456   643G Linux filesystem
Disk sda: 232.89 GiB, 250059350016 bytes, 488397168 sectors
Disk identifier: 0x00083267
      Boot     Start       End   Sectors   Size Id Type
sda4            2048 488396799 488394752 232.9G  5 Extended
sda5            4096 185479167 185475072  88.4G 83 Linux
sda6       268263424 488396799 220133376   105G 83 Linux
sda7       185481216 268261375  82780160  39.5G 82 Linux swap / Solaris
Partition table entries are not in disk order.
Disk sdb: 698.64 GiB, 750156374016 bytes, 1465149168 sectors
Disk identifier: 0x0008ffd0
      Boot      Start        End    Sectors   Size Id Type
sdb1             2048 1352790015 1352787968 645.1G 83 Linux
sdb2       1352790016 1465147391  112357376  53.6G 83 Linux
Disk sdc: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0x4950cc35
      Boot Start       End   Sectors   Size Id Type
sdc1        2048 976773119 976771072 465.8G 83 Linux
Disk sdd: 1.91 GiB, 2055208960 bytes, 4014080 sectors
Disk identifier: 0xa3aa5e04
      Boot Start     End Sectors  Size Id Type
sdd1  *       32 4014079 4014048  1.9G  c W95 FAT32 (LBA)
Disk sde: 14.46 GiB, 15524167680 bytes, 30320640 sectors
Disk identifier: A0891D7E-B930-4513-94D9-F629DBD637B2
        Start      End  Sectors  Size Type
sde1       64  9613459  9613396  4.6G Microsoft basic data
sde2  9613460  9623527    10068  4.9M EFI System
sde3  9623528  9624127      600  300K Microsoft basic data
sde4  9625600 30320576 20694977  9.9G Linux filesystem

parted -lm (filtered): _________________________________________________________

sda:250GB:scsi:512:512:msdos:ATA Samsung SSD 840:;
4:1049kB:250GB:250GB:::;
5:2097kB:95.0GB:95.0GB:ext4::;
7:95.0GB:137GB:42.4GB:linux-swap(v1)::;
6:137GB:250GB:113GB:ext4::;
sdb:750GB:scsi:512:512:msdos:ATA Hitachi HDS72107:;
1:1049kB:693GB:693GB:ext4::;
2:693GB:750GB:57.5GB:ext4::;
sdc:500GB:scsi:512:512:msdos:ATA WDC WD5000AAKX-0:;
1:1049kB:500GB:500GB:ext4::;
sdd:2055MB:scsi:512:512:msdos:Kingston DataTraveler 2.0:;
1:16.4kB:2055MB:2055MB:fat32::boot, lba;
sde:15.5GB:scsi:512:512:gpt:Kingston DataTraveler 3.0:;
1:32.8kB:4922MB:4922MB::ISO9660:hidden, msftdata;
2:4922MB:4927MB:5155kB::Appended2:boot, esp;
3:4927MB:4928MB:307kB::Gap1:hidden, msftdata;
4:4928MB:15.5GB:10.6GB:ext4::;
nvme0n1:960GB:nvme:512:512:gpt:Force MP510:;
1:1049kB:1049MB:1048MB:fat32:EFI System Partition:boot, esp;
2:1049MB:56.0GB:54.9GB:btrfs::;
3:56.0GB:270GB:214GB:btrfs::;
4:270GB:960GB:690GB:btrfs::;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                     
&#9500;&#9472;sda4                                                    00083267-04                                                   
&#9500;&#9472;sda5      ext4     8d99bfc8-90ab-4488-b7da-87e7676aff19 00083267-05                          mydocs                   
&#9500;&#9472;sda6      ext4     1a2e8d10-7b93-4de1-b551-31db6a621276 00083267-06                          Data inc AV              
&#9492;&#9472;sda7      swap     6bbc8a5a-b488-49b6-904a-952e05463815 00083267-07                                                   
sdb                                                                                                                     
&#9500;&#9472;sdb1      ext4     3c4f4688-4bd7-4262-a2b8-86f71bbd6d0b 0008ffd0-01                          hitachi 750gb            
&#9492;&#9472;sdb2      ext4     c79b648e-48c5-45db-949f-a835928f3816 0008ffd0-02                          Deju_dup_backup          
sdc                                                                                                                     
&#9492;&#9472;sdc1      ext4     32677e49-0894-4d3f-8cc4-7e27b74ac6f0 4950cc35-01                                                   
sdd                                                                                                                     
&#9492;&#9472;sdd1      vfat     E0D0-35DF                            a3aa5e04-01                                                   
sde         iso9660  2023-02-23-04-13-44-00                                                    Ubuntu 22.04.2 LTS amd64 
&#9500;&#9472;sde1      iso9660  2023-02-23-04-13-44-00               a0891d7e-b930-4513-94d8-f629dbd637b2 Ubuntu 22.04.2 LTS amd64 ISO9660
&#9500;&#9472;sde2      vfat     F7DB-4D56                            a0891d7e-b930-4513-94db-f629dbd637b2 ESP                      Appended2
&#9500;&#9472;sde3                                                    a0891d7e-b930-4513-94da-f629dbd637b2                          Gap1
&#9492;&#9472;sde4      ext4     d4d3bc52-1db3-11ee-acb8-a3c1c366bbbf 5db9e3cc-c98c-b145-847a-d0d988f40280 writable                 
nvme0n1                                                                                                                 
&#9500;&#9472;nvme0n1p1 vfat     BD0A-F1F2                            bf018dae-136c-554c-9be6-76169b6e7bac                          EFI System Partition
&#9500;&#9472;nvme0n1p2 btrfs    c7a2681d-2d1c-471e-89c0-fc64793db19b 2857f225-84d9-3844-aa0b-6cce43268fed                          
&#9500;&#9472;nvme0n1p3 btrfs    5bb8aa95-b657-4297-be5b-4352a09596b0 95aab85b-57b6-9742-be5b-4352a09596b0                          
&#9492;&#9472;nvme0n1p4 btrfs    f5ab46ce-b3da-4e59-8f18-3418fe272a09 ce46abf5-dab3-594e-8f18-3418fe272a09 Data                     

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[/install-logs-2023-07-13.2/crash]   8.4G   7% /var/crash
/dev/disk/by-label/writable[/install-logs-2023-07-13.2/log]     8.4G   7% /var/log
/dev/nvme0n1p1                                                  991M   1% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p2                                                 21.3G  52% /media/ubuntu/c7a2681d-2d1c-471e-89c0-fc64793db19b
/dev/nvme0n1p3                                                148.4G  25% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4                                                 86.1G  87% /mnt/boot-sav/nvme0n1p4
/dev/sda5                                                      45.3G  43% /mnt/boot-sav/sda5
/dev/sda6                                                        78G  19% /mnt/boot-sav/sda6
/dev/sdb1                                                          0  96% /mnt/boot-sav/sdb1
/dev/sdb2                                                      30.3G  37% /mnt/boot-sav/sdb2
/dev/sdc1                                                     291.5G  31% /mnt/boot-sav/sdc1
/dev/sdd1                                                       1.9G   1% /media/ubuntu/E0D0-35DF
/dev/sde1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________


=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid c7a2681d-2d1c-471e-89c0-fc64793db19b root 
set prefix=($root)'/@/boot/grub'
configfile $prefix/grub.cfg

================== sdd1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             ldlinux.sys                                    1

```

---

### Post by MAFoElffen on 2023-07-13
You did not answer my questions from post #23. Please stay focused.

I can see what I need so far from your other reports. I need other information beyond that, which is not possible from the boot-repair script in it's present form.

The boot-repair script can only report so much on BTRFS. And it cannot fix it. You read that in my last post right? 

And yes... I can see 2 the two bootable USB's, I can see where it has both MBR and EFI boot methods applied to it, where you tried to use it ____ to fix 'whatever'. Do not do that. Stop and follow directions please. I don't want you to lose access to your computer again

---

### Post by Robbyx on 2023-07-13
I did not realise I had two unanswered replies, Thank you. I am not able to read any emails in thunderbird,  as I am working off the live install. 

I agree it is very tiring and time consuming  to have the type of problems I am experiencing with my Ubuntu system running  BTRFS, I agree I  should change to another file system, if no easy solution is to be found, but I have had the BTRFS working well for a few months at least. I fear it will involve a lot of work and many problems  to change, only to find the failure to boot returns, because it is not directly the fault of BTRFS and thus a change of disk format will not correct the problem of booting the system.   

In attempt to find why the system was not booting, I looked at the drives with gparted.  It gave the  warning set out below. about missing files, and so I  installed mtools. The system worked perfectly with  Ubuntu loading  as it should.  Then an install of the latest Libre office updates  froze the machine. No longer would it boot up to the desktop. Even now after a very recent reinstall of the 22.04, the EFI partition is showing the same warning in gparted and the hd system is not loading  booting fully into the os.  

Assuming I can only access Ubuntu 22.04 via the live installation, can you give me the cl to permanently install mtools onto the os?


**Warning**
> Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for fat32 file system support:  dosfstools, mtools.

Currently I believe the major cause of the failure to boot is due to the missing dos tools.

[I]R: I have taken the  following quotes from the grub report available in  the advanced options in disk-repair:
[/I]
> 
[B]============================ Boot Info After Repair ============================
[/B]

**nvme0n1p1**: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bootx64.efi /efi/BOOT/fbx64.efi 
                       /efi/BOOT/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg


sdd1: __________________________________________________________________________

*RS: sdda is a USB stick that is not installed with Ubuntu. It is used for data backup of a few files.*

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 3238184 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdd1 starts at sector 
                       0. But according to the info from fdisk, sdd1 starts 
                       at sector 32.
    Operating System:  
    Boot files:        /ldlinux.sys


sde: ___________________________________________________________________________
*R: sde is the 22.04 usb installer* 

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sde and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sde: /dev/sde already mounted or mount point busy.


 => Grub2 (v1.99-2.00) is installed in the MBR of **/dev/nvme0n1** and looks at 
    sector 1 of the same hard drive for core.img, but[B] core.img can not be 
    found at this location.[/B]
 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /@/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    zstd diskfilter raid6rec crypto lzopio gcry_crc gzio btrfs part_msdos 
    biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid ed0a7043-7cb0-4710-9175-7f53d26bb6d1 root 
    set prefix=($root)'/@/boot/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /@/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    zstd diskfilter raid6rec crypto lzopio gcry_crc gzio btrfs part_msdos 
    biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid ed0a7043-7cb0-4710-9175-7f53d26bb6d1 root 
    set prefix=($root)'/@/boot/grub'
    
    ---------------------------------------------------------------------------
 => libparted MBR boot code is installed in the MBR of /dev/sdc.
 => Syslinux MBR (4.04-4.07) is installed in the MBR of /dev/sdd.

End of extracts. I can send you the full report if you require it. 

[B]
Answers to MAFoElffen's questions:[/B]

[QUOTE]
**Is the only other Linux the two USB's you had plugged in at the same time? You should only have one at a time please. Use the Ubuntu 22.04.2 LiveUSB...**
[/QUOTE

*R: Yes and noted, but one of the usb sticks may not have the os on it.*

```
ubuntu@ubuntu:~$ ls -lah /mnt/*
/mnt/BootInfo:
total 0
drwxr-xr-x 3 root root 60 Jul 13 11:12 .
drwxr-xr-x 1 root root 80 Jul 13 11:12 ..
drwxr-xr-x 3 root root 60 Jul 13 11:12 FD

/mnt/boot-sav:
total 0
drwxr-xr-x 10 root root 200 Jul 13 11:11 .
drwxr-xr-x  1 root root  80 Jul 13 11:12 ..
drwxr-xr-x  2 root root  40 Jul 13 11:11 nvme0n1p1
drwxr-xr-x  2 root root  40 Jul 13 11:11 nvme0n1p3
drwxr-xr-x  2 root root  40 Jul 13 11:11 nvme0n1p4
drwxr-xr-x  2 root root  40 Jul 13 11:11 sda5
drwxr-xr-x  2 root root  40 Jul 13 11:11 sda6
drwxr-xr-x  2 root root  40 Jul 13 11:11 sdb1
drwxr-xr-x  2 root root  40 Jul 13 11:11 sdb2
drwxr-xr-x  2 root root  40 Jul 13 11:11 sdc1

```


```
ubuntu@ubuntu:~$ sudo su -
apt update
apt install btrfs-progs
mount -t -o noatime,compress=lzo,space_cache=v2  /dev/nvme0n1p2 /mnt
root@ubuntu:~# apt update
apt install btrfs-progs
mount -t -o noatime,compress=lzo,space_cache=v2  /dev/nvme0n1p2 /mnt
Ign:1 cdrom://Ubuntu 22.04.2 LTS _Jammy Jellyfish_ - Release amd64 (20230223) jammy InRelease
Hit:2 cdrom://Ubuntu 22.04.2 LTS _Jammy Jellyfish_ - Release amd64 (20230223) jammy Release
Get:3 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Hit:4 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu jammy InRelease                                                          
Hit:6 http://archive.ubuntu.com/ubuntu jammy InRelease                                                       
Get:7 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]
Get:8 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages [565 kB]
Get:9 http://security.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [41.6 kB]
Get:10 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 DEP-11 Metadata [21.9 kB]   
Get:11 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [790 kB]                   
Get:12 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [99.7 kB]
Get:13 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [15.4 kB]
Get:14 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [942 kB]
Get:15 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [274 kB]
Fetched 2,978 kB in 1s (2,219 kB/s)                                
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
325 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
btrfs-progs is already the newest version (5.16.2-1).
0 upgraded, 0 newly installed, 0 to remove and 325 not upgraded.
[B]mount: bad usage
Try 'mount --help' for more information.[/B]
root@ubuntu:~# 


```
[I]R:I assume  your code is updating the main system not the live install. 
R: If still required please give me the replacement for the rejected  mount syntax.
Once received  I will continue with answering your last point is:     ls -lah /mnt/*
[/I]

Robin

---

### Post by MAFoElffen on 2023-07-13
Robin... Sorry. Was my omission. 

This
```

mount -t -o noatime,compress=lzo,space_cache=v2  /dev/nvme0n1p2 /mnt

```
Should have been
```

mount -t btrfs -o noatime,compress=lzo,space_cache=v2  /dev/nvme0n1p2 /mnt

```

---

### Post by Robbyx on 2023-07-13
I had no idea you had sent me #23 until today , because in my ignorance I assumed that I only had to search on the topics I had started. I was surprised that I apparently had no messages from you or 1fallen and decided to check the conferences that I was a member but had not started.

---

### Post by Robbyx on 2023-07-13
Your guesses as to the partitions  under nvm0n1p1 to 4 were correct. 

@ does show when I access 55 GB volume / @ on the main system via nautilus admin.  

```
root@ubuntu:~# ls -lah /mnt/*
total 40K
drwxr-xr-x 1 root root  172 Jul 12 11:16 .
drwxr-xr-x 1 root root    2 Jul  8 17:28 ..
lrwxrwxrwx 1 root root    7 Jul 12 11:16 bin -> usr/bin
drwxr-xr-x 1 root root 1.1K Jul 12 11:43 boot
drwxrwxr-x 1 root root    0 Nov 12  2022 cdrom
drwxr-xr-x 1 root root  134 Feb 23 03:57 dev
drwxr-xr-x 1 root root 4.6K Jul 13 10:19 etc
drwxr-xr-x 1 root root    0 Jul  8 17:28 home
lrwxrwxrwx 1 root root    7 Jul 12 11:16 lib -> usr/lib
lrwxrwxrwx 1 root root    9 Jul 12 11:16 lib32 -> usr/lib32
lrwxrwxrwx 1 root root    9 Jul 12 11:16 lib64 -> usr/lib64
lrwxrwxrwx 1 root root   10 Jul 12 11:16 libx32 -> usr/libx32
drwxr-xr-x 1 root root   12 Feb 23 03:57 media
drwxr-xr-x 1 root root    0 Feb 23 03:57 mnt
drwxr-xr-x 1 root root   66 Feb 23 03:57 opt
drwxr-xr-x 1 root root    0 Apr 18  2022 proc
drwx------ 1 root root  114 Feb 23 04:02 root
drwxr-xr-x 1 root root  240 Jul 12 11:20 run
lrwxrwxrwx 1 root root    8 Jul 12 11:16 sbin -> usr/sbin
drwxr-xr-x 1 root root  676 Feb 23 04:03 snap
drwxr-xr-x 1 root root    0 Feb 23 03:57 srv
drwxr-xr-x 1 root root    0 Apr 18  2022 sys
drwxrwxrwt 1 root root 1.9K Jul 13 10:19 tmp
drwxr-xr-x 1 root root  116 Feb 23 03:57 usr
drwxr-xr-x 1 root root  122 Feb 23 04:02 var

```

---

### Post by Robbyx on 2023-07-13
I do not know if it is of help but the 55 GB Volume / @ / mnt     is empty when accessed with admin access.

---

### Post by Robbyx on 2023-07-13
I did not specifically answer your question about the @ sign because the output does not seem to show it.

---

### Post by #&amp;thj^% on 2023-07-13
> **Robbyx said:**
> 
I agree it is very tiring and time consuming  to have the type of problems I am experiencing with my Ubuntu system running  BTRFS, I agree I  should change to another file system, if no easy solution is to be found, but I have had the BTRFS working well for a few months at least. I fear it will involve a lot of work and many problems  to change, only to find the failure to boot returns, because it is not directly the fault of BTRFS and thus a change of disk format will not correct the problem of booting the system.   

I have time just to reply this once today Robbin the months you have experienced with btrfs you could have moved to lvm/ext4,
and this might just be my opinion but it is so much more stable in that aspect and any btrfs drives and partitions you have are still accessible. I found it was a very fast pick-up to learn system, from usage to backups a just a win win.
```
&#9492;&#9472;> sudo pvdisplay
[sudo] password for me: 
  --- Physical volume ---
  PV Name               /dev/sdb2
  VG Name               vglinux
  PV Size               <465.26 GiB / not usable 2.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              119106
  Free PE               0
  Allocated PE          119106
  PV UUID               0BonQr-Fx9Q-s613-M8c1-uOCD-cfp7-WhccpA
   
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> df -h
Filesystem                Size  Used Avail Use% Mounted on
tmpfs                     1.6G  3.7M  1.6G   1% /run
/dev/mapper/vglinux-root  456G   31G  402G   8% /
tmpfs                     7.8G  516K  7.8G   1% /dev/shm
tmpfs                     5.0M   16K  5.0M   1% /run/lock
/dev/nvme0n1p1            511M   15M  497M   3% /boot/efi
tmpfs                     7.8G     0  7.8G   0% /run/qemu
tmpfs                     1.6G  220K  1.6G   1% /run/user/1000
&#9472;>
&#9474;~ 
&#9492;&#9472;> sudo vgdisplay -v
  --- Volume group ---
  VG Name               vglinux
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               <465.26 GiB
  PE Size               4.00 MiB
  Total PE              119106
  Alloc PE / Size       119106 / <465.26 GiB
  Free  PE / Size       0 / 0   
  VG UUID               zYGhL4-zPq3-T06s-4T0g-NeRE-E4aO-dPBXhv
   
  --- Logical volume ---
  LV Path                /dev/vglinux/root
  LV Name                root
  VG Name                vglinux
  LV UUID                UGiiPD-fY7P-RKcx-iEYu-P2sl-rG3W-mHYJRH
  LV Write Access        read/write
  LV Creation host, time linux, 2023-07-01 10:29:02 -0600
  LV Status              available
  # open                 1
  LV Size                <463.35 GiB
  Current LE             118617
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/vglinux/swap_1
  LV Name                swap_1
  VG Name                vglinux
  LV UUID                TIC7hf-8HHa-ilCg-5Sba-eMRd-aB5Z-9KQt7W
  LV Write Access        read/write
  LV Creation host, time linux, 2023-07-01 10:29:02 -0600
  LV Status              available
  # open                 2
  LV Size                1.91 GiB
  Current LE             489
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
   
  --- Physical volumes ---
  PV Name               /dev/sdb2     
  PV UUID               0BonQr-Fx9Q-s613-M8c1-uOCD-cfp7-WhccpA
  PV Status             allocatable
  Total PE / Free PE    119106 / 0
   
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> sudo pvdisplay -v
  --- Physical volume ---
  PV Name               /dev/sdb2
  VG Name               vglinux
  PV Size               <465.26 GiB / not usable 2.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              119106
  Free PE               0
  Allocated PE          119106
  PV UUID               0BonQr-Fx9Q-s613-M8c1-uOCD-cfp7-WhccpA
   
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> sudo lvdisplay -v
  --- Logical volume ---
  LV Path                /dev/vglinux/root
  LV Name                root
  VG Name                vglinux
  LV UUID                UGiiPD-fY7P-RKcx-iEYu-P2sl-rG3W-mHYJRH
  LV Write Access        read/write
  LV Creation host, time linux, 2023-07-01 10:29:02 -0600
  LV Status              available
  # open                 1
  LV Size                <463.35 GiB
  Current LE             118617
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/vglinux/swap_1
  LV Name                swap_1
  VG Name                vglinux
  LV UUID                TIC7hf-8HHa-ilCg-5Sba-eMRd-aB5Z-9KQt7W
  LV Write Access        read/write
  LV Creation host, time linux, 2023-07-01 10:29:02 -0600
  LV Status              available
  # open                 2
  LV Size                1.91 GiB
  Current LE             489
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
&#9474;~ 
&#9492;&#9472;> ls -l /dev/vglinux/root
lrwxrwxrwx 1 root root 7 Jul 13 07:33 /dev/vglinux/root -> ../dm-0
   

```
my only gripe is naming of drives and how they are read, ie:"dm-0"
Good Luck to Both of you,   and may the force be with you....lol

---

### Post by MAFoElffen on 2023-07-13
@1fallen --- You can do use the command lvrename to make them into something meaningful, on the live filesystem, without having to do much work. LVM methodologies are to make thing simple and flexible.

@Robbyx ---
As we have both explained BTRFS is still experimental. Like when I test DEV cycle versions of things. I expect things are going to break and be a challenge. Sometimes every day. That causes some chaos. I don't do that on a daily driver.

I, personally, would recommend for you to experiment with LVM2 or ZFS. I think you deserve and would be happier with something "Stable".

LVM2 just works out of the box. There is documentation for anything you might want to do with it everywhere...

With the effort you have spent on BTRFS, you could have learned ZFS and be well on your way to using the advanced features of that Volume Manager.

Both Volume Managers have the features you are 'trying' to get to work in BTRFS. Many people only scratch the surface of what either 'can' do.

EDIT:
Back to your results... You understand "what" BTRFS subvols are right? Explain to me what you think they are...

After that, I will explain why that is empty and why the system is broken. (What that means, in common language.)

We'll treat this as a teaching/learning experience so you can understand how things work (or supposed to work), so you can understand why it is not working, when it doesn't... Okay?

---

### Post by Robbyx on 2023-07-13
Dear 1fallen

Thank you for your hurried but helpful comment. I would be interested to hear from MAFoElffen if he agrees that I should change at this point when we have not worked out the underlying cause and it could just continue causing me havoc with  LVM instead of BTRFS. That is if I am lucky enough to get the computer working by just a change in the file system. I recall that some years ago I tried LVM and the result was not good because it rapidly filled up my hard drive with backup copies, so much so the computer became almost unusable and certainly extremely slow.

My current view is the decision to change should happen after the current system is working again. At present I can not use it as it will not boot. I hope the force is with us as well.

Robin

---

### Post by MAFoElffen on 2023-07-13
> **Robbyx said:**
> Dear 1fallen

Thank you for your hurried but helpful comment. I would be interested to hear from MAFoElffen if he agrees that I should change at this point when we have not worked out the underlying cause and it could just continue causing me havoc with  LVM instead of BTRFS. That is if I am lucky enough to get the computer working by just a change in the file system. I recall that some years ago I tried LVM and the result was not good because it rapidly filled up my hard drive with backup copies, so much so the computer became almost unusable and certainly extremely slow.

My current view is the decision to change should happen after the current system is working again. At present I can not use it as it will not boot. I hope the force is with us as well.

Robin
I think once you understand the how and why... That it should help you with anything you use in the future. Whatever that might be.

What you just reported, that the "@" subvol is empty... That would mean that it was not mounted correctly when the system was installed. You need to understand what a BTRFS subvolume "is" to understand the why of this.

If you don't understand that concept... Well, this is history repeating itself again, with your past /home versus @home... Those same concepts carry over to LVM and ZFS in the concept of what that means. That is why I feel you need to understand that concept before we go on. Agreed?

We are at post #36 of thread #3... and have not gotten anywhere. We need to have some understandings, so we can move to a solution. We currently are just going in circles.

---

### Post by #&amp;thj^% on 2023-07-13
Ninje'd by MAFoElffen ;)
Read his post #34
The Boot problem I promise is coming from "BTRFS" and a little UN-experienced user or users. 
Dang that's sounds harsh but it is not meant in that manor at all. (harsh that is)
Signing out today now....

---

### Post by Robbyx on 2023-07-13
Dear MAFoElffen

As I understand it subvols are a superior form of incremental backup which if turned on in a sensible fashion should make recover much more efficient than standard backup.

I have not used them, instead I have tried to get the system stable with the correct folder  conditions in the fstab,  and have continued to backup my data in the home directory with the ubuntu backup program. I have also used timeshare for the root directory. I am not saying my backup is perfect but it is managable until I can properly use the file system benefits. 

Robin

I know that if I have caused the absence  of subvols by not deliberately switching them on that is not an efficient use of BTRFS, but i am cautious.  I would prefer to adopt a new system in a slow manner building up my knowledge and using it when it becomes obvious I am ready to make changes because they are needed.

---

### Post by Robbyx on 2023-07-13
Dear MAFoElffen

Of course I agree with your proposals to help me better understand, etc

Robin

---

### Post by Robbyx on 2023-07-13
Dear MAFoElffen

Of course I agree with your proposals to help me better understand, etc

Robin

---

### Post by Robbyx on 2023-07-13
Part of the reason for not rushing in with subvols and similar, is that the system has been so unstable and has given me such problems that I have tried to get it stable and working properly before jumping in to cause more trouble due to my lack of adequate experience. I hope you do not find my attitude silly and excessively cautious.

---

### Post by #&amp;thj^% on 2023-07-13
We both understand that, and please take your time, it's a big choice and should be made with a full
understanding of what you want and how to best get there. (It not a race now, do your own research)

---

### Post by MAFoElffen on 2023-07-13
Okay...

Linux treats most everything as file system.

A BTRFS subvolume is just a storage container.

Think of storage containers like you would Russian Nested Dolls. Picture that in your head. Think of a hard disk as a storage container. Partitions, same. RAID, ZFS, LVM, BTRFS vdevs, same.

Think of where those containers exist.

You can define a whole raw disk as the outer container, for mdadm, LVM, ZFS, BTRFS, etc... then create nested container within... DO NOT DO THAT. Though it is possible, it is not a good idea. enough said on that. Always use a partition as your outer container.

When I create a root subvol on a BTRFS filesytem, I create them on the root of that vdev. I create suvol's of any external vdev's on their roots.

For example (typed in abstract):
```

/dev/sda
 \_ sda1
     |_ @
     |_ @home
     |_ /
     |_ /home
...etc

```
Then in fstab, you mount the subvol back into the filesystem before writing to it, so that you are writing to the nested container that is mounted at that point... so tha sub-vol @ is mounted at / and @home is mounted as /home... So that all the points where things would look for things in the filesystem are at the referenced point.

Understand that so far?

If they are not mounted and the wiring is not done when it is wriiten, then it writes just to where the point thinks it should be (underneath the subvol). That is the same that happened to your old /home, right? OR... it fails the write, because the referenced point is not mounted and nothing exists there.

With me so far?

You have to be very careful how and where you create subvols... If you changge from the root into a subfloder, then that created subvol will be nested under that directory, and it will be harder to reference, to be able to use it.

For example, if you create "@", then unmount the filesystem and mount the subvol "@" as the root, then create other subvols... then those subvols are consequently nested subvols under "@"... such as "@/@home"...

Grub needs to know where to find things, and how to reference them... So you need to know how to reference what is there and where things are located. 

More on that later. I need to go to work.

---

### Post by Robbyx on 2023-07-13
Yes, I understand. 

I noticed that in  the 1p3 directory which houses @home there were two other directories: new and robins. I had seen them recently and assumed they were the results of reinstalls that had gone wrong. It did not occur to me that they were subvols deliberately sitting there. 

New has a subdirectory called robins with a red cross in it. In that dir there are a number of folders such as desktop, videos, snap. Some of them are empty other some files produced in May. 

There is also a 3rd folder named robins with no entries. 

When i wrote that there are no subdirectories below  @home that is correct.  

Assuming I want to change to a more suitable system. How do I do it at this point?

---

### Post by Robbyx on 2023-07-13
BTW looking at the @home/ robins folder it seems all the items that should be there are still intact. I am not claiming that there is in fact  no lost data but it does not look like it at present.

---

### Post by Robbyx on 2023-07-13
BTW looking at the @home/ robins folder it seems all the items that should be there are still intact. I am not claiming that there is in fact  no lost data but it does not look like it at present.


I will not  be available until  tomorrow say 12 hours time.  

Robin

---

### Post by MAFoElffen on 2023-07-14
Just got home from work. Almost 1:30 am here. That time is good. Thats right before I go to work again.

---

### Post by Robbyx on 2023-07-14
I know what I am saying is obvious, there is no need for you  to reply promptly to me. I suggest you reply when you can as I note you will be going to work at about this time. Our times are different but as we communicate via this thread I will get a reply even if it is hours away. 

I have read the article on BTRFS at itsfoss.com.  Some of the comments  are very anti-btrfs, because of  adverse experiences.



I

---

### Post by Robbyx on 2023-07-14
I have been looking around at what to change to and ZFS looks a safe bet especially with its data protection, which I would like because I once set up a raid system and after a time found that damaged files were being cross written within the raid.

I found this of help comparing btrfs with zfs
[https://history-computer.com/btrfs-vs-zfs/](https://history-computer.com/btrfs-vs-zfs/)


I have been looking for ways to do the conversion and found useful comments here:
 [https://forums.unraid.net/topic/49161-convert-btrfs-to-xfs/](https://forums.unraid.net/topic/49161-convert-btrfs-to-xfs/)

If you have any references I should look at please indicate same. 

Robin

---

### Post by #&amp;thj^% on 2023-07-14
Hi Robbin that was a very fast choice, are you sure you have researched enough to hang your data on?
I too prefer ZFS over BTRFS, but there is a Steep learning curve involved.
I'm not sure why you want to jump into the deep end with your two choices, when ext4 with lvm will work well enough for what I've been able to see on your system.
If you install ZFS in a KVM first I think it would help.
Just my view is all..
```
Partition:
  ID-1: / size: 202.69 GiB used: 7.91 GiB (3.9%) fs: zfs 
  raid: rpool/ROOT/ubuntu_d1lsb0 
  ID-2: /boot size: 1.75 GiB used: 491.0 MiB (27.4%) fs: zfs 
  raid: bpool/BOOT/ubuntu_d1lsb0 
  ID-3: /boot/efi size: 511.0 MiB used: 14.8 MiB (2.9%) fs: vfat 
  dev: /dev/nvme1n1p1 
  ID-4: /home/me size: 203.80 GiB used: 9.01 GiB (4.4%) fs: zfs 
  raid: rpool/USERDATA/me_snfksb 
  ID-5: /media/me/02c61024-845a-40f8-8e9d-5d7815a50f64 size: 376.70 GiB 
  used: 2.0 MiB (0.0%) fs: ext4 dev: /dev/sdc2 
  ID-6: /media/me/1TB-BU size: 547.73 GiB used: 511.29 GiB (93.3%) fs: btrfs 
  dev: /dev/sdc1 
  ID-7: /media/me/2TB_Back-up size: 1.79 TiB used: 1.10 TiB (61.7%) fs: ext4 
  dev: /dev/sdf1 
  ID-8: /media/me/9b0b7fc0-a42d-426c-b972-77ea1295f8fb size: 495.56 GiB 
  used: 117.08 GiB (23.6%) fs: btrfs dev: /dev/sda2 
  ID-9: /media/me/Back-ups size: 428.03 GiB used: 321.03 GiB (75.0%) 
  fs: ext4 dev: /dev/sda3 
  ID-10: /root size: 194.79 GiB used: 2.4 MiB (0.0%) fs: zfs 
  raid: rpool/USERDATA/root_snfksb 
  ID-11: /srv size: 194.78 GiB used: 128 KiB (0.0%) fs: zfs 
  raid: rpool/ROOT/ubuntu_d1lsb0/srv 
  ID-12: /usr/local size: 194.78 GiB used: 256 KiB (0.0%) fs: zfs 
  raid: rpool/ROOT/ubuntu_d1lsb0/usr/local 
  ID-13: /var/games size: 194.78 GiB used: 128 KiB (0.0%) fs: zfs 
  raid: rpool/ROOT/ubuntu_d1lsb0/var/games 
  ID-14: /var/lib size: 197.20 GiB used: 2.41 GiB (1.2%) fs: zfs 
  raid: rpool/ROOT/ubuntu_d1lsb0/var/lib 
  ID-15: /var/lib/AccountsService size: 194.78 GiB used: 128 KiB (0.0%) 
  fs: zfs raid: rpool/ROOT/ubuntu_d1lsb0/var/lib/AccountsService 
  ID-16: /var/lib/NetworkManager size: 194.78 GiB used: 256 KiB (0.0%) 
  fs: zfs raid: rpool/ROOT/ubuntu_d1lsb0/var/lib/NetworkManager 
  ID-17: /var/lib/apt size: 194.85 GiB used: 71.6 MiB (0.0%) fs: zfs 
  raid: rpool/ROOT/ubuntu_d1lsb0/var/lib/apt 
  ID-18: /var/lib/dpkg size: 194.86 GiB used: 77.1 MiB (0.0%) fs: zfs 
  raid: rpool/ROOT/ubuntu_d1lsb0/var/lib/dpkg 
  ID-19: /var/log size: 194.83 GiB used: 45.4 MiB (0.0%) fs: zfs 
  raid: rpool/ROOT/ubuntu_d1lsb0/var/log 
  ID-20: /var/mail size: 194.78 GiB used: 128 KiB (0.0%) fs: zfs 
  raid: rpool/ROOT/ubuntu_d1lsb0/var/mail 
  ID-21: /var/snap size: 194.78 GiB used: 128 KiB (0.0%) fs: zfs 
  raid: rpool/ROOT/ubuntu_d1lsb0/var/snap 
  ID-22: /var/spool size: 194.78 GiB used: 128 KiB (0.0%) fs: zfs 
  raid: rpool/ROOT/ubuntu_d1lsb0/var/spool 
  ID-23: /var/www size: 194.78 GiB used: 128 KiB (0.0%) fs: zfs 
  raid: rpool/ROOT/ubuntu_d1lsb0/var/www 
  ID-24: swap-1 size: 2.00 GiB used: 1.5 MiB (0.1%) fs: swap 
  dev: /dev/nvme1n1p2
```
And still on the same Drive:
```
sudo lvs
[sudo] password for me: 
  LV     VG      Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   vglinux -wi-a----- <463.35g                                                    
  swap_1 vglinux -wi-a-----    1.91g  
Or just
 sudo pvs
[sudo] password for me: 
  PV         VG      Fmt  Attr PSize    PFree
  /dev/sdb2  vglinux lvm2 a--  <465.26g    0 
                                                  

```

---

### Post by MAFoElffen on 2023-07-14
Think of the filesystem, as it looks like in tree view or lsblk as a framework that Linux sees that framework laid out. The way mounts are setup underneath that... to accomplish that.

Looks like this to Linux:
```

mafoelffen@Mikes-B460M:/data/ISO$ tree -L 2 -d /
/
&#9500;&#9472;&#9472; bin -> usr/bin
&#9500;&#9472;&#9472; boot
&#9474;   &#9500;&#9472;&#9472; efi
&#9474;   &#9492;&#9472;&#9472; grub
&#9500;&#9472;&#9472; cdrom
&#9500;&#9472;&#9472; data
&#9474;   &#9500;&#9472;&#9472; ISO
&#9474;   &#9492;&#9472;&#9472; KVM-VM
&#9500;&#9472;&#9472; data2
&#9500;&#9472;&#9472; dev
&#9474;   &#9500;&#9472;&#9472; block
&#9474;   &#9500;&#9472;&#9472; bsg
&#9474;   &#9500;&#9472;&#9472; bus
&#9474;   &#9500;&#9472;&#9472; char
&#9474;   &#9500;&#9472;&#9472; cpu
&#9474;   &#9500;&#9472;&#9472; disk
&#9474;   &#9500;&#9472;&#9472; dma_heap
&#9474;   &#9500;&#9472;&#9472; dri
&#9474;   &#9500;&#9472;&#9472; fd -> /proc/self/fd
&#9474;   &#9500;&#9472;&#9472; hugepages
&#9474;   &#9500;&#9472;&#9472; input
&#9474;   &#9500;&#9472;&#9472; mapper
&#9474;   &#9500;&#9472;&#9472; mqueue
&#9474;   &#9500;&#9472;&#9472; net
&#9474;   &#9500;&#9472;&#9472; pts
&#9474;   &#9500;&#9472;&#9472; shm
&#9474;   &#9500;&#9472;&#9472; snd
&#9474;   &#9500;&#9472;&#9472; usb
&#9474;   &#9492;&#9472;&#9472; vfio
&#9500;&#9472;&#9472; etc
&#9474;   &#9500;&#9472;&#9472; acpi
&#9474;   &#9500;&#9472;&#9472; alsa
&#9474;   &#9500;&#9472;&#9472; alternatives
&#9474;   &#9500;&#9472;&#9472; apm
&#9474;   &#9500;&#9472;&#9472; apparmor
&#9474;   &#9500;&#9472;&#9472; apparmor.d
&#9474;   &#9500;&#9472;&#9472; apport
&#9474;   &#9500;&#9472;&#9472; apt
&#9474;   &#9500;&#9472;&#9472; avahi
&#9474;   &#9500;&#9472;&#9472; bash_completion.d
&#9474;   &#9500;&#9472;&#9472; binfmt.d
&#9474;   &#9500;&#9472;&#9472; bluetooth
&#9474;   &#9500;&#9472;&#9472; brltty
&#9474;   &#9500;&#9472;&#9472; ca-certificates
&#9474;   &#9500;&#9472;&#9472; chatscripts
&#9474;   &#9500;&#9472;&#9472; console-setup
&#9474;   &#9500;&#9472;&#9472; cracklib
&#9474;   &#9500;&#9472;&#9472; cron.d
&#9474;   &#9500;&#9472;&#9472; cron.daily
&#9474;   &#9500;&#9472;&#9472; cron.hourly
&#9474;   &#9500;&#9472;&#9472; cron.monthly
&#9474;   &#9500;&#9472;&#9472; cron.weekly
&#9474;   &#9500;&#9472;&#9472; cryptsetup-initramfs
&#9474;   &#9500;&#9472;&#9472; cups
&#9474;   &#9500;&#9472;&#9472; cupshelpers
&#9474;   &#9500;&#9472;&#9472; dbus-1
&#9474;   &#9500;&#9472;&#9472; dconf
&#9474;   &#9500;&#9472;&#9472; default
&#9474;   &#9500;&#9472;&#9472; depmod.d
&#9474;   &#9500;&#9472;&#9472; dhcp
&#9474;   &#9500;&#9472;&#9472; dictionaries-common
&#9474;   &#9500;&#9472;&#9472; dkms
&#9474;   &#9500;&#9472;&#9472; dnsmasq.d
&#9474;   &#9500;&#9472;&#9472; dnsmasq.d-available
&#9474;   &#9500;&#9472;&#9472; dpkg
&#9474;   &#9500;&#9472;&#9472; emacs
&#9474;   &#9500;&#9472;&#9472; environment.d
&#9474;   &#9500;&#9472;&#9472; firefox
&#9474;   &#9500;&#9472;&#9472; fonts
&#9474;   &#9500;&#9472;&#9472; fwupd
&#9474;   &#9500;&#9472;&#9472; gdb
&#9474;   &#9500;&#9472;&#9472; gdm3
&#9474;   &#9500;&#9472;&#9472; geoclue
&#9474;   &#9500;&#9472;&#9472; ghostscript
&#9474;   &#9500;&#9472;&#9472; glvnd
&#9474;   &#9500;&#9472;&#9472; gnome
&#9474;   &#9500;&#9472;&#9472; groff
&#9474;   &#9500;&#9472;&#9472; grub.d
&#9474;   &#9500;&#9472;&#9472; gss
&#9474;   &#9500;&#9472;&#9472; gtk-2.0
&#9474;   &#9500;&#9472;&#9472; gtk-3.0
&#9474;   &#9500;&#9472;&#9472; guest-session
&#9474;   &#9500;&#9472;&#9472; hp
&#9474;   &#9500;&#9472;&#9472; ifplugd
&#9474;   &#9500;&#9472;&#9472; init
&#9474;   &#9500;&#9472;&#9472; init.d
&#9474;   &#9500;&#9472;&#9472; initramfs-tools
&#9474;   &#9500;&#9472;&#9472; insserv.conf.d
&#9474;   &#9500;&#9472;&#9472; ipp-usb
&#9474;   &#9500;&#9472;&#9472; iproute2
&#9474;   &#9500;&#9472;&#9472; kernel
&#9474;   &#9500;&#9472;&#9472; keyutils
&#9474;   &#9500;&#9472;&#9472; ldap
&#9474;   &#9500;&#9472;&#9472; ld.so.conf.d
&#9474;   &#9500;&#9472;&#9472; libblockdev
&#9474;   &#9500;&#9472;&#9472; libibverbs.d
&#9474;   &#9500;&#9472;&#9472; libnl-3
&#9474;   &#9500;&#9472;&#9472; libpaper.d
&#9474;   &#9500;&#9472;&#9472; libreoffice
&#9474;   &#9500;&#9472;&#9472; libvirt
&#9474;   &#9500;&#9472;&#9472; lightdm
&#9474;   &#9500;&#9472;&#9472; logcheck
&#9474;   &#9500;&#9472;&#9472; logrotate.d
&#9474;   &#9500;&#9472;&#9472; lvm
&#9474;   &#9500;&#9472;&#9472; mdadm
&#9474;   &#9500;&#9472;&#9472; mdevctl.d
&#9474;   &#9500;&#9472;&#9472; ModemManager
&#9474;   &#9500;&#9472;&#9472; modprobe.d
&#9474;   &#9500;&#9472;&#9472; modules-load.d
&#9474;   &#9500;&#9472;&#9472; netplan
&#9474;   &#9500;&#9472;&#9472; network
&#9474;   &#9500;&#9472;&#9472; networkd-dispatcher
&#9474;   &#9500;&#9472;&#9472; NetworkManager
&#9474;   &#9500;&#9472;&#9472; newt
&#9474;   &#9500;&#9472;&#9472; nfs.conf.d
&#9474;   &#9500;&#9472;&#9472; nvme
&#9474;   &#9500;&#9472;&#9472; openvpn
&#9474;   &#9500;&#9472;&#9472; opt
&#9474;   &#9500;&#9472;&#9472; ostree
&#9474;   &#9500;&#9472;&#9472; PackageKit
&#9474;   &#9500;&#9472;&#9472; pam.d
&#9474;   &#9500;&#9472;&#9472; pcmcia
&#9474;   &#9500;&#9472;&#9472; perl
&#9474;   &#9500;&#9472;&#9472; pki
&#9474;   &#9500;&#9472;&#9472; pm
&#9474;   &#9500;&#9472;&#9472; polkit-1
&#9474;   &#9500;&#9472;&#9472; ppp
&#9474;   &#9500;&#9472;&#9472; profile.d
&#9474;   &#9500;&#9472;&#9472; pulse
&#9474;   &#9500;&#9472;&#9472; python3
&#9474;   &#9500;&#9472;&#9472; python3.10
&#9474;   &#9500;&#9472;&#9472; rc0.d
&#9474;   &#9500;&#9472;&#9472; rc1.d
&#9474;   &#9500;&#9472;&#9472; rc2.d
&#9474;   &#9500;&#9472;&#9472; rc3.d
&#9474;   &#9500;&#9472;&#9472; rc4.d
&#9474;   &#9500;&#9472;&#9472; rc5.d
&#9474;   &#9500;&#9472;&#9472; rc6.d
&#9474;   &#9500;&#9472;&#9472; rcS.d
&#9474;   &#9500;&#9472;&#9472; request-key.d
&#9474;   &#9500;&#9472;&#9472; rsyslog.d
&#9474;   &#9500;&#9472;&#9472; sane.d
&#9474;   &#9500;&#9472;&#9472; sasl2
&#9474;   &#9500;&#9472;&#9472; security
&#9474;   &#9500;&#9472;&#9472; selinux
&#9474;   &#9500;&#9472;&#9472; sensors.d
&#9474;   &#9500;&#9472;&#9472; sgml
&#9474;   &#9500;&#9472;&#9472; skel
&#9474;   &#9500;&#9472;&#9472; smartmontools
&#9474;   &#9500;&#9472;&#9472; snmp
&#9474;   &#9500;&#9472;&#9472; speech-dispatcher
&#9474;   &#9500;&#9472;&#9472; ssh
&#9474;   &#9500;&#9472;&#9472; ssl
&#9474;   &#9500;&#9472;&#9472; sudoers.d
&#9474;   &#9500;&#9472;&#9472; sysctl.d
&#9474;   &#9500;&#9472;&#9472; sysstat
&#9474;   &#9500;&#9472;&#9472; systemd
&#9474;   &#9500;&#9472;&#9472; terminfo
&#9474;   &#9500;&#9472;&#9472; thermald
&#9474;   &#9500;&#9472;&#9472; thunderbird
&#9474;   &#9500;&#9472;&#9472; tmpfiles.d
&#9474;   &#9500;&#9472;&#9472; ubuntu-advantage
&#9474;   &#9500;&#9472;&#9472; udev
&#9474;   &#9500;&#9472;&#9472; udisks2
&#9474;   &#9500;&#9472;&#9472; ufw
&#9474;   &#9500;&#9472;&#9472; update-manager
&#9474;   &#9500;&#9472;&#9472; update-motd.d
&#9474;   &#9500;&#9472;&#9472; update-notifier
&#9474;   &#9500;&#9472;&#9472; UPower
&#9474;   &#9500;&#9472;&#9472; usb_modeswitch.d
&#9474;   &#9500;&#9472;&#9472; vim
&#9474;   &#9500;&#9472;&#9472; virt-builder
&#9474;   &#9500;&#9472;&#9472; vulkan
&#9474;   &#9500;&#9472;&#9472; wpa_supplicant
&#9474;   &#9500;&#9472;&#9472; X11
&#9474;   &#9500;&#9472;&#9472; xdg
&#9474;   &#9500;&#9472;&#9472; xml
&#9474;   &#9492;&#9472;&#9472; zfs
&#9500;&#9472;&#9472; home
&#9474;   &#9500;&#9472;&#9472; maferr
&#9474;   &#9492;&#9472;&#9472; mafoelffen
&#9500;&#9472;&#9472; KVM_Pool
&#9474;   &#9500;&#9472;&#9472; datapool-backup
&#9474;   &#9492;&#9472;&#9472; KVM-VM
&#9500;&#9472;&#9472; lib -> usr/lib
&#9500;&#9472;&#9472; lib32 -> usr/lib32
&#9500;&#9472;&#9472; lib64 -> usr/lib64
&#9500;&#9472;&#9472; libx32 -> usr/libx32
&#9500;&#9472;&#9472; media
&#9474;   &#9492;&#9472;&#9472; mafoelffen
&#9500;&#9472;&#9472; mnt
&#9500;&#9472;&#9472; opt
&#9500;&#9472;&#9472; proc
&#9474;   &#9500;&#9472;&#9472; <Editted lots>
&#9500;&#9472;&#9472; root  [error opening dir]
&#9500;&#9472;&#9472; run
&#9474;   &#9500;&#9472;&#9472; <Editted Lots>
&#9500;&#9472;&#9472; sbin -> usr/sbin
&#9500;&#9472;&#9472; snap
&#9474;   &#9500;&#9472;&#9472; bare
&#9474;   &#9500;&#9472;&#9472; bin
&#9474;   &#9500;&#9472;&#9472; core20
&#9474;   &#9500;&#9472;&#9472; core22
&#9474;   &#9500;&#9472;&#9472; firefox
&#9474;   &#9500;&#9472;&#9472; gnome-3-38-2004
&#9474;   &#9500;&#9472;&#9472; gnome-42-2204
&#9474;   &#9500;&#9472;&#9472; gtk-common-themes
&#9474;   &#9500;&#9472;&#9472; snapd
&#9474;   &#9500;&#9472;&#9472; snapd-desktop-integration
&#9474;   &#9492;&#9472;&#9472; snap-store
&#9500;&#9472;&#9472; srv
&#9500;&#9472;&#9472; sys
&#9474;   &#9500;&#9472;&#9472; <Editted Lots>
&#9500;&#9472;&#9472; tmp
&#9474;   &#9500;&#9472;&#9472; <Editted Lots>
&#9500;&#9472;&#9472; usr
&#9474;   &#9500;&#9472;&#9472; bin
&#9474;   &#9500;&#9472;&#9472; games
&#9474;   &#9500;&#9472;&#9472; include
&#9474;   &#9500;&#9472;&#9472; lib
&#9474;   &#9500;&#9472;&#9472; lib32
&#9474;   &#9500;&#9472;&#9472; lib64
&#9474;   &#9500;&#9472;&#9472; libexec
&#9474;   &#9500;&#9472;&#9472; libx32
&#9474;   &#9500;&#9472;&#9472; local
&#9474;   &#9500;&#9472;&#9472; sbin
&#9474;   &#9500;&#9472;&#9472; share
&#9474;   &#9492;&#9472;&#9472; src
&#9492;&#9472;&#9472; var
    &#9500;&#9472;&#9472; backups
    &#9500;&#9472;&#9472; cache
    &#9500;&#9472;&#9472; crash
    &#9500;&#9472;&#9472; games
    &#9500;&#9472;&#9472; lib
    &#9500;&#9472;&#9472; local
    &#9500;&#9472;&#9472; lock -> /run/lock
    &#9500;&#9472;&#9472; log
    &#9500;&#9472;&#9472; mail
    &#9500;&#9472;&#9472; metrics
    &#9500;&#9472;&#9472; opt
    &#9500;&#9472;&#9472; run -> /run
    &#9500;&#9472;&#9472; snap
    &#9500;&#9472;&#9472; spool
    &#9500;&#9472;&#9472; tmp
    &#9492;&#9472;&#9472; www

1123 directories

```
But is actually sitting on top of this underneath: (Look at the mountpoints in the right-most column)
```

mafoelffen@Mikes-B460M:/data/ISO$ sudo zfs list
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
rpool                                             16.1G   875G       96K  /
rpool/ROOT                                        14.1G   875G       96K  none
rpool/ROOT/ubuntu_2cwpns                          14.1G   875G     7.16G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   875G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   875G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   875G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      6.96G   875G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   875G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  6.73G   875G     6.58G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   875G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    180K   875G      180K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt               106M   875G      106M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             46.1M   875G     46.1M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   240M   875G      240M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   875G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.48M   875G     1.48M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   875G      120K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   875G       96K  /var/www
rpool/USERDATA                                    1.93G   875G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  1.93G   875G     1.93G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        2.49M   875G     2.49M  /root

```
So when you do a backup of things that are located "on a filesystem", you can restore it to a different filesystem and volume manager.

I use this same concept to do complex installs of volume managers, and install an OS into that framework.

Does that start to make sense yet?

---

### Post by MAFoElffen on 2023-07-14
Between those layers, seen by Linux in lsblk as:
```

mafoelffen@Mikes-B460M:/data/ISO$ lsblk -e7 -o name,label,size,fstype,mountpoint
NAME        LABEL      SIZE FSTYPE     MOUNTPOINT
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
&#9500;&#9472;nvme4n1p1            512M vfat       /boot/efi
&#9500;&#9472;nvme4n1p2              2G swap       [SWAP]
&#9500;&#9472;nvme4n1p3 bpool        2G zfs_member 
&#9492;&#9472;nvme4n1p4 rpool      927G zfs_member 
nvme6n1                1.8T            
&#9492;&#9472;nvme6n1p1 datapool  1000G zfs_member 
nvme5n1     datapool   1.8T zfs_member 
&#9500;&#9472;nvme5n1p1            1.3T zfs_member 
&#9492;&#9472;nvme5n1p2 datapool    10G zfs_member 

```
That is 13 disks, that appears to Linux as one single filesystem... Each one of those partitions, that I labeled with alike label names are actually RAID-Z2 members of RAID'ed pools... So appear as just single pools mounted into the filesystem.

---

### Post by Robbyx on 2023-07-14
Yes it does make sense.Thank you.  

Today I managed to  get  Ubuntu  to load with no problem. It is working perfectly. At present it is fast and trouble free. Fstab is being mounted, and EFI is working as it should.  The btrfs files are being accessed with no error warnings or failures to read. The system is loading cleanly. So far no crashes. 
 
This could be an excuse to continue with BTRFS, but in view of both your  and  1fallen's  very clear warnings, I believe I should still proceed to use ZFS.  I assume you agree.  I just need to decide on how best to do the conversion. 

Robin

---

### Post by Robbyx on 2023-07-14
I have been looking at the layers in your examples of ZFS amalgamations of data from separate sources across multiple disks.  To me it looks like a relational database or even a pivot table. It seems like some of the fields are not normally changeable and are used as the common denominator for the ultimate amalgamations to produce  var, etc, root....

I assume there is another system which knows when spare space is available and its address on the drives as per  hard drive maps that the file system manages.

---

### Post by #&amp;thj^% on 2023-07-15
> **Robbyx said:**
> 
Today I managed to  get  Ubuntu  to load with no problem. It is working perfectly. At present it is fast and trouble free. Fstab is being mounted, and EFI is working as it should.  The btrfs files are being accessed with no error warnings or failures to read. The system is loading cleanly. So far no crashes. 
 
This could be an excuse to continue with BTRFS, 
Robin
Sounds like your getting the hang of BTRFS and mounts now, if you feel the most comfortable on that stay there. :)
To get your sea legs under you, try a fresh install on a KVM with zfs-root, you will get a better feel for it then.
```
NAME                      LABEL         SIZE FSTYPE      MOUNTPOINT
sda                                   931.5G             
&#9500;&#9472;sda1                                   16M             
&#9500;&#9472;sda2                                495.6G btrfs       
&#9492;&#9472;sda3                    Back-ups    435.9G ext4        
sdb                                   465.8G             
&#9500;&#9472;sdb1                    geekpool      512M zfs_member  
&#9492;&#9472;sdb2                                465.3G LVM2_member 
  &#9500;&#9472;vglinux-root                      463.3G ext4        
  &#9492;&#9472;vglinux-swap_1                      1.9G swap        [SWAP]
sdc                                   931.5G             
&#9500;&#9472;sdc1                    1TB-BU      547.7G btrfs       
&#9492;&#9472;sdc2                                383.8G ext4        
sdd                       rpool       238.5G zfs_member  
&#9500;&#9472;sdd1                                  121M vfat        
&#9500;&#9472;sdd2                    KaisenBoot    488M btrfs       /boot
&#9492;&#9472;sdd3                                237.9G LVM2_member 
  &#9492;&#9472;kaisen--lvm2--vg-root KaisenLinux 237.9G btrfs       /
sde                                       0B             
sdf                                       0B             
nvme0n1                               238.5G             
&#9500;&#9472;nvme0n1p1                             512M vfat        /boot/efi
&#9500;&#9472;nvme0n1p2                               2G swap        [SWAP]
&#9500;&#9472;nvme0n1p3               bpool           2G zfs_member  
&#9492;&#9472;nvme0n1p4               rpool         234G zfs_member  
nvme1n1                               465.8G             
&#9500;&#9472;nvme1n1p1                               1G vfat        
&#9500;&#9472;nvme1n1p2                            15.9G swap        [SWAP]
&#9492;&#9472;nvme1n1p3                           448.9G ext4        
me@kaisen-lvm2 ~ $ 


```
This is a Debian Disk and Layout:
```
sdd                       rpool       238.5G zfs_member  
&#9500;&#9472;sdd1                                  121M vfat        
&#9500;&#9472;sdd2                    KaisenBoot    488M btrfs       /boot
&#9492;&#9472;sdd3                                237.9G LVM2_member 
  &#9492;&#9472;kaisen--lvm2--vg-root KaisenLinux 237.9G btrfs       /
```
Robbyx what back-up tool are you using right now?
For BTRFS I'll use "snapper" and Timeshift, and i run them manually not Automated. (I prefer this)
```
 sudo timeshift --list
Mounted '/dev/dm-2 (sdd3)' at '/run/timeshift/55047/backup'
Device : /dev/dm-2 (sdd3)
UUID   : 90390c5a-19c7-4d65-bec1-e1622a0fd895
Path   : /run/timeshift/55047/backup
Mode   : BTRFS
Status : OK
1 snapshots, 235.8 GB free

Num     Name                 Tags  Description             
------------------------------------------------------------------------------
0    >  2023-07-15_09-42-52  O     Automatic APT snapshot  

```
Those are the only stable and dependable snapshot tools for BTRFS. (IMHO)

---

### Post by Robbyx on 2023-07-15
For system backup I use Timeshift (not in btrfs mode)

For data backup including the home dir, I use the Ubuntu version of Deju dup

I am going ahead with the ZFS because it is more stable and reliable that btrfs.

Robin

---

### Post by MAFoElffen on 2023-07-15
+1 ---
Use KVM VM Guests to play an learn. With those, you can learn how they work, how to extend them for what you need to work... And if they break, how to get them working again.  Use that to decide what you want to end up with...

In the early 90's, I swayed a corporation I worked for, away from linear  concepts for application design, into distributed processing and object  oriented programming. From the relational database they were using,  into an SQL based database, and the applications they built for them,  using their business rules. I think of things as they related to data  modeling, database and systems design... and how they fit into the  7-layer OSI model.

I learned by thinking of things in abstracts,  how each piece works, and how they can work together. I was referred to  as a Systems Architect. I was the person to go to if you wanted to know  where to find things and how to make something possible.

Those same  concepts apply, even how you organize the basic layout of a folder, it's  sub-directories, and the information contained inside of them. That, in  itself, can be referred to as a basic database.

For good reads on Volume Managers:

LVM2:
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/ch-lvm](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/ch-lvm)
[https://opensource.com/business/16/9/linux-users-guide-lvm](https://opensource.com/business/16/9/linux-users-guide-lvm)
[https://linuxhandbook.com/lvm-guide/](https://linuxhandbook.com/lvm-guide/)
[https://www.digitalocean.com/community/tutorials/an-introduction-to-lvm-concepts-terminology-and-operations](https://www.digitalocean.com/community/tutorials/an-introduction-to-lvm-concepts-terminology-and-operations)

ZFS:
[https://codilime.com/blog/what-is-zfs-and-how-can-i-use-it/](https://codilime.com/blog/what-is-zfs-and-how-can-i-use-it/)
[https://openzfs.readthedocs.io/en/latest/introduction.html](https://openzfs.readthedocs.io/en/latest/introduction.html)
[https://openzfs.github.io/openzfs-docs/man/7/zfsconcepts.7.html](https://openzfs.github.io/openzfs-docs/man/7/zfsconcepts.7.html)
[https://openzfs.org/wiki/System_Administration](https://openzfs.org/wiki/System_Administration)
[https://docs.oracle.com/cd/E23823_01/html/819-5461/toc.html](https://docs.oracle.com/cd/E23823_01/html/819-5461/toc.html)

BTRFS:
[https://linuxhint.com/btrfs-filesystem-beginner-guide/](https://linuxhint.com/btrfs-filesystem-beginner-guide/)
[https://btrfs.readthedocs.io/en/latest/Introduction.html](https://btrfs.readthedocs.io/en/latest/Introduction.html)
[https://documentation.suse.com/sles/15-SP2/html/SLES-all/cha-filesystems.html#sec-filesystems-major-btrfs](https://documentation.suse.com/sles/15-SP2/html/SLES-all/cha-filesystems.html#sec-filesystems-major-btrfs)


The Volume Management system I am now testing is StratisFS...
[https://stratis-storage.github.io/stratify/](https://stratis-storage.github.io/stratify/)
[https://tekneed.com/managing-layered-storage-with-stratis-in-linux/](https://tekneed.com/managing-layered-storage-with-stratis-in-linux/)
[https://opensource.com/article/18/5/stratis-storage-linux-command-line](https://opensource.com/article/18/5/stratis-storage-linux-command-line)

---

### Post by #&amp;thj^% on 2023-07-15
> **Robbyx said:**
> 
I am going ahead with the ZFS because it is more stable and reliable that btrfs.

Robin
MAFoElffen has some great resource links in post #57 (good grief it went that far)

In your journey make sure you have good back-ups for zfs snapshots.

This is a good area to have a working method intact.

---

### Post by MAFoElffen on 2023-07-15
What I like about ZFS pools is that they are flexible and portable. I can export a snapshot and send it elsewhere to be restored remotely somewhere else. I can export pools on one machine, and import them into a filesystem somewhere else, very easily.

That opens up a lot of possibilities in what you can do, and what you can create.

For example migrating a system to a new OS or different hardware. If you implement it into objects, all the pieces are portable, can be moved and reassembled somewhere else. (I remember the first person who explained multi-processor distributed processing in mainframes, and how Ethernet networking packets move, work and make sense as transported information. LOL. Late 80's!)

You can apply that to '*many things*'. ZFS just makes that methodology easy. Well, that is... If you understand '*how to tell it how to do those things*'. I actually learned more about the advanced features of LVM2, by applying what I knew about ZFS from OpenSolaris, and trying to make those things work in LVM2. It's funny that I learned about ZFS before learning LVM2...

---

### Post by Robbyx on 2023-07-15
Thank you both for your excellent advice. I will now try and put it into practice. 

Robin

---

