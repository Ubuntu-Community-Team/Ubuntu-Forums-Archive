---
title: "Dual Boot Setup"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by LimaBeans on 2010-11-19
Hello guys,
 
So I've tried the liveCD and I love it! :D Right now I want to install Ubuntu, however I still want to keep Windows XP on my computer. I've been reading many articles, but I want to know the best way to dual boot. 
 
I going to be installing Ubuntu on an ancient compuetr to see whether I can squeeze any juice out of this little thing. It only has 512 MB Ram, 40GB HDD, 2.4Ghz Pentium 4, ATI Mobile Radeon 64/128MB (can't remember). 
 
Currently I have Windows taking up about 16 GB (leaving me with about 24 GB leftover). I want to know how much space I should use for: /, /home (separate partition if possible for future upgrades), swap space, Windows, and a data partition (where I can store all my personal files which can be accessible between Ubuntu and Windows). This set-up makes 5 partitions which if I remember correctly cannot be done (if their primary, I don't know how logical partitions work). Another poblem is that if I make /home and my data partition the same one, what file system should I use. Will it automatically become ext4 (which Windows is having trouble with now), or can I format it specifically and still allow it to be /home? 
 
If it can be done, how much space should I allocate to each partition? 
 
Thanks.
 
BTW: On a side note, when I was trying it on a LiveCD, I left it for a while and the screen went completely white. I couldn't get out of it, so I had to manually shut down. Next time I stayed  with it while it loaded the LiveCD and had a play around with Ubuntu before shutting it down normally. Could the white screen have to do with the Ubuntu sleeping by any chance?

---

### Post by oldfred on 2010-11-20
This is my standard:

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

But in your case swap can be only 1GB or 2X RAM when RAM is below 1GB. I would not suggest a separate /home as you do not have a lot of room. I would make the extra space a shared NTFS partition and leave /home inside root.

Then you have something like this:

16GB Windows XP
12GB / including all system partitions
10GB NTFS shared data
1GB swap

Root can be as small as 4 to 6GB but you have to be careful to houseclean regularly and may not have room to write a DVD (if you have a DVD writer) as that will use 4GB of tmp space. IF only CD then smaller is ok also. If real tight on space you can replace some of the standard larger apps with lighter weight versions. No Firefox, no OpenOffice etc.

With 512 it should work ok, but you can try alternatives also.
Lighter weight Versions use with Chromium browser as it is lighter than firefox:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
Xubuntu, a "lightweight" distribution based on the Xfce desktop environment or add LXDE desktop (is not lubuntu)
Crunchbang: the unofficial Ubuntu Lite
Someone posted this:
Linux Mint XFCE runs fine on a PIII, 500 MHz
8 of the best tiny Linux distros
[http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552](http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552)
Slitaz, DSL, Puppy, Crunchbang

---

### Post by LimaBeans on 2010-11-20
Thanks for your reply. 
Woops, made a mistake. After my HDD's been formatted it's only 37GB. Would this set-up be OK?:
 
18GB Windows
12GB / and others
1GB Swap
6 GB NTFS and shared
 
Thanks.

---

### Post by oldfred on 2010-11-20
That works. When you have a computer with a larger drive you will want more but can work very well with that as long as you do not save huge amounts of data.

I like to set up partitions in advance using gparted from the liveCD or a gparted liveCD. The new Maverick installer is a little confusing I have heard. Since I always partition in advance and use manual install I have not seen the issues.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by LimaBeans on 2010-11-20
Yep, OK. By "huge" amounts of data, how big do you mean?
When you install programs onto Ubuntu, does it go in your home or your / ?

Yeah I think I partition it first. 

Thanks.

BTW: Have you ever heard of a problem where Ubuntu goes to sleep and goes completely white?

---

### Post by sikander3786 on 2010-11-20
**Oldfred** seems to be away for the moment so I am jumping in ;-)

When you install some programs on Ubuntu, they are installed to / partition. The only thing that goes to /home partition or home directory is their configuration/settings.

Most of the programs installed on Ubuntu are sized less than 30 MB most cases as the libraries are shared between them. I have installed all the regularly/daily needed software and still am using less than 4 GB space on /. So 12 GB would be sufficient unless you want to download all the software from repositores ;-)

Regarding the white screen issue, I feel I have heard it happen. Graphics drivers going bad... But that is not a bug in the newer versions and should not effect you.

---

### Post by LimaBeans on 2010-11-20
Hmmm...yeah, I think he's gone. 

Ahhh OK, so basically /home stores all my configuration while / stores all the apps themselves?
I don't think I want to download that many apps! Would it be OK to drop / to 10GB and increase Windows to 20GB (Windows is fat :D). 

Thanks.

