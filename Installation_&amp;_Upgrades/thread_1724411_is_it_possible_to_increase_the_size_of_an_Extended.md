---
title: "is it possible to increase the size of an Extended Partition"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by nu_buntu on 2011-04-08
hi,
I have Ubuntu 10.10 installed on my 80gb hdd, disk has following partitions :

1. /dev/sda1 = /boot            (500mb)
2. /dev/sda2 = /                  (20000mb)
3. /dev/sda3 = linux-swap    (2000mb)
4. /dev/sda4 = extended      (7000mb)
5. /dev/sda5 = /home          (7000mb)
[COLOR=Red]**6. unallocated =                   (40000mb) **[/COLOR]

**how [COLOR=Red]can i use this[/COLOR]** **[COLOR=Red]unallocated space[/COLOR] to create an NTFS partition. **

please HELP.

---

### Post by Dutch70 on 2011-04-08
Looks like you really need some reconstruction on your hdd anyway. Can you post a pic from gparted so we can get look at it? 

Please use the paper clip in the toolbar of your next post to attach the pic.

Why would you have 20000mb for /, and 7000mb for /home? That doesn't make a lot of sense to me. 
Actually, 7000mb for / and 20000 for /home would make more sense, but I wouldn't advise that either.

---

### Post by oldfred on 2011-04-08
Since you do not have windows, why the NTFS partition? If planning on installing windows, it has to be a primary NTFS partition with the boot flag. Windows will read a logical NTFS, but not boot from it.

---

### Post by nu_buntu on 2011-04-08
thanks [Dutch70]("http://ubuntuforums.org/member.php?u=595401"). here's the screenshot you requested.

---

### Post by Quackers on 2011-04-08
You didn't answer oldfred's question. Why the NTFS partition? If you want to install a Windows system you will need some partition changing (as in deleting) as you already have 4 primary partitions - which is the maximum on an mbr partitioned disc.

---

### Post by nu_buntu on 2011-04-08
since linux is new to me and my previous Ubuntu experience (which was  quite confusing), I am planning to have an NTFS partition so that if at  all i mess up with Ubuntu, I can still have my data back by windows  (NTFS) partition because I am used it.

---

### Post by Dutch70 on 2011-04-08
As oldfred said...If you don't have windows installed, there is no need for an NTFS partition. You can back it up to an ext4 partition. 

I personally think you need to back up your data now, and reconfigure your partitioning scheme. As Quackers said, you only get 4 primary partitions. You're using 1 for /boot, which you don't need, and 1 for Swap, which can be in an extended partition. 

"/" aka "root" should be around 15-20GB. *in a primary partition*
Swap should be equal to your physical RAM, plus a little for good measure if you want.
and the rest of your disk for /home, which serves as your back also. If Ubuntu breaks, it wouldn't bother /home any more than it would an NTFS partition. */home & swap in an extended logical partition.*

Note: you could reinstall Ubuntu right now and wouldn't lose anything in /home, as long as you don't format it.

Not a very good pic, but this is what you want your disk to look like. That is "/" - /home - Swap.

---

### Post by oldfred on 2011-04-08
I have to agree with Dutch70.

But if you really want an NTFS partition you just have to expand your extended partition into all of the unallocated and create a new partition(s) there.

Understand that any backup of Linux data into NTFS loses its permissions & ownership, so when you copy it back you have to reset it. Do not copy any system files as settings are a lot different. You also have to have a windows repair CD so you can run chkdsk regularly. Ubuntu runs fsck every 40 (or something) reboots. You should run chkdsk just as often, even if it does not seem to need it.

---

### Post by srs5694 on 2011-04-08
NTFS on a Linux-only system is a Bad Idea, for several reasons:


[list]
[*]To elaborate on a point oldfred made, Linux has only very minimal NTFS maintenance tools. This means that when (note *when*, not *if*) you have a system crash, power failure, or other problem that affects the filesystem, Linux will be unable to check it. When this happens, Linux will also probably refuse to mount the filesystem, which means you'll need to jump through extra hoops to get Windows to check the disk (use an emergency Windows disc or physically move the disk to another computer, probably).
[*]There may be reliability disadvantages to NTFS under Linux. The NTFS-3g drivers that Ubuntu uses seem to work well for most people, but NTFS is a proprietary Microsoft filesystem, vs. the open-specification filesystems that are Linux-native. It's hard to quantify the reliability of one filesystem vs. another, but I'd be quite surprised if NTFS was more reliable than the more popular Linux filesystems *under Linux*. (Under Windows, of course, things are likely to be the other way around.)
[*]Performance is likely to suffer compared to using a Linux-native filesystem.
[*]As others have said, NTFS doesn't store Linux-style ownership and permissions information. This may not seem like a big deal if you're the only user, but it could become an issue if you need to store executable files on the partition or do various other things with it.
[/list]


If I were you, I'd just expand the logical partition and /dev/sda5 to a comfortable size. Dutch70's suggestions are fine, but I disagree with the emphasis on the Linux root (/) filesystem being primary and /home and swap being in logical partitions. Use whichever partition types (primary vs. logical) are convenient; Linux can use either. I do recommend using as many logical partitions as possible, though; that maximizes flexibility in case you want to add OSes that require primary partitions in the future, since the primaries won't all be tied up unnecessarily.

For that matter, on a Linux-only system, ditching the Master Boot Record (MBR) partitioning system with its awkward primary/extended/logical distinction in favor of the GUID Partition Table (GPT) system makes sense. Linux can boot just fine on a GPT disk, and GPT has several minor advantages over MBR, the most important for the moment being that there's no distinction between primary, extended, and logical partitions; you can have up to 128 partitions by default (and more if you need them), and they all act much like MBR primary partitions (although that's an MBR concept that's technically meaningless in GPT). OTOH, if you think you might want to add Windows in the future, sticking with MBR is probably best, since Windows can't boot from a GPT disk on a BIOS-based computer. See my online [GPT fdisk documentation](http://www.rodsbooks.com/gdisk/) for more information on GPT.

---

### Post by srs5694 on 2011-04-08
Oh, I forgot: To modify your existing partitions, you'll need to boot from an Ubuntu live CD or other Linux emergency disc. As it is, you can't expand the existing partitions because GParted won't work on partitions that are in use. They won't be in use if you boot from a separate CD-based system (although you may need to disable the swap space; some emergency discs, including the Ubuntu installer in live CD mode, enable any swap partitions they find).

---

### Post by oldfred on 2011-04-09
Based somewhat on srs5694's sales pitches for gpt partitioning and a desire to know a little about what will be the future, I have converted one of my 160GB drives to gpt and used gpt for my 16GB flash drive install. No real issues. With 10.04 I had to add some settings to boot from a gpt disk then use grub to also see the MBR drives.

All new drives or reformats of a drive will be gpt as I only have XP one one older drive and as I have said for about 2 years, will soon not be using XP anymore. :) So no more MBR required.

---

### Post by Dutch70 on 2011-04-09
> **srs5694 said:**
> Dutch70's suggestions are fine, but I disagree with the emphasis on the Linux root (/) filesystem being primary and /home and swap being in logical partitions. Use whichever partition types (primary vs. logical) are convenient

Yes, That was merely a suggestion. I should have made that more clear.

---

