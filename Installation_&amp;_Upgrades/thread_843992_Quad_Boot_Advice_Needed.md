---
title: "Quad Boot Advice Needed"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by SidewinderPro2 on 2008-06-29
I'm planning on doing a quad boot very soon and I need some recommendations on how to pull it off. I've got Windows XP x86 bit running on my main drive and I wish to leave it the way it is. Its a 500 GB and its my main gaming setup. I currently have Windows XP Pro x64 on my secondary drive for my Crysis performance increase attempts and other things. 

I'd like to setup my secondary drive with XP Pro x64, Linux Mint 5.0 because its excellent, and Vista Home Pro x86 for some gaming testing. How should I go about getting Mint and Vista on the second drive? 

Currently I'm using the standard XP boot loader without any trouble. A menu comes up upon startup and asks to select x86 or x64 without problem. 


First, can I install Mint and Vista to the secondary drive and not damage the current XP x64 partition? XP x64 has complete use of the 250GB secondary drive, and I'm worried that partitioning it now will result in files being corrupted or wiped out, leaving a nice mess. Would it be best to wipe the drive with XP x86 or try slicing up the partition as is? Would the boot loader need to be manually modified to prevent trouble if x64 was no longer on the system?


Secondly, I need to know how to get all four operating systems to be easily accessible without having to change BIOS settings everytime I want a different operating system. I'm going to be using separate hard drives after all.

---

### Post by PmDematagoda on 2008-06-29
1:- Yes you can, but you must ensure that you install both OSes to the second hard drive and not the first.

2:- You can do that using GRUB which is installed when Ubuntu is installed, it should also be configured properly by Ubuntu on install, so you should first install Vista and then Ubuntu to make the process easier.

---

### Post by SidewinderPro2 on 2008-06-29
As far as installing Vista and Mint on my secondary hard drive, should I try repartitioning the currenty XP x64 install? I'm thinking the best route would be to wipe the drive, then install XP x64, Vista, then Mint. I'm still debating whether or not I should do that or just install Mint 5.0 on the secondary drive and just go with the dual boot.

---

