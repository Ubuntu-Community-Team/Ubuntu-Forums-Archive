---
title: "Windows 7 dual boot with ubuntu (ubuntu already installed)"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by AsianInvasion on 2010-02-01
Alright so I built a new computer recently and a friend of mine gave me ubuntu 9.10. It's pretty awesome but I need windows for the ease of running Sony Vegas 9.0 and Adobe CS4 master suite. As well as a few games. So I'm currently downloading a Windows 7 torrent (yes I'm that cheap). But I need some help on installing it along side Ubuntu. Would it just be easier to wipe my drive and install windows. If so how would I install it from a torrent if my HDD is empty. 

Thanks!

---

### Post by bcamp929 on 2010-02-01
Use gparted to create the new partition, boot into the win7 install and install it to the new partition...

---

### Post by wilee-nilee on 2010-02-01
W7 will take over the MBR when installed so you will have to reload grub as the linux grub bootloader from a live cd to boot both basically. Here is a link step 11 is what your looking for.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

If you don't have a key for W7 it will only work for so long, do yourself a favor and get a legal copy.

---

### Post by AsianInvasion on 2010-02-01
I plan on buying a retail copy in about 2 weeks when I have some cash. So do you I just have to put my ubuntu CD in after windows 7 is installed?

---

### Post by wilee-nilee on 2010-02-01
> **AsianInvasion said:**
> I plan on buying a retail copy in about 2 weeks when I have some cash. So do you I just have to put my ubuntu CD in after windows 7 is installed?

Yes basically, you have to put some simple code in the terminal. If you have any problems just post there are some regulars who can work out problems quite well. You want to shrink the 9.10 with a live cd using gparted leaving a open space for W7, gparted in 9.10 will format the W7 space to ntfs and it will  be recognized by the installer if needed.

---

### Post by djchandler on 2010-02-01
I did what you are doing (except I already owned a legal license for Windows 7) and the advice given above is very accurate. I had an easier time of it because I did it before 9.10 was released. GRUB 2 makes it a bit more complicated than it was with GRUB 1 and 9.04. But I can verify that the above instructions will work and leave you with a dual-boot system.

Back up your valuable data first.

---

### Post by wilee-nilee on 2010-02-01
> **djchandler said:**
> I did what you are doing (except I already owned a legal license for Windows 7) and the advice given above is very accurate. I had an easier time of it because I did it before 9.10 was released. GRUB 2 makes it a bit more complicated than it was with GRUB 1 and 9.04. But I can verify that the above instructions will work and leave you with a dual-boot system.

Back up your valuable data first.

I have a netbook which had W7 and the desktop and the netbook version of Lucid on it, I removed the desktop version and expanded the netbook version into that space. When I did this I lost the grub boot loader, I just followed the live cd step 11 the first one I believe and I was back in. You just want to make sure to run sudo update-grub when you finally get back into the original 9.10 install after the W7 install and grub reinstall.

---

