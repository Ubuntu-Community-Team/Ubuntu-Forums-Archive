---
title: "LVM with RAID1 for server"
date: 2024-10-05
forum: Installation &amp; Upgrades
---

### Post by SBFree on 2024-10-05
After years of using Ubuntu, I still find new things to do that make me realize that I don't know what I don't know, please forgive what may be a trivial question.

I am trying to build a server and want to use LVM. It has three drives and I would like to use the two of them (sda & sdb) as Logical Volumes configured as RAID1.

Do I need a linux swap partition on the boot drive? It looks like I set this up but not sure it is necessary.

The device nvme0n1 has about 700Gb that has not been partitioned and I would like to use this as a place to store backups. Would creating an EXT4 partition to do this be the best approach?

Once sda & sdb are part of an LVM RAID1 array, I would like to move some sub-directories from / to the array. Is that possible and if so how? Are there preferable sub-directories to move or leave behind to facilitate backup/restore?

Thanks in advance for suggestions.
scott
```

scott@scott-server:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT -e7
NAME                      FSTYPE        SIZE MOUNTPOINT
sda                                   465.8G 
&#9492;&#9472;sda1                    LVM2_member 465.8G 
sdb                                   465.8G 
&#9492;&#9472;sdb1                    LVM2_member 465.8G 
sdc                                    14.9G 
&#9492;&#9472;sdc1                    vfat         14.9G /media/scott/68C6-10F5
nvme0n1                               931.5G 
&#9500;&#9472;nvme0n1p1                               1M 
&#9500;&#9472;nvme0n1p2               ext4            2G /boot
&#9500;&#9472;nvme0n1p3               LVM2_member 197.1G 
&#9474; &#9492;&#9472;ubuntu--vg-ubuntu--lv ext4        189.5G /
&#9492;&#9472;nvme0n1p4               swap         31.3G 

```

---

### Post by TheFu on 2024-10-05
All your questions seem to be a matter of opinion.  "Best" is always a matter of opinion.  Same for "referable".  We all have different tastes and different knowledge.

I don't see any RAID1 storage.  Do you intend to use mdadm or LVM to create the RAID1?  I've posted an example of LVM  RAID1 for the entire OS in these forums before.  I have a personal dislike of the way that LVM-RAID appears in the lsblk tool - it is a bit ugly.  My preference, since testing the LVM-RAID solution would be to use mdadm to create a RAID array for sda1/sdb1, get an md0 device, then use the md0 device as the LVM PV.  

Definitely test what happens with whatever RAID you use to unsure you gain recovery experience when 1 of the HDDs fails.  I found the LVM-RAID more difficult to recover using than mdadm.  But for the full OS, Ubuntu doesn't make using mdadm for the OS easy.

Anyways, I'll provide more of my opinion about a few of the questions.
Does swap need to be on the boot storage device?  No.  In fact, if your workload will use swap at all (ram is cheap!), then placing swap onto the slowest HDD you have would allow users to "feel" the system getting slower long before swap on an SSD would.  IMHO, we want to "feel" the system get slow, before it crashes, due to OOM issues, so we can take action to relieve the RAM deficit. 

IMHO, using SSD storage for backups is stupid.  Enough said on that.  SSDs should be used for primary storage, not backups.  Backup storage should be the cheapest storage you'll trust for backups.  SSDs are 10x more expensive than any HDD storage, aren't they?

