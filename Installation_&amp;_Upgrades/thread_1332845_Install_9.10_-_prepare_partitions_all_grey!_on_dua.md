---
title: "Install 9.10 - prepare partitions all grey! on dual-boot.. why?"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by avastreg on 2009-11-20
Hi guys, 

i want to install ubuntu 9.10 on a pc which has already installed Windows 7.

I have set up an unformatted primary partition with gparted and ubuntu live (see picture related - gparted.jpg).

During the installation i choose language (i'm italian), time and keyboard and then it shows me the "prepare partition" window, with no partitions at all and all greyed out! look at picture related - prepare-partitions.jpg)

Do you have any hints?

Here's the fdisk -l - of course, i'm n00bish :)

```
fdisk -l 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
224 heads, 19 sectors/track, 114754 cylinders
Units = cylinders of 4256 * 512 = 2179072 bytes
Disk identifier: 0xa60b112f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              14       77006   163841104    f  W95 Ext'd (LBA)
/dev/sda2           84853      114755    63633296    7  HPFS/NTFS
/dev/sda5              14       77006   163840038+   7  HPFS/NTFS

```

---

### Post by avastreg on 2009-11-21
up! please help me ;)

---

### Post by darkod on 2009-11-21
I think the confusion might be that you actually started with extended partition instead of primary. Your /dev/sda1 is extended (logical) and after that /dev/sda2 is primary. I usually create extended (logical) only after 3 primaries have been used up. At east have one primary before the extended.
If you have nothing important on /dev/sda1 I would use gparted to delete all partitions except /dev/sda2 where your Win7 is. Because it will be only partition it will probably be changed to /dev/sda1.
Then do not create any partitions in advance for ubuntu, no need to. Just start with Install Ubuntu option and in step 4 use the manual partitioning to create the partitions right then. Othewise it's double the work because even if you use existing partitions for ubuntu you have to reallocate the mount points etc.

PS. I just noticed sda5 is ntfs also. Do you have some data on it? That is actually the logical partition inside sda1.

PPS. Just to give you better idea, my setup on 250GB disk is:
Primary:
65GB ntfs win7 system
141GB ntfs data
15GB ext4 /
Extended (logical):
2GB swap
10GB ext4 /home

---

### Post by Bartender on 2009-11-21
After looking at screenshots I had the same questions as darkod.  There's an extended partition at the "front" of the HDD.  It's always been a given on these forums that Windows won't boot from an extended partition.  Does 7 change that?

I'm not familiar with 7's partition scheme either - several posts have indicated that it wants to make two partitions?

Anyway, if you let Ubuntu installer go automatic it will try to create an extended partition for swap.  Since it sees an extended partition already, the installer may not be able to figure out what to do.

---

### Post by darkod on 2009-11-21
To clarify the thing about 7 two partitions. From my experience from my desktop and netbook, 7 will create 100MB boot partition but ONLY if you have blank new drive or deleting all the partitions and starting from blank, and you are creating your first, windows system partition with 7 installer. You get message that 100MB primary partition will get created with no option to cancel.
But on my desktop I was doing clean install of 7 on already EXISTING partition (ex-Vista) and it just used it without creating the 100MB.
So the rule seems to be, if you are willing to use Gparted or similar, and create your first primary ntfs for windows system with that, you will avoid "wasting" a primary partition for the 100MB. And with single drive and dual booting saving one primary partition sometimes helps a lot.

---

### Post by avastreg on 2009-11-21
> **darkod said:**
> I think the confusion might be that you actually started with extended partition instead of primary. Your /dev/sda1 is extended (logical) and after that /dev/sda2 is primary. I usually create extended (logical) only after 3 primaries have been used up. At east have one primary before the extended.
If you have nothing important on /dev/sda1 I would use gparted to delete all partitions except /dev/sda2 where your Win7 is. Because it will be only partition it will probably be changed to /dev/sda1.
Then do not create any partitions in advance for ubuntu, no need to. Just start with Install Ubuntu option and in step 4 use the manual partitioning to create the partitions right then. Othewise it's double the work because even if you use existing partitions for ubuntu you have to reallocate the mount points etc.

PS. I just noticed sda5 is ntfs also. Do you have some data on it? That is actually the logical partition inside sda1.

PPS. Just to give you better idea, my setup on 250GB disk is:
Primary:
65GB ntfs win7 system
141GB ntfs data
15GB ext4 /
Extended (logical):
2GB swap
10GB ext4 /home

now under your suggestion i have only one partition (primary) /dev/sda4 ntfs with win 7 system, 60 gb; remaining space is unallocated.

This primary partition is the first starting from left; then, there is unallocated space.

Also with this configuration, Ubuntu installation is not like this 

[http://wiki.ubuntu-it.org/Hardware/DispositiviPartizioni/RidimensionarePartizioneVista?action=AttachFile&do=get&target=ridurre.png](http://wiki.ubuntu-it.org/Hardware/DispositiviPartizioni/RidimensionarePartizioneVista?action=AttachFile&do=get&target=ridurre.png) (the image is in italian but i think you've got what i mean), but it's again like the one posted above (no options selectable in my window) :(

Any other ideas?

Maybe is SATA drive the problem?? But it's strange, ubuntu live cd goes well and gparted sees the drive

---

### Post by HeadHunter00 on 2009-11-21
I'm afraid to say this but :twisted:... You have to reinstall ubuntu.

---

### Post by avastreg on 2009-11-21
> **HeadHunter00 said:**
> I'm afraid to say this but :twisted:... You have to reinstall ubuntu.

the problem is this.. i can't!


edit: 

i've tried now with Ubuntu 9.04 and it works perfectly.. i have done the partitions from the prepare partitions window!

so it's clearly a 9.10 bug.. not a little bug!

then i'll try to upgrade to 9.10.. we'll see..

---

