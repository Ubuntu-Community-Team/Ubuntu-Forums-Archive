---
title: "What to do with Additional NVMe 2TB SSD?"
date: 2023-11-13
forum: Installation &amp; Upgrades
---

### Post by theassociate on 2023-11-13
Want to install Ubuntu 22.04 on a 2TB NVMe SSD using the following GPT partition scheme:

/boot/efi = 1GB Primary
swap = 10GB Primary (I have 80GB of physical RAM)
/(root) = 100GB Primary
/home = Remaining Space (approx 1889GB) Primary

Aiming for a single boot on an HP ZBook Fury 17 G8 workstation laptop that also has a second 2TB NVMe SSD. Currently, both drives are empty and unformatted.

My question is what to do with the second NVMe SDD after I install Ubuntu on the primary NVMe. Should I make it /data or /media? Or should I just format it as FAT32 or FAT16 and make it the equivalent of external HDD storage? I know how to do the latter easily enough, but I'm not really certain how to do the former.

I entertained the idea of creating partitions for multiple Ubuntu/Linux distros on NVMe 1 and letting /home take up all of NVMe 2, but I'm not sure if this is the best use of space, especially if I don't really see myself using multiple distros. BTW: Came up with the rough partition scheme above because all I really want is the ability to upgrade to a new distro via / in the future w/o compromising /home.

Would appreciate any thoughts from the good folks in the community. Thanks. Be blessed today.

---

### Post by TheFu on 2023-11-13
> ```
/boot/efi = 1GB Primary
swap = 10GB Primary (I have 80GB of physical RAM)
/(root) = 100GB Primary
/home = Remaining Space (approx 1889GB) Primary

```
My comments on this:

10GB is crazy for swap.  4.1G would be the max I ever used and only if all the RAM in the system was used up.  I can't imagine very many workloads that need more than 32GB of RAM, much less 80GB.  Too much swap can become a problem just like too little.  If you won't 100% know that your workload will eat all the REAL RAM in the system, I'd allocate just 1GB of swap.  Having "some" swap puts the kernel into a specific mode that is advantageous, but our goal is to have swap used only when absolutely needed, not as a crutch.  YMMV.

100G for the OS is crazy.  35G is massively oversized and the max needed.  I have 35G allocated on my 20.04 system and 25.3G of that is free.  I do split off /var and /tmp and /home to other volumes. See:
```
NAME                        TYPE  FSTYPE              SIZE FSAVAIL FSUSE% LABEL                       MOUNTPOINT
nvme0n1                     disk                    931.5G                                            
&#9500;&#9472;nvme0n1p1                 part  ext2                  1M                                            
&#9500;&#9472;nvme0n1p2                 part  vfat                 50M   43.9M    12%                             /boot/efi
&#9500;&#9472;nvme0n1p3                 part  ext4                700M    340M    42%                             /boot
&#9492;&#9472;nvme0n1p4                 part  LVM2_member       930.8G                                            
  &#9500;&#9472;vg01-swap01             lvm   swap                4.1G                                            [SWAP]
  &#9500;&#9472;vg01-root01             lvm   ext4                 35G   25.3G    21%                             /
  &#9500;&#9472;vg01-var01              lvm   ext4                 20G   15.2G    17%                             /var
  &#9500;&#9472;vg01-tmp01              lvm   ext4                  4G    3.4G     8% tmp01                       /tmp
  &#9500;&#9472;vg01-home01             lvm   ext4                 20G   12.9G    30% home01                      /home
  &#9500;&#9472;vg01-libvirt--01        lvm   ext4                137G    2.8G    98% libvirt--01                 /var/lib/libvirt
  &#9500;&#9472;vg01-lxd--containers--01
```

