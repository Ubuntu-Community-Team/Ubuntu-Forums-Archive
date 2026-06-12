---
title: "Is this an appropriate partitioning scheme for multi booting several distros? MBR+LVM"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by El Potro on 2012-07-26
Hello everyone,

I've been reading, asking, and trying to find the most suitable partitioning scheme for my multi booting 2 TB hdd, and probably this is the definitive one (or close). I want to hear your opinions, and I have some questions also. Now let's take a look:

```
N°   type      label   FS      Size
|--sda1 primary    grub2   ext4    32 MB
|--sda2 primary    swap             2 GB
|--sda3 logical    distros        400 GB
|   |
|   |   N°         label   FS      Size
|   |--sda5-----> OpenSUSE ext4     5 GB 
|   |--sda6-----> FreeBSD           5 GB
|
|   N°   type      label   FS      Size
|--sda4 primary     LVM    lvm   1536 GB
    |
    |    N°       LV name  FS      Size    Mount point
    |----1         home    ext4  1300 GB     /home      
    |--- 2         ubuntu  ext4    25 GB     /    
    |--- 3         debian  ext4    10 GB     /
    |----4         fedora  ext4    10 GB     /
    |----5         mint    ext4    10 GB     /
```

[SIZE="3"]Notes:[/SIZE]

1. GRUB2 has its own partition, that will be updated from inside Ubuntu with the following command: grub-mkconfig –o /media/btldr/boot/
2. Each distribution will keep it's own native bootloader in it's own partition just in case. Anyway GRUB2 is going to do all the work. If there's a problem, I can chainload to the selected partition (I'm thinking of the distributions that are going to be inside sda3).
3. Unfortunately I won't be using GPT at all because it seems it is not completely supported yet by all distros, and I don't want to struggle so much as long as I can avoid it.
4. Home partition is going to be shared among all distributions using different user folders.
5. I'm very concerned about resizing partitions and the physical volume of LVM. I placed the "distros" partition (/dev/sda3) outside LVM because there are some distributions or systems such as FreeBSD that doesn't support it, or doesn't support it easily (example: OpenSUSE). I want to be able to free space from /dev/sda3 and resize the logical partition and give that extra, freed space to /dev/sda4 (the LVM physical volume) so I can extend the LVM volume group and therefore the logical volume home.
6. All sizes are approximate.

[SIZE="3"]Questions:[/SIZE]

1. Will this procedure allow me to extend /dev/sda4 whenever I want?
2. Is it better to place the logical partition (distros) in sda4 (at the bottom of the disk) and the LVM partition before, in sda3? I guess not, that it is simpler to extend the LVM partition in the scheme I designed, but please correct me if I'm wrong.
3. What is the best way to create the logical volumes in LVM? I heard something about contiguous and non-contiguous logical volumes.
4. What is the best order of logical volumes I should follow or choose?

My idea is to extend the home partition if I need so. So I didn't give the whole capacity to LVM in the beginning because it is hard to shrink, so I'll be giving it more capacity, extending it gradually if I see I need it.

Any other ideas, advices or suggestions will be hugely appreciated too.

Thank you

PS: Sorry for possible mistakes, I hope I explained it all clearly.

---

### Post by dino99 on 2012-07-26
thats my way :P

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by oldfred on 2012-07-27
I am not a particular fan of LVM, this post is by a user who uses LVM.

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

If you are not resizing your LVM, then it has little practical advantage. When I got my 650GB drive several years ago, I went with 2 data partitions of 100GB one NTFS to share with XP on an old drive and the new data in ext3. I left rest of drive unpartitioned and have added 25GB / (root) partitions as I added new Ubuntu versions or tested some other install.

Are you sure you can update a grub only partition from Ubuntu. I only manually update grub only partitions. 
I think Fedora defaults to LVM and a separate /boot outside the LVM. Some say just to install to an ext4 partition so it only uses one. 
I also thought FreeBSD did not play well with others and needed a primary partition. But that may be older info, now.

I prefer to have data in data partitions and keep /home inside / (root) but different distributions use different default UIDs & GIDS, so that is a bit more difficult. I think Fedora just changed to 1000 for default UID and all Debian are.

Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