BTW: I'm using a Belkin N1 Wireless Adapter for this laptop (yes highly overpowered considering how old this machine is), and as expected Belkin didn't release any Linux drivers. How would I go about using Ndiswrapper if I can't connect to the internet to download it?

---

### Post by sikander3786 on 2010-11-20
10 GB would be manageable for /.

Regarding wireless adapter, it would be better to start a new thread in the Networking and Wireless sub-forum. You'll get better answers there.

Open for further queries regarding installation :-)

Good Luck!

---

### Post by LimaBeans on 2010-11-20
Ok, that's good. Yeah I might open another thread for that separate issue. A question, with my / partition should I use ext3 or ext4?

Thanks.

---

### Post by sikander3786 on 2010-11-20
> with my / partition should I use ext3 or ext4?

Ext4 is the default with Ubuntu so I would go for that.

You can have Ext3 as well but Ext4 is an updated version to that and I've never had any issues regarding that.

If you are just curious, you can Google "ext3 vs ext4" and find the differneces ;-)

> Yeah I might open another thread for that separate issue.

I advised that because the title attracts the experienced users to the problem. I don't have any experience with wireless adapters and no one will come to your thread specifically for solving that problem for you as the titile suggests something else.

I hope you get it :-)

---

### Post by hyperAura on 2010-11-20
Hi guys, there is an issue for me as it concerns the dual boot installation..

Every time that you install ubuntu on a windows system, towards the end of the installation, you are being asked where to set the boot loader if I remember correctly..

In almost every time that I installed ubuntu in the past I managed to mess the boot loader and then had to reinstall windows and ubuntu all over again..

Can you remind me where to install the boot loader, as I also want to install the new ubuntu on a new machine?

Thanks

---

### Post by sikander3786 on 2010-11-20
> **hyperAura said:**
> Hi guys, there is an issue for me as it concerns the dual boot installation..

Every time that you install ubuntu on a windows system, towards the end of the installation, you are being asked where to set the boot loader if I remember correctly..

In almost every time that I installed ubuntu in the past I managed to mess the boot loader and then had to reinstall windows and ubuntu all over again..

Can you remind me where to install the boot loader, as I also want to install the new ubuntu on a new machine?

Thanks
This would be called thread hijacking :-)

It would be better to start a new thread regarding your own problem.

You need to install it your relative hard disk e.g, sda or sdb. Note that it doesn't contain a number at the end.

And if you are going to install 10.10, the installer has changed a bit. The bootloader option appears at the bottom of Manual Partitioning page only, not at the end. And if you choose to partition automatically or install side by side with another OS, you'll not get that option at all.

Please start a new thread with all the necessary hardware details, existing OS installs and the output from this command.

```
sudo fdisk -l
```

Good Luck!

---

### Post by LimaBeans on 2010-11-25
Actaully, would this be a viable/good option?:
19 GB Windows (NTFS) - Primary
10 GB / (ext4) - Primary
1 GB Swap (ext4) - Logical
1 GB /home (ext4) - Primary (Is this enough considering I'm not putting any data files in this area?)
6 GB Shared Data (NFTS) - Primary
 
Thanks.

---

### Post by wilee-nilee on 2010-11-25
> **LimaBeans said:**
> Actaully, would this be a viable/good option?:
19 GB Windows (NTFS) - Primary
10 GB / (ext4) - Primary
1 GB Swap (ext4) - Logical
1 GB /home (ext4) - Primary (Is this enough considering I'm not putting any data files in this area?)
6 GB Shared Data (NFTS) - Primary
 
Thanks.

4 primaries is the max per HD. If you just put all the Linux partitions in a extended partition that will work.

So the max would be 3 primaries and one extended, but you can put all the Linux in the extended and just have the NTFS a primary, does this make sense. Size wise I don't separate the home, I just store everything off the computer basically and fill it with OS usually.

Having a separate home does make sense it just isn't the way I roll.

sikander3786 should be on again some time and they know all this stuff and can get back in to get you setup.

---

### Post by LimaBeans on 2010-11-25
Hmm... well the thing is I'm dual booting here. So basically I want a separate Windows, separate Linux (ubuntu) and/or swap (I'm not sure whether it goes in it's own partition...), separate /home (because it will help when I do upgrades), data partition (for all my data). Is there a way to do this effectively?

---

### Post by oldfred on 2010-11-25
Even though we like to have a separate /home, if you are only going to give it 1GB then it is too small and should be just in root. Then you can shared the extra space with /. You can still easily back it up if most data goes elsewhere. But default location for data is /home. My /home is about 1GB and I agressively move data to my shared or /data partitions. I have some of the defaults set a links so that still defaults else where for downloads & music but some programs default to hidden files & folders in /home.

---