If you use LVM like me, you'll have tremendous flexibility for future needs.  But if you don't setup LVM at install time, it won't be possible to add in the future without a fresh install.
With LVM, the flexibility comes by NOT allocating more storage that you need for the next month, until it is actually required.  That means that the volume where the OS is located which is 35G in my example above, should I ever need more storage there, thanks to LVM, I can add 1G or 5G or 300G more to that specific volume, if needed. I just can't see needing over 35G, however.  I've been using Linux since 1993.  The way I allocate storage has changed over all these decades and I hope I'm smarter about it now.  About the last 15 yrs, I've been using LVM for added flexibility. 

I started using LVM around 2000 and early on, I got into some trouble doing things that were possible, but terrible ideas. A massive data loss issue taught me a hard lesson. I was being foolish with my LVM use by spanning a single file system across 3 physical storage devices - stripped. After all, I wanted higher performance.  Then 1 of those devices failed and all the data on all 3 was gone, gone, gone.  This was before I had backup religion.  These days, I don't allow any single storage volume to be larger than my ability to back it up to a single backup device.

/home should be sized for what you need now. If you leave space "to the right", resizing larger isn't hard.  If you use LVM, resizing larger can be done WHILE THE SYSTEM IS being used, zero downtime and the resize requires less than 5 seconds.  Also, if you use LVM, there are lots of other things like resizing any logical volume is possible, not just the last one.

Note how I have a 1TB SSD, but I've allocated less than 25G so far?  When I need it, any of those LVs can be extended while the system is running.  Making an LV smaller is actually a little harder.  I expect /var to need more storage, which is why I sized it at 20G, but I've been better at avoiding snap packages than I thought possible, so /var/ didn't get eaten up with snaps that I don't really want.  Plus, I had 1 specific virtual machine that is 132GB in size that sits under /var/lib/libvirt/, so I specifically created a volume just for it.  Most of my VMs use LVM directly and don't show up in mount lists and the hostOS generally ignores them, except the hypervisor storage pool manager.

No way would I allocate more than about 20GB for storage to a HOME directory.  What do you plan to put there?  If music and videos, that is really wasteful.  SSD storage is still 2-5x more expensive than a spinning HDD and any spinning HDD will easily meet the speed requirements to play any video or music.  Spend money where it makes sense, not just because you have money to blow.

Ok, back to your main question .... 
> My question is what to do with the second NVMe SDD after I install Ubuntu on the primary NVMe. Should I make it /data or /media? Or should I just format it as FAT32 or FAT16 and make it the equivalent of external HDD storage? I know how to do the latter easily enough, but I'm not really certain how to do the former.

My vote is to avoid mounting anything under /media/ since that storage area is controlled by gfvs and gio, which aren't exactly known as great programs to trust.  
What are you doing for backups?  I'd never use an SSD for backup storage, but for $50, you can get a 2-4TB external USB3 HDD for backup use.  

Until you actually need a 2nd NNMe SSD, I wouldn't even install it. Why have it being used and heated prematurely when those things reduce lifespan?  OTOH, if you do video editing, you may want to setup the 2nd SSD as a data _scratch area_ for temporary edit files.  Editing video is hard on SSDs and it will use up the available write cycles, perhaps 4-10x faster than typical use would.  Just something to consider.

Lastly, with SSDs if you don't use over 80% of the storage, that extra empty area will be used for wear leveling across the entire SSD, drastically increasing lifespan for the whole storage device.  Of course, not all SSD/NVMe controllers are equal, so YMMV.  There's a reason just a few brands have excellent reputations and then others are "cheap".  Some of that is the storage type itself, but some of it is also how well the storage controller inside the SSD actually works.  While we think of SSDs like spinning HDDs with different physical sectors", we need to remember and remind ourselves that every cell inside an SSD is virtual and every block is virtual, so the idea that blocks are contiguous and next to each other just doesn't apply with SSD storage and hasn't for a long time. It is all virtual and we can never really know which cells are used for each block and each sector and each virtual "cylinder".  Those ideas are just a bridge for old-guys to have an understanding, but not used inside the SDD at all.

---

