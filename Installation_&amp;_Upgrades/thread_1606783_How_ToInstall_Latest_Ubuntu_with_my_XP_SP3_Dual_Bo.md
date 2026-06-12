---
title: "How To:Install Latest Ubuntu with my XP SP3 Dual Boot Same Physical Disk or Separte?"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by NuxIT on 2010-10-26
I was going to go ahead and intall Ubuntu 10.10 on my Windows XP w/sp3 Machine for a dual-boot config. I've done this before without issues but want to see what setup is Optimal giving my current disk drives.

Here's my current setup in this picture. You can see I have my windows on Disk0 C: and the other 38GB on this drive Unallocated.

My other 80GB drive has Two 40GB windows file systems but I could erase one of those (Disk I:) to install Ubuntu on. Does it really matter? From what I recall Grub takes over fine and manages the boot. Thanks for any tips before install. 

Should I install on Unallocated on Disk0 or free up unallocated space on Disk1 for Install? thx

[IMG]http://home.comcast.net/~16v/pics/nux.JPG[/IMG]

---

### Post by tommcd on 2010-10-27
> **NuxIT said:**
> 
Should I install on Unallocated on Disk0 or free up unallocated space on Disk1 for Install? 

It really doesn't matter which hard drive you use. I like having my operating systems on my first hard drive and all of my data partitions on my second hard drive. Since the unallocated space on Disk0 and the two partitions on Disk1 are all about the same size, and since the space on Disk0 is already unallocated, I would just go ahead and install Ubuntu to the 38GB of unallocated space on Disk0. 

Ideally, you should create three partitions:
**root**, for your system files
**swap**, for swapping out files in memory to the hard drive (this is analogous to virtual memory in Windows).
**home**, for your data.
You could go with a 10-15GB root partition, a 1GB swap, and the rest for home. I have a 10GB root partition on my laptop, and a 14GB root partition on my desktop. This has allowed me more than enough space to install all the software I want for several years without coming anywhere near close to filling up the root partition.
Then let Ubuntu install grub to the MBR (Master Boot Record) of your first hard drive (Disk0). There is no need to worry about allowing grub to control the MBR of your first hard drive. I have been dual booting Ubuntu + WindowsXP + several other linux distros for the past 5 years. I have never had any problems with getting grub-legacy or the newer grub2 to boot WindowsXP. It is easy enough to restore the WindowsXP MBR from the Windows install CD if you ever want to that anyway.
Here is a great site for getting started with Ubuntu:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
And to create a separate home partition during the install:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Write back if you need more help.

---

### Post by NuxIT on 2010-10-27
> **tommcd said:**
> It really doesn't matter which hard drive you use. I like having my operating systems on my first hard drive and all of my data partitions on my second hard drive. Since the unallocated space on Disk0 and the two partitions on Disk1 are all about the same size, and since the space on Disk0 is already unallocated, I would just go ahead and install Ubuntu to the 38GB of unallocated space on Disk0. 

Ideally, you should create three partitions:
**root**, for your system files
**swap**, for swapping out files in memory to the hard drive (this is analogous to virtual memory in Windows).
**home**, for your data.
You could go with a 10-15GB root partition, a 1GB swap, and the rest for home. I have a 10GB root partition on my laptop, and a 14GB root partition on my desktop. This has allowed me more than enough space to install all the software I want for several years without coming anywhere near close to filling up the root partition.
Then let Ubuntu install grub to the MBR (Master Boot Record) of your first hard drive (Disk0). There is no need to worry about allowing grub to control the MBR of your first hard drive. I have been dual booting Ubuntu + WindowsXP + several other linux distros for the past 5 years. I have never had any problems with getting grub-legacy or the newer grub2 to boot WindowsXP. It is easy enough to restore the WindowsXP MBR from the Windows install CD if you ever want to that anyway.
Here is a great site for getting started with Ubuntu:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
And to create a separate home partition during the install:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Write back if you need more help.

Excellent, Thanks for your response. I figured it wouldn't really matter. I'm just going to go ahead and load it on Disk0. I can't wait to get another linux load going. Pissed that Sony remove my YDL from Playstation 3!

---

### Post by Mark Phelps on 2010-10-27
I wouldn't go so far as to say that "it doesn't matter" which approach you choose, but rather, would say that either approach should work equally well.

Personally, I prefer a different approach in which each OS, its "system" partion, and any shared "data" partitions are located together -- but on separate drives.

Over the years, I have found this to save me several times from problems associated with MBR corruption/overwriting, filesystem corruption, boot failures, and other such anomalies.

Using this second approach, each drive is independently bootable and has its native MBR intact -- untouched by the other OS.  This has become very handy when repairs were needed to either the MS Windows OS or the Ubuntu OS.  I could just have the drive I needed to repair connected, and not worry at all about ripple effects with the other drive.

---

### Post by NuxIT on 2010-10-27
> **Mark Phelps said:**
> I wouldn't go so far as to say that "it doesn't matter" which approach you choose, but rather, would say that either approach should work equally well.

Personally, I prefer a different approach in which each OS, its "system" partion, and any shared "data" partitions are located together -- but on separate drives.

Over the years, I have found this to save me several times from problems associated with MBR corruption/overwriting, filesystem corruption, boot failures, and other such anomalies.

Using this second approach, each drive is independently bootable and has its native MBR intact -- untouched by the other OS.  This has become very handy when repairs were needed to either the MS Windows OS or the Ubuntu OS.  I could just have the drive I needed to repair connected, and not worry at all about ripple effects with the other drive.

Cool/Cool. Good call. I'm just going to go ahead and free up the space on Disk1 and do the load their. That way, if I have OS issues the OS's will be on separate disk drives. :guitar:

---

