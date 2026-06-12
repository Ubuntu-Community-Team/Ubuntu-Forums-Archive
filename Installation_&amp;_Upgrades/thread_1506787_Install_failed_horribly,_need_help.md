---
title: "Install failed horribly, need help"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by Drax99 on 2010-06-10
Please bear with me, as I am a Linux noob, so need small words and big pictures.  What I basically was trying to do is, make a bootable partition on my portable HD, for the occasional Linux exploration, and mebbe help with recovering failed windows installs for file recovery.  Primarily I use Windows 7 Ultimate on my HP computer, and only started dabbling with Linux at the encouragement of my Linux Guru friend.  Things have gone horribly wrong and I really would appreciate any help I can get.

The story:
Back in the day I installed the Ibex release of ubuntu on my drive with no issues, messed with it for a week and then shelved it.  I tried loading it up again later, but had forgotten whatever password I put on it, so it went on my todo list for re-installation at a later date

Well now I am trying to reinstall, downloaded the new WUBI installer, and installed without a hitch.  Well,, so it seemed.  First off, it never noticed my previous install.  Both Linux and windows acted as if the previous partition didn't exist.  I had to do math to notice I was still missing 10gb.  I checked in the disk tool, and disk management, and ther it was, hiding as "10gb space".  Not knowing any way to reclaim that space, or format it into one of the other partitions, I used disk manager to delete all volumes and partitions, then format the disk.  Worked fine, rei-ran WUBI, and installed Linux again.  However every time I rebooted to the drive, I recieved a error 22 from GRUB, and windows didn't even recognize that there was another bootable drive.  Had to manually select the drive to boot to it (producing the error).  Befor this, the windoes boot manager saw Ubuntu just fine and offered to boot it.

Now, after a brainstorming session and alotta internet searching, me and my friend decided on a plan of action.  I created a live CD, booted to it, and used it to reformat the partitions, and reinstall Ubuntu.  Worked like a charm!  Or so I thought.   After playing blissfully with my new toy for a hour, I shut down, unplugged the drive and rebooted.  My computer didnt like that.  After the POST screen I was greeted with a nasty error that no such volume existed, and the console prompt of GRUB rescue>

So.. seems something ate my windows MBR.  If I plug the drive back in, GRUB happily gves me a low-rez option menu for booting, and will let me boot into whatever I want, but without the portable drive, my PC is now a toaster.

Help please?

---

### Post by darkod on 2010-06-10
With multiple disks, and especially when installing on usb hdds you ALWAYS need to check during the install where grub2 will get installed. You do that by clicking the Advanced button in the last screen, before clicking Install.

Connect the portable, boot ubuntu and in terminal execute:

sudo fdisk -l (small L)

Post the results and we'll sort it out.

---

### Post by Drax99 on 2010-06-10
I'd like to add, I REALLY dont wanna restore my computer. takes me over a day to get it back to the way I ahve it.  And I would much rather let windows boot manager handle thing, since Linux will only be a part-time resident on my system anyway.  Id be happy to just have my windows machine back to normal at this point.  I like Linux, but its really pissing me off right now.
 
Oh, and is there some reason I cannot post here with firefox?  Ugh, had to post using IE.  Message kept getting eaten when I hit submit using the firefox engine.

---

### Post by Drax99 on 2010-06-10
Answered one of my questions, It seems I had Yahooapis blocked with noscript, preventing me from posting.  Here is the reslts, hope it helps.  The drive I have Ubuntu installed on is a 160gb WD Passport.  Linux sees it as sdb

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       76258   612435968    7  HPFS/NTFS
/dev/sda4           76258       77826    12591104    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2490    19998720   83  Linux
/dev/sdb2            2491       19457   136287427+   7  HPFS/NTFS

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xab80ac67

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS

---

### Post by darkod on 2010-06-10
Since you can boot in ubuntu with the portable connected, you only need to install grub2 to the MBR of /dev/sdb then:

sudo grub-install /dev/sdb

To remove the grub2 from /dev/sda and get windows booting without the portable, either run the repair process with windows install cd/dvd, or as quick fix from ubuntu just run:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give. That will install generic mbr on /dev/sda which does the same job as windows mbr. And much cleaner solution than windows repair process.

After that you should be fine.

---

### Post by Drax99 on 2010-06-10
thanks much, fingers crossed

---

### Post by Drax99 on 2010-06-10
You rock!:guitar:  Windoze is back to clean and sober after kicking the addiction to my external drive.   Havnt rebooted the Linux drive yet.. seriously just wanna leave it be till I overcome my cravings to beat it with a hammer.  I'll go back and play with it tomarrow, on my day off!
 
Thanks a million!

---

