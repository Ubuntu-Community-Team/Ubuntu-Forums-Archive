---
title: "Optimising mount options for ssd orvme drives using BTRFS (22.04)"
date: 2023-05-31
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2023-05-31
Musschler.dev has a long article on installing BTRFS. I am not proposing to follow all of his advice but I just need reassurance on the section step 3 below:
[https://mutschler.dev/linux/ubuntu-btrfs-20-04/](https://mutschler.dev/linux/ubuntu-btrfs-20-04/)

---------------------------------------------------------------------------------------------------
Step 3 (optional): Optimize mount options for SSD or NVME drives

Unfortunately, the Ubiquity installer does not set good mount options for btrfs on SSD or NVME drives, so you should change this for optimized performance and durability. I have found that there is some general agreement to use the following mount options:

    ssd: use SSD specific options for optimal use on SSD and NVME
    noatime: prevent frequent disk writes by instructing the Linux kernel not to store the last access time of files and folders
    space_cache: allows btrfs to store free space cache on the disk to make caching of a block group much quicker
    commit=120: time interval in which data is written to the filesystem (value of 120 is taken from Manjaro)
    compress=zstd: allows to specify the compression algorithm which we want to use. btrfs provides lzo, zstd and zlib compression algorithms. Based on some Phoronix test cases, zstd seems to be the better performing candidate.
    Lastly the pass flag for fschk in the fstab is useless for btrfs and should be set to 0.

We need to change two configuration files:

    /usr/lib/partman/mount.d/70btrfs
    /usr/lib/partman/fstab.d/btrfs

So let’s use an editor to change the following:

nano /usr/lib/partman/mount.d/70btrfs
# line 24: options="${options:+$options,}subvol=@,ssd,noatime,space_cache,commit=120,compress=zstd"
# line 31: options="${options:+$options,}subvol=@home,ssd,noatime,space_cache,commit=120,compress=zstd"

nano /usr/lib/partman/fstab.d/btrfs
# line 30: pass=0
# line 31: home_options="${options:+$options,}subvol=@home,ssd,noatime,space_cache,commit=120,compress=zstd"
# line 32: options="${options:+$options,}subvol=@,ssd,noatime,space_cache,commit=120,compress=zstd"
# line 36: pass=0
# line 37: options="${options:+$options,}subvol=@home,ssd,noatime,space_cache,commit=120,compress=zstd"
# line 40: pass=0
# line 56: echo "$home_path" "$home_mp" btrfs "$home_options" 0 0

====================================================================================

I want to set up my ssd drive so I was going to use his suggestions as to options that are listed at the top of the extract ie ssd, noatime, space_cache, commit=120 compress=zstd.


Should i make changes to the partman config drives? At present I do not have a partman partition. I think it is something that is installable. I am surprised that the options need changes via partman, hence the question.

---

### Post by #&amp;thj^% on 2023-05-31
I can't see anything wrong with Step 3, But why? The more we tinker, more chance of something going off the rails with updates.
Just my HO leave that sleeping dog lay.

---

### Post by MAFoElffen on 2023-05-31
Quote from that article:
> 
**I strongly advise to try the following installation steps in a  virtual machine first before doing anything like that on real hardware!**

Why? Because that is a fairly complex configuration, and if something went wrong, you would need experience and skills to be able to chroot into it to rescue the system... He is demonstrating that it "is" possible. Not that it is the best thing to do... It is possible. Is that what you need now? 

I applaud your determination in wanting to learn new things. You take on things that definitely will give yourself a challenge if something goes wrong. You understand that right?

On the recommendation of the author that I quoted above... Of course, "you" would need a ***working system*** to be able to do it that way (to practice that in a virtual machine), right?

I thought you were going to restore from your backups to get your system working again? Did you change your plan?

I'm just curious.

---

### Post by Robbyx on 2023-06-01
At present I have no btrfs options in my fstab. After the problems I have experienced recently I am particularly careful. 

I found that article when looking for guidance as to which options I should apply and how.  I take the point both of you are both making. I too had wondered if step 3 was overkill, or if it was advisable to apply those changes for the options to work in an optimum manner.  Rather than rush ahead and rely on packups to restore the system I decided to ask here for guidance. 

Is a  sensible way to add all the following (ssd,noa time,space_cache,commit=120,compress=zstd) with a timeshift backup (in a more secluded spot on my computer) so that I can restore the state as prior to the additions Are there any I should especially keep clear of, because they do not work well or efficiently?

R


> **MAFoElffen said:**
> Quote from that article:


I thought you were going to restore from your backups to get your system working again? Did you change your plan?

I'm just curious.

I posted a message into the thread. I wondered why you had not responded. In essence, the current useful backups were on the SSD drive (in a separate partition) and  so I could not use them.  l found another way to recover the system which I mentioned in that lastpost I made in the topic.

---

### Post by MAFoElffen on 2023-06-01
Oh dang. So starting all over from fresh?

I have a suggestion... This is what i do before a complex install for my test machines--- I make a plan, that includes the layout and what I want to do, with all the commands I need to do to do that... That way, for something like BTRFS, ZFS, LVM2... That way, I can see if it makes sense, before I even start.

Then booted from a LiveUSB, I can use "Try" and lay everything out. I can get the filesystem and all mounts taken care of from a Terminal, just by cutting and pasting the commands in...And cutting and pasting the output back in, or any changes I made to that. Or use GParted, if I want to go that way. 

While doing a complex install, I can use the document as a scratch pad. To make notes and jot down ideas of what worked, or didn't. What the device names were, so I can use them. Etc.

When I get that all laid out, and done... Then I do whatever I need to do in the install process, to install that system on the system. That install could be with the installer, mounted into that laid-out filesystem, or chrooting into it to rsynch or debootstrap a system into it...

That way, I  have a record to look back on of how that system went together, just in case I later have to make changes, or have to recreate it again. I learn a lot doing it that way, but also can look back on it to remember what I did.

---

### Post by #&amp;thj^% on 2023-06-01
Btrfs is different from traditional filesystems. It is not just a layer that translates filenames into offsets on a block device, it is more of a layer that combines a traditional filesystem with LVM and RAID. And like LVM, it has the concept of allocating space on the underlying device, but not actually using it for files.

A traditional filesystem is divided into files and free space. It is easy to calculate how much space is used or free.

Also tread lightly with my suggestions, 

Examining btrfs, Linux&#8217;s perpetually half-finished filesystem
This btrfs filesystem overview highlights some longstanding shortcomings.
Jim Salter - 9/24/2021, 5:30 AM
We don't recommend allowing btrfs to directly manage a complex array of disks&#8212;floppy or otherwise.
Enlarge / We don't recommend allowing btrfs to directly manage a complex array of disks&#8212;floppy or otherwise.
Faustino Carmona Guerrero via Getty Images
355 with

Btrfs&#8212;short for "B-Tree File System" and frequently pronounced "butter" or "butter eff ess"&#8212;is the most advanced filesystem present in the mainline Linux kernel. In some ways, btrfs simply seeks to supplant ext4, the default filesystem for most Linux distributions. But btrfs also aims to provide next-gen features that break the simple "filesystem" mold, combining the functionality of a RAID array manager, a volume manager, and more.

We have good news and bad news about this. First, btrfs is a perfectly cromulent single-disk ext4 replacement. But if you're hoping to replace ZFS&#8212;or a more complex stack built on discrete RAID management, volume management, and simple filesystem&#8212;the picture isn't quite so rosy. Although the btrfs project has fixed many of the glaring problems it launched with in 2009, other problems remain essentially unchanged 12 years later.
History

Chris Mason is the founding developer of btrfs, which he began working on in 2007 while working at Oracle. This leads many people to believe that btrfs is an Oracle project&#8212;it is not. The project belonged to Mason, not to his employer, and it remains a community project unencumbered by corporate ownership to this day. In 2009, btrfs 1.0 was accepted into the mainline Linux kernel 2.6.29.

Although btrfs entered mainline in 2009, it wasn't actually production-ready. For the next four years, creating a btrfs filesystem would display the following deliberately scary message to the admin who dared mkfs a btrfs, and it required a non-default Y to proceed:

Btrfs is a new filesystem with extents, writable snapshotting,
support for multiple devices and many more features.

Btrfs is highly experimental, and THE DISK FORMAT IS NOT YET
FINALIZED.
I use it only on my daily driver Arch, and when a sever is needed or come into play It's ZFS baby all the way. LOL

---

### Post by MAFoElffen on 2023-06-01
Very well said! 

That brings into play something I was going to ask about your new plan... What is your goal? I mean, since starting over, you have a clean slate to go from. I have BTRFS machines to test from, have used LVM2, mdadm, and combinations of both for years... But my daily drivers are all on ZFS, which I have used, beginning in 2015 with OpenSolaris... It covers my wants and needs.

You certainly have some choices open now, to venture where you want.

So what is your end-goal and what path to it would you like to take to that?

---

### Post by Robbyx on 2023-06-04
I thank you both  for your comments. Although there seems to be a slight misunderstanding about my current system's state, your comments were very useful. Thank you. 

There seems to be a  misunderstanding about my current system's state:  I am not starting fresh.  

I confirm that I have recovered everything including the original file system structures and data thereon. The SSD drive that was formatted to  btrfs for the root, home, and data, was safely restored in full with its btrfs format. The other drives still in EX4 were visible all along but I could not use them  because I was locked out of the root and home, and my passwords. 

I did not need to use the backups to restore any of the partitions including the BTRFS ones. So in effect I am back in the position I was prior to the lock out, but without the optimum partition options in fstab for btrfs. 

I am continuing to run the SSD with the original btrfs,  but I have  stripped back the btrfs fstab options to the minimum so as to reduce complication until I was sure I had a full recovery.  Now I wanted  to bring in the benefits of btrfs, and thus switch on some of the fstab options for the SSD drive, as  referred to in #4 ((ssd,noa time,space_cache,commit=120,compress=zstd). 

I started this thread because I do not want to find myself locked out again.  I think I may have been overly cautious.  

The article I quoted at the start looked complicated, but had an air of knowledge and expertise. In particular it claimed that changes were needed to specific root files, to make btrfs work at high efficiency.  I was surprised by this claim because I was aware that people are happy with Btrfs without making  changes to the root files. As per my opening  comment #1 the author explains how to make the improvements. I am not intending to follow all of the article. In fact at this stage I had intended to leave my btrfs system as is, other than adopting btrfs  options which improve its efficacy. Here is the quote again:

 > We need to change two configuration files:

/usr/lib/partman/mount.d/70btrfs
/usr/lib/partman/fstab.d/btrfs

So let’s use an editor to change the following:

nano /usr/lib/partman/mount.d/70btrfs
# line 24: options="${options:+$options,}subvol=@,ssd,noatime ,space_cache,commit=120,compress=zstd"
# line 31: options="${options:+$options,}subvol=@home,ssd,noa time,space_cache,commit=120,compress=zstd"

nano /usr/lib/partman/fstab.d/btrfs
# line 30: pass=0
# line 31: home_options="${options:+$options,}subvol=@home,ss d,noatime,space_cache,commit=120,compress=zstd"
# line 32: options="${options:+$options,}subvol=@,ssd,noatime ,space_cache,commit=120,compress=zstd"
# line 36: pass=0
# line 37: options="${options:+$options,}subvol=@home,ssd,noa time,space_cache,commit=120,compress=zstd"
# line 40: pass=0
# line 56: echo "$home_path" "$home_mp" btrfs "$home_options" 0 0

Am I correct in interpreting his changes as not fundamental to btrfs, but just adjustments to ensure that options are switched on if chosen in the fstab?

1Fallen quotes:

> Jim Salter - 9/24/2021, 5:30 AM
We don't recommend allowing btrfs to directly manage a complex array of disks—floppy or otherwise.


My setup is not a complex array of disks.  I do not have a raid system. The o/s is on a ssd as mentioned above. The rest are just for additional storage and backups via Backup and Timeshift. To me this means I am not clashing with Jim Salter's recommendation and do not need to reformat the ssd drive to something like EX4. Am I being reasonable and sensible, or just reasonable?

R

---

### Post by #&amp;thj^% on 2023-06-04
Robbyx please give me some time to create a Ubuntu on BTRFS, and yes i knew you weren't starting fresh. (we discussed in a PM)
Can you now show me/us this:
```
cat /etc/fstab
```
I'm going to give your link a good go over before saying anything else, I need proof of concept first. :)

---

### Post by Robbyx on 2023-06-04
cat /etc/fstab

> # / was on /dev/nvme0n1p2 during installation 
UUID=25f25728-d984-4438-aa0b-6cce43268fed /               btrfs   defaults,noatime,subvol=@   0 0

# /boot/efi was on /dev/nvme0n1p1 during installation 
UUID=BD0A-F1F2  /boot/efi       vfat    umask=0077      0       0

# /home was on /dev/nvme0n1p1 during installation 
UUID=5bb8aa95-b657-4297-be5b-4352a09596b0 /home           btrfs   defaults,noatime,subvol=@home 0  0

#/dev/nvme0n1p4: LABEL="Data" 
UUID=f5ab46ce-b3da-4e59-8f18-3418fe272a09 /media/robins/data_sdde btrfs  defaults,noatime   0  0

#----------------------------------------SSD 250GiB
#/dev/sdc5: LABEL="mydocs" on SSD_250 *
UUID=8d99bfc8-90ab-4488-b7da-87e7676aff19 /media/robins/mydocs_sdd ext4 defaults,noatime 0 0

#/dev/sdc6: LABEL="Data inc AV" on SSD_250 *
UUID=1a2e8d10-7b93-4de1-b551-31db6a621276  /media/robins/data_inc_av_sdd ext4 defaults,noatime 0  0

# swap was on /dev/sdc7 during installation *
UUID=6bbc8a5a-b488-49b6-904a-952e05463815 none            swap    sw              0       0

#----------------------------------Hitachi HD 750GiB

# sdc1 hitachi 750GiB
UUID=3c4f4688-4bd7-4262-a2b8-86f71bbd6d0b /media/robins/hitachi_750GiB ext4 defaults,noatime 0 2

#/dev/sdc2: LABEL="Deju_dup_backup" 
UUID=c79b648e-48c5-45db-949f-a835928f3816   /media/robins/hitachi_deju_dup ext4 defaults,noatime 0 2
# -------/dev/sda1: Western Digital HD 500Gib

UUID=32677e49-0894-4d3f-8cc4-7e27b74ac6f0  /media/robins/western_digital_500gib_hd ext4 defaults,noatime 0 2


---

### Post by #&amp;thj^% on 2023-06-05
It never fails, when I reply to posts, i get wrapped up in something else.
Robbyx had i looked closer at that link posted, all of that has to be done at install time only.(even step 3)
My new install looks:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=48d833f3-d5bb-4467-9487-f430d471babf /               btrfs   defaults,subvol=@ 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=4971-5C55  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/nvme0n1p2 during installation
UUID=48d833f3-d5bb-4467-9487-f430d471babf /home           btrfs   defaults,subvol=@home 0       2
# swap was on /dev/nvme1n1p2 during installation
UUID=839fb0a6-5151-49db-a408-bac6cf9ff7f3 none            swap    sw              0       0

```

That new fstab is very different than my Arch report but oh well.
And it looks to me like you always use "Deju_dup_backup" and I don't so not much help from me there. (sorry)
I use snapper for my snapshots.(back-ups and restore)
Following that link with a live installer:
```
me@me-Lenovo-Legion-5-15ARH05:~$ cat  /usr/lib/partman/mount.d/70btrfs
cat: /usr/lib/partman/mount.d/70btrfs: No such file or directory
me@me-Lenovo-Legion-5-15ARH05:~$  /usr/lib/partman/fstab.d/btrfs
bash: /usr/lib/partman/fstab.d/btrfs: No such file or directory

```

---

### Post by Robbyx on 2023-06-05
Thank you for your help. I have come across partman before.

robins@robins-desktop:~$ partman
Command 'partman' not found, but can be installed with:
sudo apt install ubiquity
robins@robins-desktop:~$ 

R

---

### Post by #&amp;thj^% on 2023-06-06
Well I really wasn't much help at all, but thanks for the kindness.
I'm not so sure I like BTRFS on Debian. :(
I have zero problems with just this:
```
cat /etc/fstab
# /dev/sdb3
UUID=95259b8c-a6c0-4c55-834c-882c971af825	/         	btrfs     	rw,relatime,ssd,space_cache=v2,subvolid=5,subvol=/	0 0

# /dev/sdb1
UUID=0D3A-1DF1      	/boot     	vfat      	rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=ascii,shortname=mixed,utf8,errors=remount-ro	0 2

# /dev/sdb3
UUID=95259b8c-a6c0-4c55-834c-882c971af825	/home     	btrfs     	rw,relatime,ssd,space_cache=v2,subvolid=5,subvol=/	0 0

# /dev/sdb2
UUID=abd40114-ef48-4a55-996c-b4c919c6360e	none      	swap      	defaults  	0 0


```
With all kinds of disk storage, but no Raids on Btrfs.

---

### Post by MAFoElffen on 2023-06-06
But then this:
```

mafoelffen@ubuntu-btrfs01:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=d1644cfc-aa1e-417e-b21f-1d2a55ae5895 /               btrfs   defaults,subvol=@ 0       1
# /boot was on /dev/sda2 during installation
UUID=67677bbf-242e-40b2-a3bf-7cda46662260 /boot           btrfs   defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=C5EE-AFED  /boot/efi       vfat    umask=0077      0       1
# /data was on /dev/sda5 during installation
UUID=2ee02f47-ed28-4ae9-80fc-9b52d7152187 /data           btrfs   defaults,subvol=@data 0       2
# /home was on /dev/sda4 during installation
UUID=e3e0ff0b-1023-46f1-898c-f1acc726f571 /home           btrfs   defaults,subvol=@home 0       2

```
This is Ubuntu LTS 22.04, installed via using the 22.04.2 install ISO... Using "Try", the creating the partitions, filesystems, and subvols manually. Then rebooting the Live Image Environment, starting the installer, and letting the installer's partition manager (partman) to see the storage & filesystems, using "Other" to mount the seen BTRFS filesystem's subvols... Using 'use as' to wire the mounts together correctly... Then continue the installation.

Note that subiquity is filesystem aware and you can still do that, up to Lunar 23.04. The new installer, starting at 23.04 is not filesystem and file manager aware, so, in my opinion, is broken. I am joined in a Bug Report to try to get that fixed for future versions. This is not just as described, but for all file managers: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977)

Note: On 1fallen's mention of BTRFS RAID... Well... I keep this link handy and refer to it from time to time. Look at this: [https://btrfs.readthedocs.io/en/latest/Status.html](https://btrfs.readthedocs.io/en/latest/Status.html)

That is the current status page of BTRFS, based on a kernel version of Linux kernel 6.3. RAID 0, 1, 10 is marked as stable. RAID's 5 & 6 are still considered as unstable.

---

### Post by #&amp;thj^% on 2023-06-06
> **MAFoElffen said:**
> 
Note that subiquity is filesystem aware and you can still do that, up to Lunar 23.04. The new installer, starting at 23.04 is not filesystem and file manager aware, so, in my opinion, is broken. I am joined in a Bug Report to try to get that fixed for future versions. This is not just as described, but for all file managers: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977)

Note: On 1fallen's mention of BTRFS RAID... Well... I keep this link handy and refer to it from time to time. Look at this: [https://btrfs.readthedocs.io/en/latest/Status.html](https://btrfs.readthedocs.io/en/latest/Status.html)

That is the current status page of BTRFS, based on a kernel version of Linux kernel 6.3. RAID 0, 1, 10 is marked as stable. RAID's 5 & 6 are still considered as unstable.
Yep 23.04 was my effort to help with this, thanks MAFoElffen I knew something was very different.
And i would add myself to that Bug link.....But you know the rest of that story. LOL

---

### Post by #&amp;thj^% on 2023-06-07
This is pretty darn nice as well:
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a device; this may
# be used with UUID= as a more robust way to name devices that works even if
# disks are added and removed. See fstab(5).
#
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=A4AE-CC2F                            /boot/efi      vfat    defaults,noatime 0 2
UUID=58260458-9182-455e-a6bd-6addaecf162e /              btrfs   subvol=/@,defaults,noatime,compress=zstd 0 0
UUID=58260458-9182-455e-a6bd-6addaecf162e /home          btrfs   subvol=/@home,defaults,noatime,compress=zstd 0 0
UUID=58260458-9182-455e-a6bd-6addaecf162e /var/cache     btrfs   subvol=/@cache,defaults,noatime,compress=zstd 0 0
UUID=58260458-9182-455e-a6bd-6addaecf162e /var/log       btrfs   subvol=/@log,defaults,noatime,compress=zstd 0 0
tmpfs                                     /tmp           tmpfs   defaults,noatime,mode=1777 0 0

```
Now I just need to add my back-up /dev.
EDIT:6/20/2023
This is bit more complex, but I'm keeping this one:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# systemd generates mount units based on this file, see systemd.mount(5).
# Please run 'systemctl daemon-reload' after making changes here.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/kaisenlinux--vg-root /               btrfs   acl,noautodefrag,barrier,compress=zstd,datacow,datasum,discard=async,noflushoncommit,space_cache=v2,treelog,noatime,nodiratime,subvol=@ 0       0
# /boot was on /dev/sdb2 during installation
UUID=5bcfea5b-8efd-4ddd-86c8-c22c5de9b06d /boot           btrfs   acl,noautodefrag,barrier,compress=zstd,datacow,datasum,discard=async,noflushoncommit,space_cache=v2,treelog,noatime,nodiratime,subvol=@boot 0       0
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=A4AE-CC2F  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/nvme0n1p2 during installation
UUID=cd45c578-8f5b-4eca-8ab9-3ae7da40e749 none            swap    sw              0       0
# swap was on /dev/nvme1n1p2 during installation
:


```

---

