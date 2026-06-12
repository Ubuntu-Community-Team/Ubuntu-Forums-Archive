---
title: "Fresh PC (SSD) Install Ubuntu &amp; Windows 7"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by 02darkRS on 2011-09-19
I have searched three days for a similiar question or tutorial. I've learned a lot of great information on here & studied a few problem threads by other users for learning purposes but have not found anything unique to what I am trying to accomplish. 
 
Let me know if this is doable, adviseable, etc. Also, if there is a tutorial anywhere for this I would apprciate the redirect. I have found plenty showing the opposite: Windows install adding Ubuntu. 
 
Working with a fresh build here as follows: 
AMD Phenom II x4 965 Black Edition CPU
Biostar A780L3G MB
Zeus 650W PS
PCIe GEForce 9500
Barracuda 1TB 3.0Gbs 7200RPM
OCZ 60GB SSD 
Crucial 4GB DDR3 1066
Inside an ANTEC Two Hundred
<><>
 
I am getting Windows 7 free as a student but not until a month from now. I would like to install Ubuntu (NOW) & Grub on the SSD, then dual boot with Windows 7 (install next month). Is this doable &/or adviseable or should I wait until 7 is intalled to add Grub & Ubuntu? 
Everything I have found describes intalling Windows, then Ubuntu. I also, have not found any good tutorials on setting up a dual boot brand new out of box SSD. If you know of one or can provide direction that would also be great. 
 
My skill level: Advanced user of windows apps + took programming classes in C & VB 10 years ago + set up a few office networks. I have wiped a disk & reinstalled windows plenty of times but..... partitioning & starting fresh (especially on a SSD) is brand new to me.
 
