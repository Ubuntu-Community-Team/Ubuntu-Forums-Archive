---
title: "Win XP on one HDD, Ubuntu on second HDD, Files Stored on a third HDD"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by Tsui Pen on 2010-11-14
Hi,

I am new to Linux and and have a basic understanding of computers. I tried searching for an answer in different threads, but none seemed to apply to me. I apologize in advance if I overlooked a thread. There are 4 interrelated questions I have.

1. I have three HDDs. HDD 1 is running Windows XP, and HDD 2 is just used as storage. I just bought my third HDD and plan on using it for storage. I want to start fresh and I will be formatting HDD 1 and 2, and only use HDD 3 as storage. My first question is: Do I install Ubuntu or Win XP first? Does it matter? If so, what implications does this have if I later need to format one of the HDDs?

2. I want to install Win XP on one HDD and Ubuntu on another. I saw a tutorial here, but it apparently did not apply to GRUB2, which is what the latest version of Ubuntu uses. I have looked on the internet, but none start from a fresh formatted drive, which, in my mind, seems like the simplest way of doing this entire process. Does anyone know of a really good tutorial for installing the latest Ubuntu on one HDD and Win XP on another?

3. I've read that some people don't get the dual-boot startup screen and some fudging around is needed. This is completely unknown territory for me, but I am willing to learn how to do it. I see many ways of doing it but I'm not sure which one to choose based on my situation. Can anyone recommend specific steps to follow, given that I will have two formatted HDDs? (If this even matters.)

4. Will both HDDs be able to read HDD 3 (used for storage)?

My motherboard is an nForce 750i SLI. I believe it has 4 SATA connectors, of which 2 are in use. And I just bought my third HDD which I plan on connecting using SATA.

Please let me know if you need more information on my PC specs.

I really appreciate all the help, even if they are just links.


Steven

---

### Post by oldfred on 2010-11-14
While this is Lucid it goes over some of the issues.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

the main issue is to make sure when you install Ubuntu you install its boot loader to the same drive. With Maverick now they seem to have made it that the new combo box on where to install grub2 is only available if you use manual install, so you have to partition in advance.
Others suggest unplugging other drives. Windows always prefers to be the first drive, Ubuntu will use UUIDs so even if installed to hd0, it will still boot on hd1 by using a search by UUID.

Windows will not read ext partitions, so any data you want to share should be on a NTFS partition. You may still want to have a separate /home and/or /data for Linux only stuff.

How large are the drives.

With multiple drives you should know about this handy script. I run it before & after every install to make sure everything is where it is supposed to be and it documents partition sizes & locations in case you ever need  that data. Until you have the new install it may not tell very much.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Tsui Pen on 2010-11-14
Thanks for the reply, oldfred.

I plan to have Win XP on the 465GB drive, Ubuntu on the 111 GB one, and the main storage drive is 1TB.

The drives are pretty massive because I do audio recording and, to a smaller degree, some film editing.

I'll have a look at the links and information you've provided closely and will report back.

Thanks, again!

---

### Post by oldfred on 2010-11-14
My standard suggestion for Ubuntu is

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

But, I like to have several 25GB roots if hard drive is large enough, so I can install the next version without deleteing the old. I actually have 3 in rotation, old, current & beta. I in effect have either XP or Ubuntu on my three drives, plus a full install on a 16GB flash and several ISOs loopmounted on a 4GB flash I use for new installs and repair ISOs.

Some like to have an operating system on every hard drive, so they do not have to use liveCD or other way to boot.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

---

