---
title: "Dualboot 2 partition in one harddisk"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by imjscn on 2008-06-23
I downloaded xubuntu-8.04-desktop-i386.iso, plan to make a dualboot OS. 
Here's my PC condition:
Dell Dimention2400, 512MB RAM, 80GB storage, 2 partition on one harddisk. 
I've learned a lot reading posts in this forum, but before install, I still have some questions:
1. Each of myy 2 partitions (C and D) is equally 40 GB. WinXP already installed in C, plan to install Xubuntu in D. Do I need to go through the resizing/partitioning procedure?

2. Is 40G:40G reasonable? considering I have one or two software works with Windows only(I'm sure there's no replacement yet).

3. Is Swamp partition nessecory? Does it slow down performence?

4. I read from this link  [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
It introduce a Home partition, It's a great thing, but how to make such a partition during installing?

5. I need to install Wine for using some of Windows programes. Is it an option during Xubuntu installing, or I can install Wine after install Xubunu?

6. If things go wrong during install, I wish to boot back to Windows so that I can come back to this forum asking for help. So, What should I do before install? (I have backed up all my things)

I wish to hear your suggestions. Thanks very much for your time!

---

### Post by confused57 on 2008-06-23
> **imjscn said:**
> I downloaded xubuntu-8.04-desktop-i386.iso, plan to make a dualboot OS. 
Here's my PC condition:
Dell Dimention2400, 512MB RAM, 80GB storage, 2 partition on one harddisk. 
I've learned a lot reading posts in this forum, but before install, I still have some questions:
1. Each of myy 2 partitions (C and D) is equally 40 GB. WinXP already installed in C, plan to install Xubuntu in D. Do I need to go through the resizing/partitioning procedure?

2. Is 40G:40G reasonable? considering I have one or two software works with Windows only(I'm sure there's no replacement yet).

3. Is Swamp partition nessecory? Does it slow down performence?

4. I read from this link  [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
It introduce a Home partition, It's a great thing, but how to make such a partition during installing?

5. I need to install Wine for using some of Windows programes. Is it an option during Xubuntu installing, or I can install Wine after install Xubunu?

6. If things go wrong during install, I wish to boot back to Windows so that I can come back to this forum asking for help. So, What should I do before install? (I have backed up all my things)

I wish to hear your suggestions. Thanks very much for your time!

Thought I'd bump your thread...I'll give you my opinion, but anyone else is welcome to critique or offer a better suggestion.

You won't need to resize, just select manual partitioning...here's an excellent guide on partitioning:
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

40 Gb will be more than sufficient, a new install of Hardy will be about 4 Gb.

I would recommend approx. 1 Gb swap, with 512 Mb ram.

You can designate a separate /home partition during a manual installation.

Install wine after installing Ubuntu.

I would recommend downloading a copy of Super Grub Disk, before installing Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a very small download & can boot Windows or Ubuntu.

Another very useful utility would be the Gparted Live CD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
again, it's a small download & is a free, opensource partitioning tool

Basically, what you would probably need to do is delete the D partition after you select manual partitioning.  Then you should be able to set up the Ubuntu partitions on the free space.  I would recommend approx. 10 Gb for your root partition, mountpoint  /, primary partition, ext3 filesystem, beginning of free space...all but 1 Gb for /home, mountpoint /home, ext3 filesystem, logical partition, beginning of free space...the remaining 1 Gb will be swap, logical partition, mountpoint swap.

Another option after you delete your D partition...I think there is a selection for install on the free space, which would automatically install Ubuntu with a / & swap partition.

You may want to wait on other suggestions, but this should get you started.

---

### Post by Pumalite on 2008-06-23
+1

---

### Post by imjscn on 2008-06-23
Hi confused57, thanks for your detailed suggestion! I downloaded the two softwares, they are really the right solution for me.

I spend the whole day studying Linux things and solutions for my needs, especially the software which can't run in Linux. I arrive a point that...maybe a Virtual Machine is better than Dualboot for me. 

The thing is...I need to run the Windows software all the day.

If I completely switch to Ubuntu, will the partition size be the same as you suggested on Dualboot?

---

### Post by confused57 on 2008-06-23
> **imjscn said:**
> Hi confused57, thanks for your detailed suggestion! I downloaded the two softwares, they are really the right solution for me.

I spend the whole day studying Linux things and solutions for my needs, especially the software which can't run in Linux. I arrive a point that...maybe a Virtual Machine is better than Dualboot for me. 

The thing is...I need to run the Windows software all the day.

If I completely switch to Ubuntu, will the partition size be the same as you suggested on Dualboot?
I've never used Wubi or VMware, but I believe you would get much better performance with a dual boot.  You can set Windows to boot by default in grub...if you ever need to, Super Grub Disk can reinstall Windows bootloader(IPL) to the mbr.  Windows won't even know you have Ubuntu installed as a dual boot, you'll boot into each independently of the other.

The partition size(s) for Ubuntu are a matter of personal preference and necessity, depending on how you plan on using Ubuntu.  If you have data on your D drive and don't want to delete the partition, you can just resize it with the Gparted live cd:
[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)
then install Ubuntu on the free(unallocated) space.

Here's another excellent guide about partitioning that might be helpful:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

You may want to look into Wubi or VMware, if that's what you decide on.

---

### Post by imjscn on 2008-06-23
Many thanks! 
I just realized that I can't go dualbooting because I need the windows software running all the time. dualbooting means I can work only on one of the OS. Silly me, but learned a lot, ready to learn further :-)

Now, let me install Ubuntu first.

---