(I have plenty of old HD's with Vista, XP, 7, etc but none of them would boot in my new machine. Most were from a dell or gateway which I heard will only work in their machines? Always booted to Windows Repair. *not the problem! just a side note on another approach to setting up the SSD with a windows HDD seperate install if I can get one working.)

---

### Post by Grenage on 2011-09-19
To be honest it's not that hard to install Ubuntu first, just make sure than Windows has a Primary partition available.  When you install Windows, it will wipe out Grub, but it's pretty easy to reinstall it.

---

### Post by 02darkRS on 2011-09-19
So, if I create a boot CD from Ubuntu download, I can just create a partition for it on the SSD. Use it until I get windows 7. Then create a partition for windows 7 & install it? 
 
If Grub will be wiped out upon W7 install, shouldn't I just wait to install it? Will it need it's own partition? 
 
I have found plenty on the size to make the W7 install. I planned to just give it whatever space Ubuntu & Grub do not need.
 
What size should the Ubuntu partition be? What File System is best in this install? The SSD will hold Ubuntu / W7 / Grub. The HDD will hold W7 User files, Ubuntu User Files, etc.

---

### Post by cryptotheslow on 2011-09-19
Well going by the MS info here:
[http://technet.microsoft.com/en-us/library/dd799232%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd799232%28WS.10%29.aspx)

Win7 needs a minimum of 15GB free for its partition.

I would look to put the root (/) partition on the SSD and /home (for your user directories) on the HDD

Knowing how fussy Windows can be - I would be planning ahead here. And would approach it like this:

1. Create a 40GB partition on the SSD, mark it as "Active" and format it to NTFS. This will be used when you come to install Win7. Even if you end up having to delete this partition to install Win7, at least it will end up being the first on the drive...  which Win7 may or may not be fussy about (dunno!).
2. Create a 20GB partition on the SSD and format to ext4. This will be for the / partition of Ubuntu.
3. Create an ext4 formatted partition of whatever size on the HDD. This will be for /home
4. Create 4GB swap format partition on the HDD.

If you intend to have a data partition that you can use to have files accessible in both Win7 and Ubuntu, create it on the HDD and format to FAT32 or NTFS.

You should be able to achieve all this using GParted from the LiveCD... and quite probably can be done when going through the install itself.

When you do install Win7 it will overwrite Grub - leaving you with a machine that just boots straight into Win7 only. However you will be able to restore Grub subsequently, that will then give you the option of choosing between Ubuntu and Win7 at boot time. How to do this is well documented in many places :)

---

### Post by 02darkRS on 2011-09-19
Thanks, I was actually just researching GPARTED. Sounds like I need to research LiveCD & it will provide the steps I am looking for. Great info, thank you.

---

### Post by Grenage on 2011-09-19
> **02darkRS said:**
> So, if I create a boot CD from Ubuntu download, I can just create a partition for it on the SSD. Use it until I get windows 7. Then create a partition for windows 7 & install it?
Indeed, or you can just create the partitions you plan to use, right from the start.  For example you may wish to have a 40GB Windows partition, and a 40GB Linux partition; you may wish for a 40GB Windows partition, a 30GB Linux partition and a 10GB Linux home partition.
 
> **02darkRS said:**
> If Grub will be wiped out upon W7 install, shouldn't I just wait to install it? Will it need it's own partition?
That's entirely up to you, but you can install grub from a liveCD with relative ease.

> **02darkRS said:**
> I have found plenty on the size to make the W7 install. I planned to just give it whatever space Ubuntu & Grub do not need.
You'll be able to manipulate partition sizes after they've been created by using gparted, but you tend to only do that if you really need to - there are some small risks.  If you can decide on the partitions sizes from day one, it's a plus.
 
> **02darkRS said:**
> What size should the Ubuntu partition be? What File System is best in this install? The SSD will hold Ubuntu / W7 / Grub. The HDD will hold W7 User files, Ubuntu User Files, etc.
Ubuntu should be using the Ext4 file-system as a default, which is fine; Windows will want to use NTFS, which is also fine.

My Ubuntu install is probably around 16GB, with another 60GB for my home directory.

---

### Post by cryptotheslow on 2011-09-19
Just picking up from Grenage. While it is true, partitions can be resized at any time relatively easily with GParted (provided the partitions are unmounted first). The general consensus seems to be that if you want to resize a Win7 partition you should do so using Win7's disk management tools and defragment first. I believe it can get a bit uppity if you use GParted to resize a Win7 partition.

---

### Post by Hakunka-Matata on 2011-09-19
> **02darkRS said:**
> So, if I [COLOR=Red]create a boot CD from Ubuntu download[/COLOR], I can just **[COLOR=DarkGreen]create a partition for it on the SSD[/COLOR]**. Use it until I get windows 7. Then create a partition for windows 7 & install it? 
 
If Grub will be wiped out upon W7 install, shouldn't I just wait to install it? Will it need it's own partition? 
 
I have found plenty on the size to make the W7 install. I planned to just give it whatever space Ubuntu & Grub do not need.
 
What size should the Ubuntu partition be? What File System is best in this install? The SSD will hold Ubuntu / W7 / Grub. The HDD will hold W7 User files, Ubuntu User Files, etc.
1. [COLOR=Red]create a boot CD from Ubuntu download [COLOR=Black]
[/COLOR][/COLOR]
[LIST]
[*][COLOR=Red][COLOR=Black](or a USB, 1GB is big enough, use unetbootin)[/COLOR][/COLOR]
[/LIST]
[COLOR=Red][COLOR=Black]2. [/COLOR][/COLOR]**[COLOR=DarkGreen]create a partition for it on the SSD[/COLOR]**. 

create 3 primary partitions, part# 1 & 2 for windows, you know what size you need.
[LIST]
[*]**Primary: #1, **ntfs, for WindowsOS,
[*]**Primary: #2,** ntfs, for spare primary, (will facilitate resizing, moving in future)
[*]**Primary, Extended: #3,** an Extended partition of all the unallocated space left.
[LIST]
[*]**Logical: #5,** 20Gib, Ext4 - type 83 - Linux,  mount point **/**
[*]**Logical: # 6,** all unallocated space left - 2GiB, Ext4 - type 83 - Linux,  mount point **/home**
[*]**linux-swap: # 7,** 2GiB, swap - type 82 -
[/LIST]
 
[/LIST]
*************************************************
since your SSD is only 60GB, you might want to create your sda6, /home partition on the other hard drive?
Leaving the first primary partition sitting created, but empty, leaves a space for the Windows OS, mark that partition 'boot' also, otherwise windows installer won't see it.

---

### Post by 02darkRS on 2011-09-19
> **cryptotheslow said:**
> Just picking up from Grenage. While it is true, partitions can be resized at any time relatively easily with GParted (provided the partitions are unmounted first). The general consensus seems to be that if you want to resize a Win7 partition you should do so using Win7's disk management tools and defragment first. I believe it can get a bit uppity if you use GParted to resize a Win7 partition.
 
This is on an SSD. Don't want to defrag that.... but i assume the rest applies?

---

### Post by oldfred on 2011-09-19
Partitioning and sizes are very personal and each of us have somewhat different suggestions once you get past the minimums.

I suggest the shared NTFS on your rotating drive. I have used a shared Windows format drive with my XP since 2006 without issue. I changed from FAT32 to NTFS and can only recommend NTFS for larger partitions as FAT does not have a journal (chkdsk or repairs will take forever) and cannot have any file over 4GB. I was backing up Ubuntu into a FAT partition and did not really notice every file was 4GB (truncated without any messages) or I never had a backup.

When first starting with Ubuntu my wife wanted all the emails & bookmarks from XP. So I moved Thunderbird & Firefox profiles to the shared partition and then those were identical in both systems. We reduced the amount in XP, but I still have one application I use occasionally.  I think for two years I promised to stop XP but still have not.

Some info on using gparted:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

With SSDs you need some settings to reduce writes.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

Arch recommends gpt but that is only with Ubuntu with BIOS or UEFI or Windows when booting with UEFI not BIOS. You will need MBR(msdos) with Windows.
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)

