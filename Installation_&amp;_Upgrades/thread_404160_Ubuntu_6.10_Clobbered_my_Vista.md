---
title: "Ubuntu 6.10 Clobbered my Vista"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by guerrebear on 2007-04-08
I was curious about Ubuntu and decided to download 6.10 and load it onto my Vista laptop (a new sony vaio).  It looked like it was going OK, and it gave me the option of resizing my existing partition and making a dual-boot configuration, which I did, leaving about 15GB for Ubuntu.  This chugged for a while and ultimately produced a working bootable Ubuntu which I have briefly tested.

I then tried to reboot and the boot loader didn't offer a Vista option.  After reading forums I found that one should edit the menu.lst file for grub to put vista as the first option.   I did so and indeed this gave me an option to boot vista, but when I select this it sends me to the Sony emergency recovery program which basically gives me the option to wipe the machine and lose weeks of time that I spent fiddling with and patching vista to get it to be stable.

Reading some more, it seems that the Ubuntu community was well aware of this problem and chose to neither do anything about it nor offer warnings on the Ubuntu download page.  One post gave the advice of loading the latest GParted onto a CD (since the Ubuntu 6.10 download, I notice belatedly, is six months old and presumably doesn't have a vista-compatible GParted).  Booting this GParted "live" CD was supposed to fix things but it doesn't; it merely shows the /dev/sda2 partition as being 161.74 GiB of "unknown" data (i.e. not a NTFS file system anymore since the Ubuntu installer apparently destroyed it).  Since it's unknown, this tool won't touch it.

So I'm left with no way to repair my Vista partiton short of wiping the hard drive, reloading vista, loading days worth of patches, then restoring my most recent backup.  Thanks a lot, Ubuntu team.  Quite a remarkable show of professionalism.  "It just works", indeed.

---

### Post by bitphire on 2007-04-08
I am still a n00b to linux but thought these might help if you haven't seen:

Think this is the best bet:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)


this one you might have to adapt since it's installing window's after Ubuntu is installed:
[http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot](http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot)


There has to be a way to save it. :( I have vista but can't get Ubuntu to install on my PC yet so haven't had the chance to try this but I will.

---

### Post by heimo on 2007-04-08
Every time partitions are resized, there's a risk of losing data (regardless of what operating system you'll be installing). About warnings: Yes, there should definitely be a warning about risk of losing data before accepting changes to partition tables. Wasn't there?

Sorry to hear your "experience" with installing Ubuntu was so terrible. Hopefully you can find alternative, non-destructive way to rescue your Windows installation. Best of luck.

---

### Post by guerrebear on 2007-04-08
For what it's worth, here is a printout from fdisk -lu:


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    13367295     6682624   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    13382145   352578554   169598205    7  HPFS/NTFS
/dev/sda3       352578555   389094299    18257872+  83  Linux
/dev/sda4       389094300   390716864      811282+   5  Extended
/dev/sda5       389094363   390716864      811251   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    7  HPFS/NTFS

---

### Post by guerrebear on 2007-04-08
Forgot to mention that when I set grub to root hd0,1, I get Grub Error 13: Invalid or unsupported executable format.  

I presume that when the installer ran the old version of GParted it had never been tested on Vista, and when I resized the partition it basically clobbered it so badly that it's not even recognized as an NTFS partition by most software.

---

### Post by silver on 2007-04-08
> **guerrebear said:**
> 

<snip>

So I'm left with no way to repair my Vista partiton short of wiping the hard drive, reloading vista, loading days worth of patches, then restoring my most recent backup.  Thanks a lot, Ubuntu team.  Quite a remarkable show of professionalism.  "It just works", indeed.

#1 - Boot to the Vista DVD and run a repair of the OS.

#2 - Vista has a very unique and fickle boot loader. 

#3 - Sony's proprietary disk image is at least partially responsible for your difficulties.

#4 - Backup, backup, backup. Hard drives are at an all time low. I don't pity anyone that simply doesn't have a backup.

#5 - If you have data to recover then simply install in the partition where Ubuntu was previouly located.

---

### Post by dsterry on 2007-04-08
I have edgy and vista on an hp laptop. I used the Disk Management tool in Vista to do the resize and that worked fine. Since it's in there and native that's what I'd recommend doing for all future vista-linux dual booters.

---

### Post by wj32 on 2007-04-08
Use testdisk:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

And, do you call Windows professional? It actively IGNORES any other non-ms operating system and replaces your boot loader. Doesn't come with a decent partitioner and just shows GNU/Linux partitions as "Unknown".

---

### Post by silver on 2007-04-08
I've used Testdisk myself on occasion however I wouldn't get my hopes up about it recovering the Vista bootloader. Microsoft finally got a clue after thousands of people had boot loader troubles and rewrote the bootloader from the ground up. He could install XP into the Ubuntu partition and then install the Vista BootPro utility from [http://www.vistabootpro.org/](http://www.vistabootpro.org/). Might work.

---

### Post by confused57 on 2007-04-08
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=398122](http://ubuntuforums.org/showthread.php?t=398122)

Added:  I started a new thread with a suggestion for a warning to Vista users planning on setting up a dual boot with Vista:
[http://ubuntuforums.org/showthread.php?t=404200](http://ubuntuforums.org/showthread.php?t=404200)
Sounds like a good idea to me, but have only received one reply at this time.

---

### Post by guerrebear on 2007-04-08
> **confused57 said:**
> Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=398122](http://ubuntuforums.org/showthread.php?t=398122)

Added:  I started a new thread with a suggestion for a warning to Vista users planning on setting up a dual boot with Vista:
[http://ubuntuforums.org/showthread.php?t=404200](http://ubuntuforums.org/showthread.php?t=404200)
Sounds like a good idea to me, but have only received one reply at this time.

OK, thanks to everyone with suggestions but none of them worked.  I've also downloaded a couple of purported NTFS partition repair tools and none of them recognize what's left of my Vista partition now that the Ubuntu install disk has finished destroying it.  Sony laptops don't ship with a Vista disk so I can't attempt to repair the partition, but I have an old Vista beta disk which did not recognize the partition as being valid NTFS, so it probably wouldn't have mattered.

The problem is not in the boot process -- grub seems to be doing the right things, it's just that the Vista partition is toast, thanks to the fact that the Ubuntu team hasn't updated their gparted partition tool in six months or more.  The current Ubuntu ISO availabe for download on this website is totally lethal to pre-existing installs of Vista if you re-size the partition.   An no, there wasn't any warning.  I foolishly assumed that with all the hype about Ubuntu, it was a serious, stable, and mature prouct.  My mistake.

---

### Post by DizzyTech on 2007-04-08
Do not be a fool.  If you read anything about Ubuntu, you'll know it has a six-month release cycle.  The new edition arrives in about a week.

Don't act so put upon.  Nobody should go blindly into a Linux install without a backup.

If you want to call us 'unprofessional,' go ahead.  Go scurry back to the company and their software that makes every attempt to ignore competitors.  That's professional.

As well, community is the greatest tool.  If you had any doubts, ask a question on the forums before the install, not after it decimated your system because your lack of knowledge.

---

### Post by finferflu on 2007-04-08
Maybe you haven't noticed, but there is a warning before partitioning. I've installed Ubuntu a lot of times, and I can remember the warning is there (it's almost in every distro I have tried)...

---

### Post by DizzyTech on 2007-04-08
There are also about six "Are you sure?" dialogs.  They actually mean something, unlike in Windows.

---

### Post by Tatty on 2007-04-08
Im certainly no expert, but the problem here seems to be Vista, not Ubuntu.

---