Moving storage from anywhere except boot can be done.  It just needs to appear to be in the correct location in the directory.  That can be causes using correct mounts in the fstab or using symbolic links, if you are willing to have an extra level of redirection (I wouldn't for the OS).

The ubuntu--vg-ubuntu--lv LV is huge. Why?  use **lvreduce** after booting from alternate media to reduce it to 35GB or less.  Especially for a server with LVM, even 35G should be overkill.  Here's a real system using LVM where I reduced it to 35G and about 8GB was used for the server OS.  35G looks to be 3x larger than necessary, but YMMV, of course.
```
$ df /
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01   35G  7.8G   25G  24% /

```
I do create other LVs for storage that is included by default under /.  Personal preference. Here's a custom OS layout on a 20.04 server.  I have about 6 months to decide what the next OS it has will be.  Probably not Ubuntu, I'm sad to say. 
```
$ lsblkt
NAME                              TYPE  FSTYPE              SIZE FSAVAIL FSUSE% LABEL       MOUNTPOINT
nvme0n1                           disk                    931.5G                            
&#9500;&#9472;nvme0n1p1                       part  ext2                  1M                            
&#9500;&#9472;nvme0n1p2                       part  vfat                 50M   43.8M    12%             /boot/efi
&#9500;&#9472;nvme0n1p3                       part  ext4                700M  313.9M    46%             /boot
&#9492;&#9472;nvme0n1p4                       part  LVM2_member       930.8G                            
  &#9500;&#9472;vg01-swap01                   lvm   swap                4.1G                            [SWAP]
  &#9500;&#9472;vg01-root01                   lvm   ext4                 35G   24.7G    23%             /
  &#9500;&#9472;vg01-var01                    lvm   ext4                 20G   13.7G    25%             /var
  &#9500;&#9472;vg01-tmp01                    lvm   ext4                  4G    3.6G     2% tmp01       /tmp
  &#9500;&#9472;vg01-home01                   lvm   ext4                 20G    7.3G    58% home01      /home
  &#9500;&#9472;vg01-libvirt--01              lvm   ext4                137G    2.8G    98% libvirt--01 /var/lib/libvirt
```

I don't bother with RAID for the OS since switching to quality SSDs.  Had a discussion with a storage vendor at a conference about SSD failures and he said they love to take the money, but that failures for quality SSDs happen very infrequently.  He doesn't bother with RAID.  I am religious about daily, automatic, versioned, backups.

With LVM, much of the flexibility comes from having spare room inside the VG for snapshot uses and to add more storage to file systems when it is needed.  I've never guessed the correct, needed size before and after 30 yrs of trying, I'll just go with flexible storage management instead.  You can find descriptions of that layout in other posts here - why I did it and why they are sized as they are.

---

### Post by SBFree on 2024-10-05
Thank you for the reply. RAID1 was set up after the post. Your response has made me rethink using it at all. I'm off to try a another install without RAID. I am going to try and work through recreating what you displayed in your response, shrinking the LV created by the installer. In your example, how do I refer to the 'vg01-home01' reference? Is it a Physical Volume or Volume Group or Logical Volume? How do I create the the blocks(?) listed under nvme0n1p4 and give them mount points like the ones in your example? The installer from Ubuntu with the Graphical User Interface allows installing with LVM but uses the entire disk as in my first post. I reinstalled and then started the machine with a live USB, resized with

```

sudo lvresize --resize-fs -L -850G /dev/ubuntu-vg/ubuntu-lv
```

then used GParted to shrink the partition. That didn't seem right and I have no idea how to the create the mount points shown in your example or how to actually get the files from the directory home that already exists to the new one.
That left me with 

```

ubuntu@ubuntu:~$ sudo lsblk -e7
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda                         8:0    0 465.8G  0 disk 
sdb                         8:16   0 465.8G  0 disk 
sdc                         8:32   1   7.5G  0 disk 
&#9492;&#9472;sdc1                      8:33   1   7.5G  0 part /cdrom
nvme0n1                   259:0    0 931.5G  0 disk 
&#9500;&#9472;nvme0n1p1               259:1    0     1M  0 part 
&#9500;&#9472;nvme0n1p2               259:2    0     2G  0 part 
&#9492;&#9472;nvme0n1p3               259:3    0  50.5G  0 part 
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 252:0    0  50.5G  0 lvm 
```

I'm off to read an LVM tutorial. Is installing the server version of Ubuntu make using LVM more straight forward?
Thanks for reading and any further suggestions.
scott

---

### Post by TheFu on 2024-10-05
For a custom LVM setup, I get to choose all the VG and LV names. No default names for me.  I've learned that the default names can conflict if I need to move the storage to another system temporarily, so I avoid that issue.  My VG names are unique across all my systems, but aren't tied to any hostname or purpose.  I've learned better over the decades, the hard way.  Of course, it is possible to use **vgrename**, but if I can avoid an issue, why not?

a) you can't use any Ubuntu Desktop v24.04.  Canonical decided that LVM isn't important for desktops.  This was "new" in 24.04, though I don't have any Ubuntu 22.04 or later desktops to actually know.  I did test a few 24.04 desktops and the server.  Desktops - no LVM in the installer.  The server install seemed to be the same as in prior releases. LVM worked fine.