---

### Post by cryptotheslow on 2011-09-19
Good point on the defragmentation.

You may also want to look into possibly putting /tmp and /var (tempfiles and mostly log files) on the HDD as well as they are frequently written too.

As you're probably beginning to see - there is no "best" way when it comes to partitioning for Linux....   just what works best for you and your setup / usage. You can do pretty much anything you like. :)

---

### Post by 02darkRS on 2011-09-19
This seems obvious based on some of the directions provided but in order to avoid wasting a disk..... does gparted come as part if the ubuntu.iso LiveCD when I download it?
 
edit: nm I see one of the links provided says gparted comes with Linux installations.

---

### Post by 02darkRS on 2011-09-20
After more reading (thanks for all the links) & thinking, I believe this is what I have come up with: 
<><><><><>
60GB SSD:
**Primary: #1, **40GB, ntfs, for WindowsOS,
**Primary: #2,** 6GB, Ext4 - type 83 - Linux, mount point 
 
1TB HD:
**Primary: #1, ***_??GB_*, ntfs, for Windows items needing to be removed from SSD due to constant writing & size constraints *_(size not yet determined - need to review windows ssd install write ups again)_*
**Primary: #2, Extended: #3, **4GB*_+??GB _*
[INDENT]**Logical: #5,** 2GB, Ext4 - type 83 - Linux, mount point **/home** 
**Logical: #6, linux-swap:** 2GB, swap *_Ext4?_* - type 82 - 
**Logical: #7,** *_(??GB)_* /tmp & /var ----- *_NEED more info on these_*
[/INDENT]**Primary: #3, ***_500GB_*, ntfs - Shared Windows & Ubuntu Storage
 
<><><><>
 
Does this plan look like I am getting the hang of this?

---

### Post by oldfred on 2011-09-20
The 60GB SSD will have about 55GB usable, so I would just make / (root) be the rest of the SSD. If you have only 6GB even with /var separate you will have to do regular maintenance to keep it small.

Swap does not have a format, it is just a partition. Or you can use a file.
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")

If you have a separate /home I would make it bigger. Mine is tiny as I do a lot to redirect all saved info to other partitions. My Firefox & Thunderbird profiles are in the NTFS partition, my KmyMoney files are in my /data partition and any data in /home that is sizeable gets redirected to somewhere else. But all my system partitions including /home are in a 20 or 25GB / partition so they share available space until I move it or it is not needed.

I see many suggest a small /tmp and have also seen a few posts where users had issues. I think if you want to write a DVD, it preloads it into /tmp so you need the 4+GB for /tmp. Since you have a 1TB drive you so not have to have partitions on the small size that someone with only a 40GB drive may have to have.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by 02darkRS on 2011-09-20
Good point on the SSD, guess I'll just use it all. 

As far as /home goes. I plan to have a data partition also. I want all real data saved there. I don't exactly know what profile data gets saved to /home on either OS but since I normally just have a basic desktop picture, firefox theme, & bookmarks I would assume not much? Any real files or data I'd need would be saved on the NTFS shared data partition. 

still studying the rest of the data. thanks

---

### Post by 02darkRS on 2011-09-20
Ok, now that I have read & played with gparted I have some questions.

1. I played with gparted on partitioning the 60GiB SSD as follows:
/dev/sda
Partition #1 | ntfs | W7 | 40.04 GiB |  |  |  
Partition #2 | ext4 |  /   | 10.74 GiB |  |  | 

A. it auto populates align to MiB. Is this correct?
B. it does not let me flag as boot. Will that happen when I install the OS's on their respective partitions?

2. I plan for the 1TB HDD the following:

/dev/sdb
Partition #3 | ntfs | W7 apps | 100 GiB |  |  |  |
Partition #4 | Extended | 100 GiB |  |  |
                #5 | ext4 | /home | 20GiB |  |  |  |
                #6 | ext4 | /temp  | 20GiB |  |  |  |
                #7 | ext4 | /var     | 20GiB |  |  |  |
                #9 | linux-swap | 10GiB |  |  |  |
Partition #8 | ntfs  | data | 600GiB |  |  |  | 

A. Again aligning to MiB? should a HDD align to cylinders?
B. Why did it label sdb1 as sdb3? sdb2 as sdb4 & sdb8 on the extended partition as sdb9?
C. The windows apps partition is for the user files holding & all the other files/settings that will  require frequent writes. can those be on 1 partition or should they be on logical partitions separately?
D.  I read with the windows files & settings that I want to be on the HDD that I have to direct them manually at or after install. Is it the same with Ubuntu or will it see /home, /temp, etc & know to use it? Please provide a link for that if so. I've read the other links & did not find such information. 

