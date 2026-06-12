---
title: "Installing on custom built PC with SSD + normal HD"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by My_web on 2010-11-12
Hi everyone,

I've ordered parts for a new build which should get here tomorrow. I know how to set everything up but I just had a question about partitioning as I'm going to be using an SSD drive and a normal 7,200 HD for data.

I would also like to be able to dual boot Windows 7. I think I've sussed everything out but if anyone has any experience with this sort of setup please let me know if the following partitions would work:

On the 64GB SSD:
- root partition for Ubuntu 32GB
- Windows 7 partition 32GB

On 500GB hard drive:
- /home partition
- /linux-swap
- Data partition for windows

Does this setup make sense? Am I missing anything? Thanks in advance.

---

### Post by Herman on 2010-11-12
I have a custom built PC too and mine has a 64 GB SSD and a 1 GB hard drive for data. 
I only have Ubuntu installed in this computer. 
My SSD contains Ubuntu in one single partition, including a swap file instead of a separate swap area. The way I use it is to keep the files I'm currently working on in the SSD. 
My way of thinking is when I want to make my computer work hard, for example rendering a video in kdenlive or opening a map with a large raster image or something like that, I want all of the reading and writing to occur within my SSD drive. 
Then later, when the work is complete and whenever my SSD drive starts to get a little bit full, I move all my larger files to the hard disk for storage. 

Hard disk drives rely on the use of voice actuator coils to make little  arms holding the read-write heads pivot around a pole to sweep to and  fro across the hard disk platter looking for sectors containing the   requested data to read, or some empty sectors to write to. The time it  takes for the electro-mechanical device to find the sectors it's looking  for is called 'seek time'.

Since Gnu/Linux operating systems were first made, and long before SSDs were ever dreamed of, Gnu/Linux operating systems have had the ability to be installed in multiple partitions and Ubuntu is no exception. There is no requirement for those partitions to be in the same hard disk drive, (or SSD etc). When an operating system is spread out over more than one hard disk drive, it's possible to gain a performance boost by spreading the workload over two or more hard disks. The operating system can be using the read-write heads of the two or more hard disks simultaneously for seeking and reading or writing data. Some kinds of RAID setups can be even faster, but I'm only talking about a multiple partition installation on more than one hard disk right now.

Introducing an SSD into the equation raises some interesting questions.
The seek time for an SSD is virtually nil, and the reads are much faster and even the writing to an SSD is usually a little faster than writing to a hard disk drive. I wonder if having half of your operating system in an SSD and half in your hard disk will speed up performance or slow your system down. I suspect the latter. There's another school of thought that goes something like this, "A chain is as strong as it's weakest link and a computer will run as fast as it's slowest component."
If you want to be able to make use of the faster performance of your SSD drive, which you have paid a premium price for, it makes more sense to me to have the entire operating system inside the SSD, unless of course you have more than one SSD.

Personally, I would install Ubuntu in the SSD and if I really was forced to use Windows7 for some reason, I'd install it in the HDD, since Windows is a notoriously slow operating system anyway and it seems like a waste of good SSD space. I'm forced to use Windows XP at work but I'm spared the pain of having to put up with Vista or 7, we're not even allowed to use those. (LOL).

These are only my personal thoughts and opinions, and you may want to run some experiments yourself to try to either confirm my opinions or else prove me wrong. :)

---

### Post by My_web on 2010-11-12
Thanks for the thorough reply Herman. What you suggest does make sense, especially as I spend 99% of my time in Ubuntu anyway (I sometimes switch back to Windows for games).

It definitely makes sense to use the SSD to the max, but I keep reading that excessive read/write operations wear the drive down. After some more research it would seem that my SSD's MTBR is 1,000,000 hours or 114 years ([product page here](http://www.corsair.com/products/ssd_nova/default.aspx)). So I guess the extra read/writes would make absolutely no difference seeing as I would probably be changing it again in a few years anyway.

If I have understood the SSD's lifespan correctly then I probably will store everything for Ubuntu on the SSD and have Windows on the other drive with a shared NTFS partition for videos, music and general storage.

So I think I will lay it out like this now:
SSD:
/ partition
/home partition
/linux-swap (you mentioned a swap file? is this instead of a swap partition?)

Other HD: 
80GB for Windows
The rest for storage (for both OSes)


Thanks for your advice, it's helped a lot.

---

