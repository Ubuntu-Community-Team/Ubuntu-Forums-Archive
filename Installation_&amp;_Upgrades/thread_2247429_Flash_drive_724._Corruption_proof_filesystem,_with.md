---
title: "Flash drive 7/24. Corruption proof filesystem, without journaling?"
date: 2014-10-07
forum: Installation &amp; Upgrades
---

### Post by fernando29 on 2014-10-07
I am setting up an Ubuntu based system that should meet the following requirements:

1. It has to preserve the Flash drive (onboard eMMC) where it is installed. So it should only write when it is absolutely necessary.
2. It is going to be on 24/7
3. It will run unattended.
4. At occasions, It can be turned off without a proper shut-down. In those cases a file-system corruption must be avoided.

Now, as the preservation of the flash drive is the first goal, I have collected by googling, several tweaks that I am thinking in apply:

1. Do not create swap partition.
2. Leaving as much as possible unallocated space in the drive (supposedly this space can be used for the drive's wear leveling functionality).
3. Disabling Journaling for the / partition (ext4).
4. Use noatime, nodiratime and discard flags.
5. Mount '/tmp', '/var/log', '/var/tmp' on memory.

Regarding the system requirements and the measures taken to preserve the drive I have some questions:

1. It is supposed that I must disable journaling. And the system should be immune to filesystem/data corruption if there is a power failure. As journaling is used precisely to recover the system is such events, how could I balance this couple of countradictory requirements
2. Is it enough to disable journaling when the system is already installed?. Some posts say it should be disabled when the partition is formated, but It would make me lose several hours of work.
3. When '/tmp', '/var/log', '/var/tmp' are mounted on memory, it should be specified the amount of memory reserved to each dir. What happens if the system exceeds this size?. As the system will be running 24/7 and I can't reserve much space (this reserve reduces the amount of available RAM) it is likely that it wil happen.

I hope I can get some help and advice with what I am doing. 

Thanks.

---

### Post by tgalati4 on 2014-10-07
I would probably start with trimmed-down distro such as TinyCore Linux.  It is designed to run off of a USB stick with all of the write minimizations taken care of.  I have used Damn Small Linux (a predecessor to TinyCore) for embedded projects with another Ubuntu machine for development.  I could simply compile and drag over the binaries and they would run fine.  So you might consider a dual-machine development environment.  Just make sure your major kernel versions are similar on both platforms.

What is the hardware?  The hardware you use will impact these decisions.

---

### Post by fernando29 on 2014-10-07
Actually I started my work with TinyCore. Unfortunately, as the Kernel available was older than what I needed, and the low community participation in their forums, bring me to base my system on an Ubuntu Minimall install (you can find anything you need for Ubuntu).

The hardware is an Intel "NUC" board [DE3815TYBE]("http://www.intel.com/content/www/us/en/nuc/nuc-board-de3815tybe.html") (Atom E3815 processor, 4Gb Flash eMMC drive, and (in my case) 2 Gb in RAM.

---

### Post by tgalati4 on 2014-10-07
That NUC board seems to have some horsepower.  For shutdown protection, I would put in a 12VDC gel cell and define all of the power-off settings to perform an immediate shutdown.  For flash drive write-minimization, I would look through the Damn Small and Tiny Core Linux development notes for techniques that were used in those distros.  There may be a full, modern linux distro with similar flash optimizations, but I don't know of one off hand.

To me, a better option would be to run in RAM as a LiveUSB with some persistance for User data.  The User data can be on the same, or a different partition.  That way, a sudden poweroff will simply wipe the RAM.  The [LiveUSB]("https://help.ubuntu.com/community/UNetbootin") should last a long time.  The trick is to [remaster]("https://launchpad.net/relinux") it with all of your packages, configurations, and settings needed for your application.  It will probably take several iterations.

---

### Post by oldfred on 2014-10-07
As I understand it flash drives do not have the same internal memory as SSD and do not last as long. 
Do some flash drives have wear leveling logic, even?

The journal is to help speed up a restore of a file system after minor corruption by perhaps an abnormal shutdown. But if file system is smaller then just running fsck still will not take a long time, so journal is not as essential. Ext4 still has some advantages over ext2, but you still can turn journal off.

       With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sdb1

A user commented in this thread:

 How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
See comment: There&#8217;s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.

Flash drives do not support trim, so discard will not work. If using a small SSD then using fstrim command is now preferred to do trim.

I would think if keeping system up like a server, then battery backup would be vital.

---

### Post by fernando29 on 2014-10-08
Hi. Thanks for your contributions.

> **tgalati4 said:**
> That NUC board seems to have some horsepower.  For shutdown protection, I would put in a 12VDC gel cell and define all of the power-off settings to perform an immediate shutdown.  For flash drive write-minimization, I would look through the Damn Small and Tiny Core Linux development notes for techniques that were used in those distros.  There may be a full, modern linux distro with similar flash optimizations, but I don't know of one off hand.

To me, a better option would be to run in RAM as a LiveUSB with some persistance for User data.  The User data can be on the same, or a different partition.  That way, a sudden poweroff will simply wipe the RAM.  The [LiveUSB]("https://help.ubuntu.com/community/UNetbootin") should last a long time.  The trick is to [remaster]("https://launchpad.net/relinux") it with all of your packages, configurations, and settings needed for your application.  It will probably take several iterations.

Basing my system on a Linux Live would be a very good alternative. The problem was precisely with remastering. I tested Remastersys and it only works if there is a desktop on the system. As I understand, Relinux is the continuation of the already cancelled Remastersys project. However if the definitive solutions is boot to RAM [this ]("http://ubuntuforums.org/showthread.php?t=1594694")could do the trick.
 
> **oldfred said:**
> As I understand it flash drives do not have the same internal memory as SSD and do not last as long. 
Do some flash drives have wear leveling logic, even?

According with what I have researched, the onboard eMMC should have:

[http://www.smartm.com/files/salesLiterature/emmc/eMMC_technical_brief.pdf](http://www.smartm.com/files/salesLiterature/emmc/eMMC_technical_brief.pdf)

> **oldfred said:**
> The journal is to help speed up a restore of a file system after minor corruption by perhaps an abnormal shutdown. But if file system is smaller then just running fsck still will not take a long time, so journal is not as essential. Ext4 still has some advantages over ext2, but you still can turn journal off.

       With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sdb1

My system is about 900MB. Should I run fsck allways at startup?


> **oldfred said:**
>  
Flash drives do not support trim, so discard will not work. If using a small SSD then using fstrim command is now preferred to do trim.


Even if the storage device has wear leveling?.

---

### Post by tgalati4 on 2014-10-08
I see the dilemma using ReLinux.  Follow the basic steps of ReLinux, but do them on the commandline.  It will be tedious, but it can be done.  The link you posted is from 2010, but if it works with the later versions of kernel, then that would be one way to achieve a low footprint.

I'm not familiar with emmc devices, so only testing will determine how reliable they are with the OS configuration that you want to use.

---

### Post by oldfred on 2014-10-08
Most of what I have seen is USB flash drives which have some issues & limits. Not sure about your eMMC flash whether it is more like an SSD or a USB flash drive?

---

### Post by Michael_McKenney on 2014-10-08
I am not sure I would use a USB flash drive for this.  They can be flaky over time.  Many companies use SD media to boot from.  HP used SD on their blade servers.

---

### Post by fernando29 on 2014-10-08
> **tgalati4 said:**
> I see the dilemma using ReLinux.  Follow the basic steps of ReLinux, but do them on the commandline.  It will be tedious, but it can be done.  The link you posted is from 2010, but if it works with the later versions of kernel, then that would be one way to achieve a low footprint.

I'm not familiar with emmc devices, so only testing will determine how reliable they are with the OS configuration that you want to use.

When I tested Remastersys, actually I runned it from command, but it throw the following error:
> 
Error Remastersys:

Lightdm not setup properly. You must set your default desktop with lightdm prior to remastering

Which is contradictory to me. If you are running from command, why does it ask you for a desktop. At least folks at relinix project have made some serious changes since the project fork, it will fail in the same way. However I will do a try.

As for my link, the autor of the boot-to-RAM script uploaded an update for Ubuntu 14.04, 5 months ago

> **oldfred said:**
> Most of what I have seen is USB flash drives which have some issues & limits. Not sure about your eMMC flash whether it is more like an SSD or a USB flash drive?

Actually I have not found much useful information about. I think It is something between a USB Flash and a SSD. It has wear leveling and better speed than a USB 2 Flash, but I doubt It has what a fully featured SSD has to have.

It is a kind of chip used often on cell phones and other devices as main storage. Recently it can be found on SBC as BeagleBone and other Linux dev boards.

> **Michael_McKenney said:**
> I am not sure I would use a USB flash drive for this.  They can be flaky over time.  Many companies use SD media to boot from.  HP used SD on their blade servers.

Actually MMC memories seem to be very similar to SD. MMC even can be used on a SD socket. eMMC is just an "board mountable" version of MMC.

---