### Post by theassociate on 2023-11-13
Good thoughts, @TheFu. So, 500MB for EFI, 4GB for swap, 50GB for /, and 80GB for /home to start? Thanks much.

For what it's worth, I know nothing about LVM. I've only just recently veered into the treacherous waters of the "Something Else" option on Ubuntu's USB Installer. Would love to hear more, though. Can you point me to a good step-by-step guide that utilizes LVM?

Also, because I didn't want to complicate things with my original post, I neglected to mention that, in addition to the two NVMe SSDs, my ZBook also has a standard 1TB SATA SSD. And this I plan to replace with a 5TB Seagate Barracuda HDD ASAP, based upon your recommendation. The setup I used in the old EliteBook 8770w laptop I've replaced was a 256GB SATA SSD for /boot, swap, and /, and a standard 1TB HDD for /home. Pretty straight-forward. I bought that rig back in 2012. Don't know why I just assumed that, in       2023, we would have perfected SSD technology to the point where       standard HDDs would be obsolete. Guess I was way off with that assumption.  :  )

So, after replacing the SATA SSD with a new 5TB HDD, do you still think I should open my new rig and remove the second NVMe that it came with so I don't shorten its life (even though I won't be using it)? Maybe just hold onto it as a back-up? Guess I didn't consider how the constant writing of video editing would shorten its life-span.

Thanks for taking the time to post such a thoughtful and timely response. I greatly appreciate it.

---

### Post by Dennis N on 2023-11-13
I love LVM too. I won't do a standard install unless there is no LVM support by the installer.
I suggest you google "Why use LVM in Linux" and you will get a lot to read over, including guides.
I will note that you can mix standard installs with LVM installs all on the same disk.

My system with several LVM installs and one standard install too. 

```
NAME                  LABEL        FSTYPE        SIZE
zram0                                              8G
nvme1n1                                        465.8G
&#9500;&#9472;nvme1n1p1                        vfat          100M
&#9500;&#9472;nvme1n1p2           Fedora-boot  ext4         1000M
&#9492;&#9472;nvme1n1p3                        LVM2_member   293G
  &#9500;&#9472;vg_02-fedora      Fedora       ext4           30G
  &#9500;&#9472;vg_02-common--vm                              25G
  &#9492;&#9472;vg_02-debian_12                               20G
nvme0n1                                        931.5G
&#9500;&#9472;nvme0n1p1                        vfat          100M
&#9500;&#9472;nvme0n1p2                        LVM2_member 732.4G
&#9474; &#9500;&#9472;vg_01-Common      Common-Files ext4           80G
&#9474; &#9500;&#9472;vg_01-ubuntu      Ubuntu       ext4           30G
&#9474; &#9500;&#9472;vg_01-debian      Debian       ext4           20G
&#9474; &#9500;&#9472;vg_01-debian_swap              swap            2G
&#9474; &#9492;&#9472;vg_01-manjaro                  ext4           25G
&#9500;&#9472;nvme0n1p3           Manjaro      ext4         33.2G
&#9492;&#9472;nvme0n1p4                        vfat          310M

```

---

### Post by TheFu on 2023-11-13
> **theassociate said:**
> Good thoughts, @TheFu. So, 500MB for EFI, 4GB for swap, 50GB for /, and 80GB for /home to start? Thanks much.


I've posted what I use. What you've posted above isn't mapping. I've made my suggestions. 

```
$ df /boot/efi
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p2   50M  **6.1M**   44M  13% /boot/efi
```
So, I'm using 6.1MB for EFI and allocated 50MB for it.  Why do you think you need 500MB?  "just in case?"  The same goes for / at 50G.  You can always add storage where it is needed later.

> **theassociate said:**
> 
For what it's worth, I know nothing about LVM. I've only just recently veered into the treacherous waters of the "Something Else" option on Ubuntu's USB Installer. Would love to hear more, though. Can you point me to a good step-by-step guide that utilizes LVM?

