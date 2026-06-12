---
title: "SB850 Fake Raid not working"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by Kronon on 2010-07-14
I've bought a new computer and want to put Ubuntu (prev kubuntu) on it.
It has 3 disks. Because I want to use raid 5.
It has a 890XFA-GD70 (MSI) motherboard with a (amd) SB850 southbridge.
Also have a T1090 amd processor on it.

I created a Fake Raid array with it. And Windows is running on raid 5 now.
I tried installing Ubuntu 10.4 LTS & Kubuntu 9.10. Both won't find a raid array.
Running dmraid -ay with the installer cd's give me
ERROR: pdc: zero sectors on /dev/sdc
ERROR: pdc: setting up RAID device /dev/sdc
ERROR: pdc: zero sectors on /dev/sdb
ERROR: pdc: setting up RAID device /dev/sdb
ERROR: pdc: zero sectors on /dev/sda
ERROR: pdc: setting up RAID device /dev/sda
no raid disks

Doing fdisk on the drivers gives me:
sda: 3 partitions
sdb: 0 partitions
sdc: 0 partitions
Also gives some error on the mbr about it being wrong or something.

Using AHCI and NCQ on the drives

Can't use (linux) software raid, because I also want windows 7. And FakeRaid + Software raid won't work together.

Any ideas on how I get it working?
Tried searching the internet but only got dead ends.

---