### Post by Herman on 2010-11-12
> I keep reading that excessive read/write operations wear the drive  down. After some more research it would seem that my SSD's MTBR is  1,000,000 hours or 114 years ([product page here]("http://www.corsair.com/products/ssd_nova/default.aspx")).  So I guess the extra read/writes would make absolutely no difference  seeing as I would probably be changing it again in a few years anyway.:) Well, the internet is full of people who keep repeating the same things over and over again without applying very much logic or research or experiments of their own to check and make sure what they keep repeating is still up to date or was ever even factual at all in the first place. "Internet parrots". 
There may be a few people who really have had bad experiences with USB flash memory sticks, and I think the quality of flash memory products does vary between manufacturers and even models of the same brand much more than people have come to expect based on their experiences with hard disk drives.

You have a good brand of SSD, you shouldn't need to worry about flash memory wear any more than you would worry about wearing out a hard disk.
Hard disk drives wear out too, they develop 'bad sectors', and in addition to that they also generate more heat, (from the motor and bearing), and are more subject to all kinds of mechanical failures. 
I'm pretty sure that most good quality SSDs for sale today will last at least as long as a comparable HDD, and probably much longer.

My EeePC has only a 4GB SSD in it and it has already lasted long enough for me to have had my money's worth out of it, and it still going strong after a couple of years of abnormal use. Here's a thread about it, [[ubuntu] Installing Ubuntu on a USB stick ? - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=805596")  It's only 4GB, so there are not a lot of spare empty sectors for the SSD controller's wear leveling algorythms to work with. In a normal sized SSD like we're talking about now, the expected life time would be exponentially greater.

As always, we still need to keep making backups regardless of whether we use an SSD or HDD.

SSD's are expensive per GB, and very large HDDs are now being made for reasonable prices, so it makes sense to use a large HDD for storage and an SSD for the operating system and files currently being worked on.

I have always been a person who prefers the simplicity of having Ubuntu in one partition, and I even like to have a swap file instead of a swap partition, (  [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile") ). In this case one of the reasons I installed with only one partition was also to reduce boot time, Ubuntu can [boot in as little as 3.03 seconds]("http://members.iinet.net/%7Eherman546/p1/ocz-lynx-lucid-20100430-18.png") in my SSD.  :)

---

### Post by Herman on 2010-11-12
The other thing about having an integrated single partition installation is I can make a backup of the entire operating system with one single dd command to a file in the HDD and restore it again with the opposite dd command.
Many other Ubuntu users prefer to use 'Clonzilla' or 'Partimage' for that kind of work instead of the dd command and that's safer for most people as it removes most of the chances for human errors to occur which can destroy data.

If you like having a separate /home and swap that's fine, it's a popular way to install Ubuntu and there's nothing wrong with it.

---

### Post by My_web on 2010-11-12
I like the idea of one partition, it does sound easier to manage. The thing is because I have limited space on the SSD taking up 8GB (2*amount of RAM) of it for the swap seems a bit excessive. I read elsewhere that Swap is only used for hibernation and therefor not necessary (my PC is either on or off, I never use hibernate)? Also I've never noticed my swap being used during normal usage (free -m).

3.03 seconds is amazing, my current pc feels quick enough but I don't think it's anywhere near that speed. I will probably try out a similar setup to yours with everything on one partition to see how it goes. Thanks again for your advice, I'll try and post here with what I ended up choosing.

---

### Post by Herman on 2010-11-13
I don't use hibernation myself, but I do like to follow the first half of the how-to and make a swap file.
I agree with you that an 8 GB swap area or swap file would be quite excessive and probably wasteful.
It seems to me from my own experiments that having at least a small swap area or swap file improves performance, even if I have plenty of RAM and I don't think my system needs it. Even just a 256 MB swap area would be good.  I have 2GB of RAM in this computer and I made a 2 1/2 GB swap area. I always set swappiness to 10 though, when installing in flash memory, so that the operating system will prefer to use the RAM modules instead because I think that my operating systems work fastest that way. 

[Swap FAQ]("https://help.ubuntu.com/community/SwapFaq") - Ubuntu Community Docs]
       
       [Linux Performance tuning - vm.swappiness]("http://unixfoo.blogspot.com/2007/11/linux-performance-tuning.html") - unixfoo.blogspot.com
       
       [What Is the Linux Kernel Parameter vm.swappiness?]("http://www.linuxvox.com/2009/10/what-is-the-linux-kernel-parameter-vm-swappiness/") - Linux Open Source Blog

---

