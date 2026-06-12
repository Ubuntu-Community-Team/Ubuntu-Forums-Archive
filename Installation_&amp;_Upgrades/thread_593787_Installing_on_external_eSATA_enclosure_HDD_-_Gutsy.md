---
title: "Installing on external eSATA enclosure HDD - Gutsy"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Ellipsys on 2007-10-27
Hello all. I am currently looking to dual boot Windows Vista x64 and Gutsy. Windows is all ready installed, and I want to give Gutsy its own Hard Drive, considering the problems I've heard about resizing Vista partitions.  

With this in mind, I've been thinking about getting an eSATA external enclosure. This would basically provide a passthrough so that it would look like a "normal" internal SATA drive, I believe. As such, it should be easy to install Gutsy on it, right?  I would also like to know the following

1. What happens if I unplug the eSATA After installation? Ie. Will Windows still be able to boot, and Linux simply wouldn't be displayed in the GRUB boot menu? 

2. Would I be able to use it as a portable linux install on any PC? I'm guessing not, but I thought to ask.

Thanks.

---

### Post by Ellipsys on 2007-10-28
Good idea? Bad idea?

---

### Post by FXEF on 2008-01-20
> **Ellipsys said:**
> Hello all. I am currently looking to dual boot Windows Vista x64 and Gutsy. Windows is all ready installed, and I want to give Gutsy its own Hard Drive, considering the problems I've heard about resizing Vista partitions.  

With this in mind, I've been thinking about getting an eSATA external enclosure. This would basically provide a passthrough so that it would look like a "normal" internal SATA drive, I believe. As such, it should be easy to install Gutsy on it, right?  I would also like to know the following

1. What happens if I unplug the eSATA After installation? Ie. Will Windows still be able to boot, and Linux simply wouldn't be displayed in the GRUB boot menu? 

2. Would I be able to use it as a portable linux install on any PC? I'm guessing not, but I thought to ask.

Thanks.

Bump Bump

Ellipsys, I see no replies to your post. This is something I would like to do, however would like input from users that have done this before I invest in the hardware.

Come on guys.... give us a little input. Good or Bad:-({|=

---

### Post by KRGiff on 2008-01-21
Hi.  I have done this very similar setup (I'm using a mobile HD setup), and I know that if your BIOS permit it, you can select and boot your Win Vista on internal SATA or IDE HD or your Unbuntu HD on eSATA.  By using this setup, you wouldn't have to bother with dual-boot setup (or GRUB) at all, and this may be a much easier and trouble-free setup for you.  I know that if you can boot your Ubuntu Installation CD and see your eSATA drive, then you can install on it and then you'll have both OS to boot from.

If you have your Win Vista and Ubuntu drives powered up when booting and with appropriate filesystem software installed, you will be able to see the drives on each other operating system and you can read/write files to each OS drives.

---