I am typing this on the new system with LiveCd. So, we've gotten that far!

Also, on the windows link provided earlier it mentioned needing a system partition, windows partition, & a recovery partition for windows install. Thus should sda1 be a extended with 3 logicals?

---

### Post by srs5694 on 2011-09-20
> **02darkRS said:**
> Ok, now that I have read & played with gparted I have some questions.

1. I played with gparted on partitioning the 60GiB SSD as follows:
/dev/sda
Partition #1 | ntfs | W7 | 40.04 GiB |  |  |  
Partition #2 | ext4 |  /   | 10.74 GiB |  |  | 

A. it auto populates align to MiB. Is this correct?

Yes. See [this article I wrote](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for information on the consequences of doing this incorrectly on some types of modern disks. Although they aren't mentioned in the article, SSDs have similar issues, although the minimum alignment to get optimum performance with them is higher than with Advanced Format hard disks. AFAIK, all common modern disks work fine with 1 MiB alignment, which is why it's the default with newer partitioning tools.

> B. it does not let me flag as boot. Will that happen when I install the OS's on their respective partitions?

Neither Linux nor modern versions of Windows care about the boot flag, with the exception that the Windows boot loader uses it to locate the bootable partition. If you use GRUB as your MBR-based boot loader, the boot flag is therefore irrelevant. Chances are Windows will set the boot flag on its own partition, though (and put its boot loader in the MBR).

> A. Again aligning to MiB? should a HDD align to cylinders?

No! Although spinning hard disks do have cylinders, the cylinder values reported by partitioning tools have evolved from accurate representations of disk cylinders to convenient fictions to harmful fictions over the past couple of decades. Today, alignment should be to other values, as already noted.

> B. Why did it label sdb1 as sdb3? sdb2 as sdb4 & sdb8 on the extended partition as sdb9?

It's not clear what you mean by this. Please post the output of your partitioning tool, such as a GParted screen shot.

In general, though, partition numbers need not match on-disk order. The first four partitions by number are always primary partitions, but they can reside in any order on disk. Any one of them may be an extended partition. Logical partitions are numbered from 5 and up, and they may reside in any order on the disk. Keeping the partition numbers in the same sequence as the on-disk storage space can help avoid confusion, but is not strictly necessary. Typically, partition numbers match partition creation order, although details differ from one partitioning tool to another.

> C. The windows apps partition is for the user files holding & all the other files/settings that will  require frequent writes. can those be on 1 partition or should they be on logical partitions separately?

I'm not quite sure what you mean by this question. Are you asking if you should separate user data from application data in Windows? If so, I might do so, but it really depends on the exact nature of both types of data. Also, I'm less familiar with what Windows programs do with their data than I am with Linux, so somebody else might be better able to offer advice on this than I.

> D.  I read with the windows files & settings that I want to be on the HDD that I have to direct them manually at or after install. Is it the same with Ubuntu or will it see /home, /temp, etc & know to use it? Please provide a link for that if so. I've read the other links & did not find such information. 

Linux programs and their settings generally go in fairly well-defined locations, such as /bin and /usr/bin for user binary (program) files. These are laid out in the [Linux Filesystem Hierarchy Standard (FHS).](http://www.pathname.com/fhs/) You can create separate partitions for most (but not all) directories, in which case Linux will store the relevant files in those partitions automatically. Most Ubuntu users are well-served by a root (/) partition, a swap partition, and perhaps a /home partition. Your use of an SSD makes for a good case for splitting off some others, as you've done. (BTW, it should be /tmp, not /temp.)

---

### Post by ehidle on 2011-09-21
Forgive me if this is a stupid question, but why not simply run Windows 7 in VirtualBox on top of Ubuntu?

---

### Post by 02darkRS on 2011-09-21
ehidle, I've never used a virtual. I am sure it's much easier but I want to 1. learn from this & 2. physically install windows as, it's being used for school with particular OS needs. Not sure that a virtual machine will allow for running in XP mode. Plus, when my wife decides 5 minutes to learn ubuntu is too much.... i'll need Windows to be available as standard. 
 
srs5694: I cannot post a screen shot. Running from a liveCD last night. So, nothing was saved. 
 
What I mean is i created 2 partitions on sdb. it labeled them partition 3 & 4 instead of 1 & 2. Then the logical partition which should have been labeled partition 8 showed up as 9.
 
Will it store those in their respective directories on a seperate HDD automatically? I assume it would do that on the same drive but if the OS is on SSD & the respective directories are on the HDD will it still be automatic?

---

### Post by fiunchinho on 2012-08-02
What was your final setup? Any lesson learned? Im about to install my system for W7 and Ubuntu and I have a 60GB SSD aswell.

---