If I asked your for a step by step guide to drive a car, could your recommend one if you've been driving for 30 yrs?  Probably not.  You'd tell me to use google or youtube and look around for what "clicks" for me.  Right?
There's a user here ... Hammond who I don't recall seeing recently. He posted server setup guides on his website and linked to them here. Maybe that's what you seek? IDK.

The way I setup LVM on installs is to start the installation or get into the "Try Ubuntu" mode, then pull a script that I wrote over from another system on my network, customize that script as needed for the specific system/storage, setup the new storage with partitions that look like what I've already posted, then toggle back into the installer, choose "do something else" and just connect the different volumes to the specific mount locations and file system types there.  Trying to use the Ubuntu installer to manually setup LVM for non-trivial needs is too much of a pain.  Canonical's installer sucks for anything other than what they deem to be the defaults, which is really sad, since other non-ubuntu installers make it almost a joy to setup LVM is an intuitive way.

While I don't really know on the most recent Ubuntu releases, in the past using LVM required having a separate /boot/ partition, so I've been trained by Ubuntu to set that up.

> **theassociate said:**
> 
Also, because I didn't want to complicate things with my original post, I neglected to mention that, in addition to the two NVMe SSDs, my ZBook also has a standard 1TB SATA SSD. And this I plan to replace with a 5TB Seagate Barracuda HDD ASAP, based upon your recommendation. The setup I used in the old EliteBook 8770w laptop I've replaced was a 256GB SATA SSD for /boot, swap, and /, and a standard 1TB HDD for /home. Pretty straight-forward. I bought that rig back in 2012. Don't know why I just assumed that, in       2023, we would have perfected SSD technology to the point where       standard HDDs would be obsolete. Guess I was way off with that assumption.  :  )


I'm not a fan of Seagate storage and odd-sized storage seems to have higher failure rates than the standard 4, 8, 10, 12TB sizes according to all the reading I've done.  Seagate doesn't have the best name in quality storage. Of course, YMMV. I've been burned too many times by that company.  Oddly, in the 1990s, they were one of the customers of some software that my company/team built to help them manage the parts that go into all their different storage devices.  In the 1990s, they were a very different company.  I don't know exactly when, but their management changed in the early 2000s and started making questionable decisions that only engineers should be making, IMHO.  The last 2 Seagate HDDs I owned, both failed right around 12 months of use. One at 11months and the other around 13 months.

> **theassociate said:**
> 
So, after replacing the SATA SSD with a new 5TB HDD, do you still think I should open my new rig and remove the second NVMe that it came with so I don't shorten its life (even though I won't be using it)? Maybe just hold onto it as a back-up? Guess I didn't consider how the constant writing of video editing would shorten its life-span.

Electronic devices don't like heat.  SSDs generate heat if they have power.  Inside my systems, the SSDs report significantly higher temperatures compared to all other storage.

---