b) I setup my LVM layout BEFORE getting to the "do something else" part of the installer.  Normally, I toggle to a different TTY, pull a script over using ssh/scp from another system, customize the script (all my systems are a little different), run the script, often, manually, select/pasting lines grouped by task, then after all the require partitions, LVs and file systems have been created, I toggle back to the installer and "hook up" the different partitions and LVs where they need to be mounted inside the installer.  

c) The only time I just let the installer go with defaults is on laptops because I want LUKS encryption on my laptops, always, period.  Then I have to go back and fix things post-install because I'm not 100% certain I understand how LUKS, crypttab, initramfs, and grub all fit together.  Nobody knows everything. It is a hassle. Setting up the old mounts and new mounts for the stuff to be moved over is a hassle. Moving entire directories between different file systems takes time.  Then ensuring the fstab mounts the correct, new, LV with the correct, data in the right place is just accounting, but necessary.  If I wasn't distracted doing this (kids, SO, phone, etc.), I'll delete the files from the old storage locations before booting into the fresh OS again.  If I was distracted, then I could have made a mistake somewhere and need to be more cautious.  I'm like a dog that sees a squirrel - need to stay on 1 task at a time for anything with lots of accounting/details, to prevent bonehead mistakes.

Working through an LVM tutorial is a good thing.  Do some testing with small amounts of storage too.  10MB LVs teach just as much as 100GB LVs when it comes to LVM knowledge and skills.  No need for me to answer the other questions. You'll understand after you work through a tutorial.

---

### Post by tea for one on 2024-10-06
> **TheFu said:**
> you can't use any Ubuntu Desktop v24.04.  Canonical decided that LVM isn't important for desktops.  This was "new" in 24.04, though I don't have any Ubuntu 22.04 or later desktops to actually know.  I did test a few 24.04 desktops and the server.  Desktops - no LVM in the installer.  The server install seemed to be the same as in prior releases. LVM worked fine.
LVM options are available during the installation process for Ubuntu 24.04.
Erase Disk and install Ubuntu > Advanced features > Use LVM or Use LVM and encryption
Screenshots here [https://ubuntu.com/blog/ubuntu-desktop-24-04-noble-numbat-deep-dive](https://ubuntu.com/blog/ubuntu-desktop-24-04-noble-numbat-deep-dive) (Additional encryption options)

---

### Post by TheFu on 2024-10-06
> **tea for one said:**
> LVM options are available during the installation process for Ubuntu 24.04.
Erase Disk and install Ubuntu > Advanced features > Use LVM or Use LVM and encryption
Screenshots here [https://ubuntu.com/blog/ubuntu-desktop-24-04-noble-numbat-deep-dive](https://ubuntu.com/blog/ubuntu-desktop-24-04-noble-numbat-deep-dive) (Additional encryption options)

I tried setting up LVM with Xubuntu and Lubuntu installs. Nope. Nothing I did would make LVM actually possible.  After 4 attempts with Xubuntu, 2 with Lubuntu.  I even tried the "Use LVM" next-next-next option as the last scenario before giving up. I gave up and did a "next-next-next" install without LVM to test everything else.  

The LVM option is there, but it cannot be used to connect LVs to mount points in 24.04 desktops.  In ubuntu server, it works. Not desktops, unless they added it back in 24.04.1 desktop installs.  I haven't bothered with 24.04.1 at all.  I'll try it later today, but not with Gnome DE. I hate the Gnome desktop bloat.  The OP is probably going to use Ubuntu Server (no GUI) anyway.

When 24.04 was first released, there were a few discussions here about LVM support being disabled.  A bug was opened.  The answer was that supporting MSFTs default disk encryption had forced a change in the installer's back-end partitioning tool and that LVM wasn't supported in that tool.  They hadn't cleaned up the installer GUI to remove the LVM option for some reason.

I know that LVM+LUKS works on Linux Mint 22 (24.04-based). Guess the Mint guys didn't bother changing the partitioning back-end tool.

I really hope I'm wrong.

---

### Post by Dennis N on 2024-10-06
At this point in time, if you intend to install Ubuntu (not server) to an existing LVM logical volume or volumes of your creation, you must start with a supported release that uses the Ubiquity installer. The most recent supported release that used Ubiquity would be 22.04 LTS. After that is done, you do an in-place upgrade to 24.04 LTS.

See:
[https://ubuntuforums.org/showthread.php?t=2497556&p=14191185#post14191185](https://ubuntuforums.org/showthread.php?t=2497556&p=14191185#post14191185)

---

