---
title: "problem with grub2"
date: 2014-06-27
forum: Installation &amp; Upgrades
---

### Post by nkibm3 on 2014-06-27
hello,
i have a problem with grub2. when i try to do grub-install. i get an error.

```
sudo grub-install /dev/sda
Installing for i386-pc platform.
grub-install: warning: your embedding area is unusually small.  core.img won't fit in it..
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
```

i dont know what for information is relevant for this problem, so i think for begin i say a little bit and give more information after questions.

this my hdd's:

```
sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
112 heads, 45 sectors/track, 387604 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          45   268430399   134215177+   7  HPFS/NTFS/exFAT
/dev/sda2       268430400  1317007439   524288520    7  HPFS/NTFS/exFAT
/dev/sda3      1317009408  1933993983   308492288   83  Linux
/dev/sda4      1933993984  1953523711     9764864   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd3d0d3d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    68360191    34179072   83  Linux
/dev/sdb2        68362238    78163967     4900865    5  Extended
/dev/sdb5        68362240    78163967     4900864   82  Linux swap / Solaris
```

i use ubuntu 14.04 on /dev/sda3. but at time i can only boot from the 2. hdd (40 gb) with grub (+ ubuntu 14.04) on it, i boot then /dev/sda3 from 1. hdd. on the 1. hdd (1000gb) is a win bootmgr (win 7 loader).

(sorry my english is bad)

---

### Post by yancek on 2014-06-27
You apparently don't have enough room for core.img at the beginning of your disk.  Take a look at post 2 at the link below.  If you use GParted, use it from your Ubuntu CD or a GParted CD, not from the installed system.

[http://ubuntuforums.org/showthread.php?t=2045421](http://ubuntuforums.org/showthread.php?t=2045421)

---

### Post by nkibm3 on 2014-06-27
**ok. thx for the quick answer.** i have had so an idea little time ago, but i am very, very afraid of data lost. i cant do safety copys and if something is broken on /dev/sda this would be horrible for me.
thats so bad. then i think if i do i do boot ubuntu on the 2. hdd make it from there with gparted ant then move 1MB "right" /dev/sda1.

oh. oh. i dont like this. :(

---

### Post by yancek on 2014-06-27
I'm not sure if I understand what you are doing or for that matter, what you are trying to do.  You indicate in your first post that you have Ubuntu 14.04 on both the sda 1TB drive as well as on the 40GB drive.  Is that correct?  If so, why? You indicate you can boot Ubuntu on the 40GB drive and if I understand correctly, from that boot menu you can also boot the Ubuntu on the 1TB drive.  Is that correct?  Why do you then want to install Grub to sda?  You do understand that if you do that, you will overwrite the windows boot code in the master boot record.  What exactly is your final goal?

---

### Post by oldfred on 2014-06-27
Moving NTFS partitions also can be an issue. You definitely have to use chkdsk from a Windows repairCD or flash drive, so make sure you have those available.
Windows has in the partition boot sector info on partition start & size that must match partition table. Chkdsk will reset that info, but you have to be prepared as you will not be able to boot Windows until after it is fixed.

Not sure how you got sda1 to start at sector 45. Since Vista Windows partition tools  and for the last several years Linux partition tools have started partitions at sector 2048 like your sdb. And even XP started at sector 63.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by nkibm3 on 2014-06-28
> **yancek said:**
> You indicate in your first post that you have Ubuntu 13.03 on both the sda 1TB drive as well as on the 40GB drive.  Is that correct?
yes, but 14.04 on both.
> **yancek said:**
> 
Why do you then want to install Grub to sda?  You do understand that if you do that, you will overwrite the windows boot code in the master boot record.  What exactly is your final goal?
it is so: before this problem i had win xp and ubuntu 14.04 on the 1tb hdd (/dev/sda1 start at sector 63; grub installed, all working). on the 40gb hdd i had fedora.
someday i installed win7 on the 40gb hdd, but there was an "error" (maybe my fault) and the bootmgr (win7 loader) get installed to the 1tb hdd.
at this point i only could boot win7 on the 40gb or win xp on the 1tb hdd. i tried Super *Grub2* Disk and other things, but i didnt worked. so the only thing for help was to install ubuntu 14.04 on the 40gb.

now i setup in bios to boot standard the 40gb hdd. but from it i can only start  ubuntu on both hdd's. if i start the win7 loader on /dev/sda1 he starts but he cant load win xp on /dev/sda1. i can choose it but then system reboots (i think this make sense).
if i want to start win xp i have to boot at startup from the 1tb. it loads bootmgr i choose earlier windows version and it starts win xp normally.

my goal is to get back all fine as before. boot standard from the 1tb, boot grub and can choose win xp or my ubuntu 14.04.

but im really not sure. i thinked yesterday also about a point. i imagined it so: i move "right" 1mb /dev/sda1. i install back grub on /dev/sda but then ... he didnt find win xp (respectively the win 7 loader) OR he finds it but if he starts the win7 loader crashes and cant load win xp.

i dont know this all a good idea, or useful. but thats the story. 

PS: 
**thx** _@oldfred_ for the hint.

---

### Post by oldfred on 2014-06-28
Perhaps why you cannot boot Windows is somehow it got moved from the old XP sector start of 63 to 45. If start or size of any NTFS partition changes it will have major issues.

And sometimes chkdsk does not work or needs running until no errors as it does not fix everything on one pass.

       How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by nkibm3 on 2014-06-28
> **oldfred said:**
> Perhaps why you cannot boot Windows is somehow it got moved from the old XP sector start of 63 to 45. If start or size of any NTFS partition changes it will have major issues. [...]
*(if i boot from the 1tb hdd i can start win xp with the win7 loader [earlier windows version].)*
i have tried some windows tools in the recovery console (win xp) but the also give me warnings that something is wrong with my MBR, partition table and then a message like "if you can boot normal your system then dont do anything and stop!".
so i stopped.
i look again soon i think, like you described. thx.

---