### Post by MAFoElffen on 2023-11-14
I have a bit different views... And TheFu is going to think I'm crazy:
```

mafoelffen@msi-ubuntu:~$ lsblk -e7 -o name,label,size,fstype,mountpoint,model
NAME        LABEL             SIZE FSTYPE     MOUNTPOINT             MODEL
sda                           3.6T                                   WDC WD40EZAZ-00S
&#9500;&#9472;sda1                         16M                                   
&#9500;&#9472;sda2      Win_G             3.4T ntfs       /home/mafoelffen/WIN_G 
&#9492;&#9472;sda3      Home_LTS        295.4G ext4                              
sdb                         465.8G                                   Samsung SSD 870
&#9500;&#9472;sdb1      System Reserved    50M ntfs                              
&#9500;&#9472;sdb2                      365.2G ntfs                              
&#9500;&#9472;sdb3                          1K                                   
&#9492;&#9472;sdb4                        508M ntfs                              
sdc                           3.6T                                   WDC WD40EZRZ-22G
&#9500;&#9472;sdc1                        128M                                   
&#9492;&#9472;sdc2      WIN_F             3.6T ntfs                              
sdd                           3.6T                                   WDC WD40EZAZ-00S
&#9500;&#9472;sdd1                         16M                                   
&#9492;&#9472;sdd2      20210604          3.6T ntfs                              
sde                           4.5T                                   ST5000DM000-1FK1
&#9500;&#9472;sde1                        128M                                   
&#9492;&#9472;sde2      WIN_H             4.5T ntfs       /Media_H               
sdf                           7.3T                                                   
&#9492;&#9472;sdf1      mpool             7.3T zfs_member                        
sr0                          1024M                                   HL-DT-ST DVDRAM GH24LS70
nvme2n1                       1.8T                                   Samsung SSD 990 PRO 2TB
&#9500;&#9472;nvme2n1p1 kpool             1.8T zfs_member                        
&#9492;&#9472;nvme2n1p9                     8M                                   
nvme0n1                       1.8T                                   Samsung SSD 990 PRO 2TB
&#9500;&#9472;nvme0n1p1 EFI               750M vfat       /boot/efi              
&#9500;&#9472;nvme0n1p2 bpool               3G zfs_member                        
&#9500;&#9472;nvme0n1p3 rpool             750G zfs_member                        
&#9500;&#9472;[COLOR=#ff0000]nvme0n1p4                   250G swap       [SWAP][/COLOR]                 
&#9500;&#9472;nvme0n1p5 hpool             359G zfs_member                        
&#9492;&#9472;nvme0n1p6 kpool             465G zfs_member                        
nvme1n1                     465.8G                                   PCIe SSD
&#9492;&#9472;nvme1n1p1 dpool             465G zfs_member                        
nvme3n1                     465.8G                                   PCIe SSD
&#9500;&#9472;nvme3n1p1                    16M                                   
&#9492;&#9472;nvme3n1p2                 465.7G ntfs                              

```
I have 164GB of fast RAM... And I still use my swap... Yes, that is 250 GB of swap on very fast disk. I thrash this workstation testing things, during big compiles, while I have many things running at once. And it sings. But I also have my own Conky on my desktop so I can keep track of how things are going, all the time. I can see things when they happen, to see if I need to adjust.

I have lots of disk, balanced between HDD, SSD and NMVe. I have 4 NMVe's in there right now, want to replace 2 of the smaller ones, and still have 5 empty NVMe slot open. I am slowly replacing the old HDD's with SDD's.

I do Volume Managers. I use both LVM and ZFS. Each has some perks that opens up a lot of possibilities, and let's things be flexible.

As for what should you do with you extra disk, use some of it for backup's, and the rest for what-if's... Things happen. And if you have a volume manager and some spare storage, they come in handy to add another slice wherever you need to.

---

### Post by TheFu on 2023-11-14
> And TheFu is going to think I'm crazy:

Yep, but there's a fine line between crazy and genius.  Hard to tell the difference sometimes.  I'm sticking you with "crazy" still. ;)  

But mainly because you are throwing money at expensive storage when cheaper HDDs would work too.  Oh ... and you have far too much NTFS!

---

### Post by MAFoElffen on 2023-11-14
But remember I still game to unwind... then test and verify Windows NEXT and Insider builds for Windows Desktop, Server... and beta test VMware vSphere, vCenter, ESXi releases and updates. But all that is getting less and less time spent in those, as time goes by. 

All my media files all on NTFS on HDD drives, as the media server stays up whether running Linux or Windows. HDD drives are just fine for media.  of the HDD SATA bays are hot-swap bays, 6 more SSD bays...  Then that 2 bay USB drive caddy. So booting from something that I have to test on metal is still somewhat convenient.

Most all my VM's are now on fast storage... They run as if they were on metal. I can crash and blow then up in no time flat! But seriously, it has opened up a lot of possibilities. I made sure I had lots of room in this new machine for adding more storage...

---

