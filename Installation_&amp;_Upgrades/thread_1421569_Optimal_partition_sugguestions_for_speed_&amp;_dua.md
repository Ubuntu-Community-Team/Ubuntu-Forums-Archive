---
title: "Optimal partition sugguestions for speed &amp; dual boot with shared data"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by BastardNamban on 2010-03-04
I am installing a custom 8.04 live disk (basically, a mirror of my whole system with user data intact, sans all non-OS files) from a USB key with remastersys for the .iso creation, and UNetbootin for the bootable USB on a brand new 120GB PATA WD HDD. Both do nicely so far, so I have a working livedisk to use until I need to install Ubuntu to the drive.

I had a pure linux box, but I need to add XP with dual booting now- I have to use Autodesk Inventor 2010 software for my college class on my laptop, so I don't drive 30 miles to use the 1 computer lab equipped with that software. 

I'm not new to Linux, but I am new to more in-depth partitioning. I've taken the lead and looked into things- read this good guide, among others:[HTML]http://www.psychocats.net/ubuntu/partitioning[/HTML], and noticed that there is a way to more deftly use partitions so that personal files can be shared access and write between Windows and Linux partitions- with this:[HTML]http://www.fs-driver.org/[/HTML]

Ubuntu is still my main OS, but being able to access all my media/data files between the 2 systems would be nice. Problem is, until now, I've put everything on a single partition because I didn't know better. Now I do, but am a bit confused with all the guides as to what's most efficient, especially in my case where full RAM speed is crucial to running a single program.

Here's what I know I need to do:

1. The Windows XP install I know needs from 20-30GB for Inventor 2010 LT to work well. I don't need anything else in XP spacewise- it's just being added for Inventor.

2. I'd like to create a separate /home partition for Ubuntu this time to save my user data, making future upgrades much more painless (I will be getting Lucid soon). How that works when upgrading, though, I don't know yet..

3. I'd like both OSes to share all my personal files (docs, pics, music, Inventor design files) if it is an efficient choice that works without problems.

4. Finally, because 2GB is minimum for Inventor to run decently, I need to maximize the speed of my RAM for it- from my reading, these so-called "swap" partitions can somehow be added for buffering this- people seem to sugguest the swap be half the size of the RAM for fastest speed, and some say add separate /usr or other partitions. I'm not clear on what would be most efficient for me.

I have limited HDD space- because of my laptop's BIOS, this single 120GB drive is the biggest I can get on my laptop, so efficient partitioning would make a huge difference for me. Before this, a 60GB HDD was in this. I'd like to see some added space for my data storage, but still keep things as fast as possible for Inventor when I use it, and Ubuntu.

Can anyone offer some partition sugguestions? :o

---

### Post by oldfred on 2010-03-04
Disk partitioning will not make any noticeable difference in system performance. More RAM is the cheapest way to speed up a system. You do not want to use swap as it is way slower than RAM, but it is good to have some swap incase you are running lots of memory intensive applications. Swap will not help windows, it is for linux only.

I had dual boot XP & Ubuntu for 3 years with just a 20GB shared partition for photos, firefox & thunderbird profiles, and misc data. When I did a clean install of Karmic I created a separate ext3 data partition and separate /home but now without any of my data /home is about 1GB. My root with many applications is only about 5GB. So if you are putting most of your data in NTFS shared partition, you can have 10-20GB for root, 2GB for swap and your choice if you want a separate /home or not. I would not let windows read EXT3 partitions and even though Ubuntu will read & write the windows partition, I only read from the operating system partition. Some windows (only) users recommend a separate data partition so when windows has issues they can still access their data.

Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by BastardNamban on 2010-03-04
Thanks for the links. I'm more of a hands on learner, so I wish I had someone here versed in linux more than I to show me/ask questions- I could have been done in 20 minutes. But I don't.

I read all the links you sent me, and a bunch more:
[HTML]http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition
http://ubuntuforums.org/showthread.php?t=1397508
http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting
http://www.linux.com/archive/articles/114157

http://gparted.sourceforge.net/larry/generalities/gparted.htm

http://www.arsgeek.com/2006/11/01/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable-with-ntfs-3g/

http://lifehacker.com/software/rsync/geek-to-live--mirror-files-across-systems-with-rsync-196122.php[/HTML]

After absorbing all of those as best I can, some questions:

1.Is the best option to make the shared partition for reading and writing an NTFS partition? If so, will my Ubuntu install be able to do so natively as I am led to believe? What would the performance difference be for this over keeping all my data in an Ext3 partition, possibly unshared just for Ubuntu?

2. Does it matter what order the OSes are installed in? XP takes a while. I was going to install Ubuntu first after partitioning. Does the actual order matter in any way, as long as at least one NTFS partition exists solely for XP?

3. Should I treat XP like linux, in that I don't install Inventor or other software in XP on the same NTFS partition as the OS? IE: should I make one NTFS partition for just the XP OS, and another to put Inventor in? If the second choice, should that second partition be a shared NTFS partition for all my pics, music, etc. and any windows programs, or should those be separate?

Here's what I'm thinking of doing before you answer any of the above, after reading through all those links above and the ones you gave (I will of course wait until I hear from you once more on those before doing anything, since I have class shortly after this today):

Of the 111.76 GB Gparted is showing I have from my livedisk usb, making:

1 primary partition, about 25GB NTFS, for everything XP OS & programs;
1 primary partition, about 7GB Ext3, for /, Ubuntu's OS only;
1 swap partition, 2GB Ext3, just in case of Inventor maxing out my 2GB of RAM, basically as a failsafe,
1 primary partition for the rest, about 77GB Ext3, for /home, where I will keep all my data, unreadable to XP, but available to Ubuntu, making future upgrades simpler.

Thoughts? I'll check back around 8:30- got to drive 30 miles to class. This is why I am so meticulous about doing this as efficiently as possible- I don't want to drive that anymore just to get work done, but I don't want to sacrifice the usability of my computer- ideally, stuff like music and pics would be at least available to read in XP- I don't know that I'd need to change them in XP, so write I may not need.

EDIT: I'm thinking I don't need a swap partition to cover for Inventor- because XP wouldn't recognize an Ext3 swap, and that's the only type there seems to be. Is there a way to make a swap compatible with XP, because even with my GeForceGo 6800 card and the 2 GB of RAM in my Inspiron 9300, I think I might still bog down my computer at some point. Ideas? I've maxed out the memory on this laptop, so more memory is a no-go, but I plan on using this as my only computer for a few more years.

---

### Post by oldfred on 2010-03-04
NTFS is just about the only choice for sharing with windows. FAT is obsolete (no journaling and 4GB max file size) and should only be used on USB card where the device requires it. All the newer installs of Ubuntu include the NTFS drivers. The advantage of EXT3 or 4 is that it is linux native. It supports the full file permissions and ownership. 

Some say you must install windows first. It does not really matter as you can reinstall grub in just a minute or two once you know how. Windows overwrites the MBR when it is installed and that is the only advantage of Ubuntu second as then grub is last and will find & allow the booting of windows. 

I do not know inventor, but most windows apps have to be in the programs directory. I either make apps save data to the shared partition or have a .bat files to copy the data the the share partition.

Size of shared vs. /home depends on how you save data. Does inventor create lots of large files? I might make sure the shared and /home are adjacent partitions so if in the future you wanted to shift some space it would be a little easier. I might go 10GB for root.

Windows has to be a primary partition. The others do not matter but if resizing in the future it is more difficult to move if one is inside the extended and the other is not.

---

