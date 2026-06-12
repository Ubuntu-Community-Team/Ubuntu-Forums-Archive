---
title: "Vista and Ubuntu 10.04 Dual Boot Problem"
date: 2013-04-06
forum: Installation &amp; Upgrades
---

### Post by cobras on 2013-04-06
Hey Folks,

I know it's going to seem that I'm posting a question that's already been answered elsewhere, but I've followed several threads here and on other forums, and I've tried suggestions found by searching the web.  No luck

My machine was running Vista 7 just fine, but I do a lot of image editing and prefer GIMP, so I installed Ubuntu 10.04 alongside Vista.  All was well for a week or so until I got Error 17.

As I understand it, the solution to Error 17 is to reinstall GRUB.  I've tried to do this by several methods, all of them similar, but none of them work.  The last method I tried comes from _Getting Started with Ubuntu_ by the Ubuntu Manual Team.  This method consists of the following series of commands:

$ sudo fdisk -l
$ sudo mkdir /media/root
$ sudo **mount** /dev/sda1 /media/root
$ ls /media/root
$ sudo grub-install --root-directory=/media/root /dev/sda

This solution makes good sense to me, but once I get to the **mount** command a message tells me the file type must be specified.  The command 'file /dev/sda5' (sda5 corresponds to my Linux device) returns something like 'block special (8/5)', which is not what the command line commands.

Any suggestions?

By the way, I know from the output of the first command (sudo fdisk -l) that my machine is booting to the Vista device.

Thanks in advance,
cobras

---

### Post by oldfred on 2013-04-06
Error 17 is from grub legacy, grub2 does not use error numbers. So your 10.04 is an upgrade? Or did you install grub legacy manually as 10.04's default was grub2 unless you upgraded.

