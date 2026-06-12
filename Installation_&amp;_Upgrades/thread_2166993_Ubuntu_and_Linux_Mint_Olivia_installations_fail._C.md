---
title: "Ubuntu and Linux Mint Olivia installations fail. Can you help?"
date: 2013-08-11
forum: Installation &amp; Upgrades
---

### Post by robert14 on 2013-08-11
Hello. Thanks for your time.

I have a UEFI ASUS m5A97 MB. My hard drives are in GPT format.  I have tried several times to get Linux to install (Inlcuding Ubuntu), with only partial success. For Example:

I have LinuxMint Olivia on a partition adjacent to my Windows 7 installation. 
Windows has a 100MB fat 32 partition, an un-named 128 meg partition, and it's C:\drive (SDA1-2-3)

Linux is: 
/Root=SDA4 with bootloader.
Home=SDA5
swap=SDA6

It's there, I just cannot access it. I have tried EasyBCD within Windows, no results at all. I have tried Ubuntu Boot Repair which gets me access to any Linux installation I have tried, but I cannot boot into Windows 7... which is a problem because I'm not ready to bag Windows yet.

I have tried a separate Hard Drive install, same hard drive; separate partition install, and separate hard drive install of Linux while the Win7 is unplugged from the motherboard... that was interesting. Linux installs, and boots fine. When I plug in my Windows 7 disk NOTHING happens, like Windows 'sees' the Linux partition and decides to show me that it hates me. 

Can you guide me as to how I can achieve dual boot from this point? As I said, LinuxMint is on my hard drive right now... I just can't use it. 

Would it be useful to format my drives back to MBR format, then install windows 7, then Linux? This may be viable, because I was, for a very limited time, successfully running both systems. My Win7 was installed before the installation of the UEFI board, with MBR disks. The whole thing came crashing down because the hard drive was going bad.

Thanks for your time and guidance. 

Robert

---

### Post by r_avital on 2013-08-12
Robert,

I have zero knowledge of UEFI and I wish I had a direct solution to the problem.  But since you have received no replies for a while, I have a couple of suggestions:

1. If you're willing as a last resort to reinstall from scratch, then from all I've read over the years about dual-booting with linux and windows, linux should be installed last.

2. Instead of dual-booting, since you're not ready to bag win7 yet, consider installing Linux only on your HDD, and installing win7 as a VM under it, that way you don't need to bag it at all.  Use either Virtualbox or VMWare's VM Player (free, my prefrence).  It runs very well on my end, but expect the win7 performance ("experience index" or whatever MS calls it this week) to decrease a bit.

Hope this helps.

---