### Post by Kronon on 2010-07-16
Found some other post on this forum ([http://ubuntuforums.org/showthread.php?t=1519043](http://ubuntuforums.org/showthread.php?t=1519043) ) having the same problem. Although he didn't go as in depth as I did.

Does FakeRaid just not work on SB850 chipsets?

---

### Post by ronparent on 2010-07-16
Type 'dmraid -l' in a terminal - that will list the supported chipsets.

---

### Post by crimzon on 2010-07-22
Just resolved this issue on my system, more or less what you are going for I think. I was reading a lot of documentation and it looks like it's just better to go with software raid and skip the HW controller all together. 

Fresh install of Ubuntu Studio 10.04 with (3) 1TB drives. I have a 500GB drive stuck in there for windows later on, since it doesn't play well with others.

This is a good thread with some screen shots.

[URL="http://ubuntuforums.org/showthread.php?t=1373742&highlight=software+raid"]"http://ubuntuforums.org/showthread.php?t=1373742&highlight=software+raid"
[/URL]

I just cleared all three drives, auto partitioned, set each one bootable and to ext4 and "/" leaving the swap alone. Then I used the "configure software raid" option at the top, selected the 3 data partitions I wanted to use and finished that.

Now back on the partition screen, you should see your new RAID at the top. Just press enter to go into it and set the mount point as "/" and hit finish at the bottom of the page to start install. 

Grub installed to all three drives' boot sectors for redundancy. Everything seems happy now. 

Read Benchmarks of my RAID 5: 

| min 105MB/s | max 232MB/s | avg 165MB/s |



Further Thoughts: 

I would install your Win7 to a separate drive if you have one to simplify boot and raid issues, then modify GRUB accordingly.

Manually partition the individual drives with ext4/swap but leave room on each drive to set up a Win7 based software raid through Windows Disk Manager (pretty simple from what I've seen.)

That way you end up with Ubuntu installed to a bootable RAID with the option of booting to Windows and taking advantage of all your drives in an independent NTFS software raid down the road.

Hope this makes sense. Hope I'm not giving you bad advice, but this seems the best way for me.

---

### Post by ronparent on 2010-07-23
That is one solution. Another, I just discovered yesterday, is just to add a package that was omitted from the 10.04 distribution. Apparently 10.04 doesn't install without workarounds because the distribution omitted the package kpartx! It could be easily added to a 10.04 live cd session and then 10.04 easily installed by the installer run from that same session.

---

### Post by WinstonChurchill on 2010-08-05
I have this same issue on a Gigabyte board (AMD SB850) with three 500GB HDD's in a RAID5, and installing the 'kpartx' package does not resolve the issue. If I put the HDD's in a RAID0, Ubuntu can see it (even without dmraid); but no such luck with RAID5, and when I run dmraid I get the exact same error as the OP. 

Interestingly, a Windows XP boot CD I had laying around can see the RAID5 without any issue at all - this is probably the first time in my life I've ever had problems with disk hardware in Linux but not in Windows. I have an old 4th HDD that I plan on using to boot Linux - the idea is that I run windows on the RAID5, and I can boot linux and mount my windows drive to get at the files there if I ever want to, so obviously linux-software RAID isn't a good solution...

I'm going to work on this for awhile, and I'll post any solution I find - but in the meantime, any ideas?

**EDIT: **I gave up - stuck with Linux software RAID. I've been looking for a good excuse to ditch Windows forever - and here it is! Plus, the FakeRAID BIOS controller seems to be VERY poorly written... I trust Linux a lot more.

---

### Post by Kronon on 2010-08-21
Tanks for the replies.
software raid is no option for me as I use windows 7 with fake raid.
Hope I get raid working with the additional packet.
But I think the kernel is just plain lacking support for the SB850 raid driver.
Don't really know were I can get an answer to that question though.

P.S. Windows (XP/Vista/7) detect the raid array because they use bios calls. Linux doesn't. So Linux is fully dependant on drivers.

---

### Post by ronparent on 2010-08-21
Linux doesn't use drivers for fakeraid. The program dmraid serves that purpose. Fakeraid support is quirky however and behavior varies from one Ubuntu release to another. Another reason you will have to show more focus if you want to get it to work (or if it is workable).

I have the same chipset on a gigabyte board which allows me to use raid 0. To discover how the raid set appears to your system and whether or not the raid 5 is supported, look at it from a live cd. Booted to a live cd open a terminal and enter the commands:

sudo dmraid -r

sudo dmraid -s

Post the output here and we'll see if you drives are discoverable.

---

### Post by Kronon on 2010-09-06
They both give:

ERROR: pdc: zero sectors on /dev/sdc
ERROR: pdc: setting up RAID device /dev/sdc
ERROR: pdc: zero sectors on /dev/sdb
ERROR: pdc: setting up RAID device /dev/sdb
ERROR: pdc: zero sectors on /dev/sda
ERROR: pdc: setting up RAID device /dev/sda
no raid disks

Btw. I heard rumours that AMD raid is nothing more then rebranded promise raid (more or less).

---

### Post by ronparent on 2010-09-06
The pdc designation is indeed a promise raid. The bad news is that pdc apparently doesn't support level 5, at least thru dmraid in Linux (ie code: dmraid -l yields 'Promise FastTrack (S,0,1,10)')! It appears that the only raid chipsets which support level 5 in Linux are nvidia, isw (intel) and ddf1. I'll say it for you - this sucks.

---

### Post by Kronon on 2010-09-07
You took the words right out of my mouth;). So I won't bother saying it.
I'm a bit dissapointed at amd that they haven't tried some way to get support on Linux.

I'm even more dissapointed that I found out that real RAID is slower then fake RAID.
So buying a card with real raid, would cost me 350 and give me less performance.

Note: found source file version of drivers for one of there raid cards ... [http://englishsupport.promise.com/upload/Support/NEC/SRC/SRC-306100003.tar.gz](http://englishsupport.promise.com/upload/Support/NEC/SRC/SRC-306100003.tar.gz)
I bet they use a standard algorithm for all there raid products.

Maybe it works

---

### Post by ronparent on 2010-09-07
Don't expect much. One of the reasons the linux community calls it fake raid is that the fakeraid chip set is not a fully implemented hardware raid. In fact, it is closer to a software raid (which is why the program dmraid supprts most MB raid chipsets). It is also why, like in your case, that although a level 5 is available in Windows, the general purpose dmraid hasn't caught up with it in linux. 

You might have a point however. Maybe more of the raid 5 capability is built into the chipset and accessible thru the driver for linux. It is more likely a reach to expect a hardware driver to work with the fakeraid chipset.

---

### Post by Rebelli0us on 2010-09-12
Ubuntu will not run on my GIGABYTE GA-890GPA-UD3H either. It cheerfully installs, trashes the existing windows bootloader and boots with "grub rescue". Linux runs fine off the Desktop CD but will not boot off SB850.

I returned the mobo, I consider anything that doesn't run on Linux to be defective. AMD has very poor support for Linux, so punish them (along with the hardware manufacturers). I'm replacing the mobo with NVIDIA chipset.

---

### Post by ronparent on 2010-09-12
That is one solution. I have used MB's with nvidia chips also. At the time they have offered their own glitches. So I am not inclined to that rash a conclusion - otherwise I might have concluded that any OS that doesn't run on otherwise reliable hardware is defective (not true)!

---

### Post by Rebelli0us on 2010-09-12
> **ronparent said:**
> That is one solution. I have used MB's with nvidia chips also. At the time they have offered their own glitches. So I am not inclined to that rash a conclusion - otherwise I might have concluded that any OS that doesn't run on otherwise reliable hardware is defective (not true)!

The problem is AMD has poor support for Linux. They're not providing open source video drivers, so Linux devs have to reverse engineer drivers.

The video driver alone causes systems to idle at 10-15 watts AC higher in Linux than in Windows. It looks like the same mess with the chipset drivers. In fairness, could be that if AMD provided open source for their new technologies, Intel might take advantage.

Regardless, hardware manufacturers must support Linux or the Windows monopoly will never end. I love my AMD Phenom II X4 B55 but I'm gonna punish AMD, there are still plenty of mobos with NVIDIA chipset that work better in Linux, especially their video drivers.

---

### Post by SeattleJoe98101 on 2010-11-11
I'm not sure if this is the right thread, but here's my situation:

I dual boot Windows 7 and Ubuntu.  I have a Gigabyte (MA 790X-UDOP4) motherboard with  fake Raid.  The motherboard has two controllers, but I used the one from  Gigabyte, which I believe is equivalent to a jmicron386.  I presently have a Raid 1  array on two 2 TB drives.  The motherboard runs an AMD quad core chip.

I tried several times to install with the Maverick CD (both desktop and  alternate --AMD 64 bit), but it failed every time.  When I got to the  partitioning page it would show nothing to partition.  Finally I tried  an old Karmic 64 bit CD.  That worked perfectly, and I was able to see  my raid array.  I then partitioned the drive with qparted and installed Windows.   The CD also allowed me to use DD to copy a raid disk partiton to an img  file on another raid partition.  Windows sees both of these files OK and  in fact, Windows has no problem whatsoever with the Raid partitions.

I then installed Karmic to a partition.  I tried upgrading to lucid, but  after the upgrade, it wouldn't function properly.  I then reinstalled  Karmic and did the upgrades (but not an upgrade to Lucid).  I then began  having problems booting the partition.  On another (non-raid) drive I have a Maverick installation.  It boots fine, but doesn't see the raid; rather it sees the two mirror drives as separate.  Installing kpartx does nothing.  An installation of dmraid results in a statement that it is already installed and is the latest version.

The question I have is whether there is a way to install the newer  versions of unbuntu on a fake raid array.  It looks to me like they  changed something after Karmic and dropped support for my type of Fake  Raid.  So is there some way I can get it to work.  And will Natty have  support for this type of fake raid?  If not, does one of the other Linux  distros have such support?  

Alternatively, is there something that I can do with Maverick to make it  work?  I have tried using the alternate CD and also installing kpartx  before trying an install.  This appears to let the system see the Raid  Array, but doesn't permit an installation to it.  I don't know how to  install kpartx from the alternate CD and so I haven't tried that.

If replying, please assume that I know nothing and need step by step  instructionsl

Thanks in advance.

---

### Post by Cynical on 2011-01-29
I apologize if I'm responding to a dead thread at this point but I am using a motherboard with AMD's SB850 chipset and I have no issues installing Ubuntu 10.10 onto a fakeraid array composed of two 1TB Hitachi drives. The installer recognizes the array so I don't even need to do anything from the command line. However I think I'm done with windows so I'm going to try out software raid performance in linux :)

---