[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

If system was working and you get this error, it may be corruption and you need to run fsck?

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

You can use this tool, but it does not fix grub legacy, but will offer to upgrade to grub2. Otherwise just post link to its BootInfo report.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by cobras on 2013-04-07
> **oldfred said:**
> Error 17 is from grub legacy, grub2 does not use error numbers. So your 10.04 is an upgrade? Or did you install grub legacy manually as 10.04's default was grub2 unless you upgraded.

Good question.  I installed 8.04 and updated completely before upgrading to 10,04.  10.04 was fully updated when it started acting up.  Is it possible that one of these updates included an upgrade of GRUB?  I ask because your suggestion 'sudo e2fsck -f -y -v /dev/sdb1' managed to patch up my system enough that it now boots up - though it clearly still has issues.  No offer to upgrade GRUB.

I'll report back as I get time to investigate further.

Thanks,
cobras

---

### Post by oldfred on 2013-04-07
If you are happy with grub legacy, I would not necessarily change.

The main reason for grub2, was that legacy has not been maintained for years. Ubuntu had to modify its version to support booting ext4 partitions. Now with so many new hardware & software changes a new boot loader was required, but it is a large change. I did not like grub2 originally as it was so different & then there was not much documentation. But now that we understand it and they have made many improvements grub2 is better than grub legacy.

---

### Post by cobras on 2013-04-13
As I last posted, I was able to boot up thanks to oldfred's suggestions, but there were still unsolved issues.  There were warnings I couldn't read during boot up (scrolled too fast), and the login screen didn't render properly (it was fragmented).

I decided to upgrade to 12.04 while I still could, hoping the upgrade would fix whatever was broken.

As of today, I'm running 12.04 with no apparent problems, so I'm going to say my problem has been solved, though it would have been great to learn what caused the problem to begin with.

Thank you so much for your help.

cobras

As I last posted, my original problem was never really solved.  I simply worked around it by installing 12.04 alongside Windws Vista, and all seemed well.  I could run Ubuntu or Vista at will with no problems whatsoever - until yesterday when my system totally crashed.

It wouldn't boot even after going to the library and trying several ubuntu disk versions.  Yes, I made sure the cd player was first in the boot order.

After many tries, the machine finally booted, so I reinstalled GRUB (sudo grub-install /dev/sda1), hoping anything boken would get patched up in the process.  At this point my machine is at least booting up, but it won't run Vista even though it's still listed on the menu.  'sudo fdisk -l' returns

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x988b55cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    83148532    41573242+   7  HPFS/NTFS/exFAT
/dev/sda2        83152440   312576704   114712132+   5  Extended
/dev/sda5        83152503   303162614   110005056   83  Linux
/dev/sda6       303162678   312576704     4707013+  82  Linux swap / Solaris
```

Any suggestions?

---

### Post by ahallubuntu on 2013-06-04
Check the hard drive S.M.A.R.T. health. Install GSmartControl and look at the Attributes tab. Any Attributes highlighted in red or pink? Those are the ones you should be most worried about. If none are highlighted, the drive is probably not failing.

---

### Post by cobras on 2013-06-04
I did as you suggested ahallubuntu.  The drive passed its basic health check and none of its attributes are highlighted.

At this point, I've had so many problems I'm starting to think the machine is infected.  Any suggestions on programs that'll root out any bugs, viruses, etc.?

---

### Post by ahallubuntu on 2013-06-04
Yes, it could well be infected. Or the Windows filesystem could have become corrupted. Or an update could have failed or something. Lots of things could cause a Windows installation to fail. The first thing I'd do (after checking the hard drive's S.M.A.R.T., which you've done) is to boot a Windows disc and run chkdsk /f on your Windows partition. Next see if you can boot Vista AT ALL even in Safe Mode. There are a bunch of free scanning tools like Malwarebytes you can run to look for infections.

Here's a question: why do you still need Vista at all? Games? Special software? Consider what you really need Windows for at this point. If you use Windows only for a few things (like say tax software) you could install Windows in a Virtual Machine (e.g. Virtualbox) in Ubuntu and just start that up when you need to do anything Windows-related. That's what I do. I have Windows 7 as a dual-boot on my hard drive with Ubuntu but I haven't booted to it in months. I use the Virtual Machine instead for occasional Windows stuff - it opens like another window in Ubuntu, and when I'm done, just exit Virtualbox and save the state.

---

### Post by cobras on 2013-06-05
> **ahallubuntu said:**
> 

Here's a question: why do you still need Vista at all?

I'll try to keep it short.

The hard drive currently on my machine is there because I was having so many problems (Apparantly unresolvable - at one point the person trying to help me with a bug report literally ran out of ideas.) with Ubuntu on the previous drive, that I replaced it.  The replacement drive came with Vista installed.

I want Ubuntu to work, so I keep on trying.  I kept Vista hoping that if Ubuntu failed again I could revert to the more reliable, stable OS.  What I didn't realize was that the dual-boot solution somehow makes Vista dependent on Ubuntu.  At this point, if I could restore my hard drive to its original state, I would do so in a heartbeat.

Back to the immediate issue.  I may have stumbled onto a clue, but I need help deciphering it.

Recall that '**sudo fdisk -l**' returns

[B]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x988b55cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    83148532    41573242+   7  HPFS/NTFS/exFAT
/dev/sda2        83152440   312576704   114712132+   5  Extended
/dev/sda5        83152503   303162614   110005056   83  Linux
/dev/sda6       303162678   312576704     4707013+  82  Linux swap / Solaris[/B]

I tried '**sudo fsck /dev/sda1**' and got the following:

[B]fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>[/B]

My understanding is way too limited to know what my next step should be.

---

### Post by ahallubuntu on 2013-06-05
> **cobras said:**
> I tried '**sudo fsck /dev/sda1**' and got the following:

You can't run fsck on a Windows NTFS partition. fsck is for Linux partitions.

As I said, get a Windows CD and boot it so you can run Windows chkdsk /f on the Vista partition.

---

### Post by fantab on 2013-06-06
> **cobras said:**
> ...so I reinstalled GRUB (sudo grub-install /dev/sda1), hoping anything boken would get patched up in the process.  At this point my machine is at least booting up, but it won't run Vista even though it's still listed on the menu.

Grub must be installed to /dev/sda the Drive, and not on partition /dev/sda1.

You can fix Vista MBR with: [http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/)

If the rest of the Vista install is good then after fixing MBR Vista should boot. If that doesn't help then you will have to re-install Vista.
After this (either MBR fix or reinstall) Ubuntu will not boot.
To boot Ubuntu again you must reinstall GRUB. You can do this with [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair") utility.

---

### Post by Mark Phelps on 2013-06-06
If you don't have a Vista installation DVD, then you can obtain (purchase) a Win7 repair CD image from the following link (actually works better at repairing Vista than the original Vista disk): [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by oldfred on 2013-06-06
NTFS does keep one backup of the NTFS partition boot sector. If you installed grub to the NTFS partition boot sector you overwrote essential Windows boot info and must restore it. You usually can use testdisk if do not have a Windows repairCD, But do need Windows repair tools to run chkdisk or make the repairs if backup is also bad.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

