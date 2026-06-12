---
title: "Help!!! Cannot install Ubuntu 7.10"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by Graham1 on 2008-01-03
Hi

Please help!!! From the installation, I get as far as the partitioning and mounting part (4 of 7, I think) and then it just seems to freeze after applying these settings (the cursor just keeps on spinning). I left the laptop for a good 20-30 mins and it was still applying these settings. 

My partition setup is shown below:-

1. Windows XP (ntfs, not mounted) = 12GB
2. Ubuntu 7.10 (ext3, mounted as /) = 12GB
3. Boot (fat32, not mounted) = 100 MB
4. Swap (linux-swap, mounted as swap) = 2 GB
5. Data (ntfs, mounted as data) = 9 GB

Any ideas what the problem could be? Btw, my laptop is an Compaq nx7010 (1.6 GHz, 512 MB Ram).

:)

---

### Post by gazj on 2008-01-03
if you mean by boot the folder /boot in your ubuntu installation it cannot be fat32, must be ext2/3 or some other linux filesystem

---

### Post by Graham1 on 2008-01-03
> **gazj said:**
> if you mean by boot the folder /boot in your ubuntu installation it cannot be fat32, must be ext2/3 or some other linux filesystem

The Boot partition is used only by XOSL to boot between XP and Ubuntu 7.10. It just seems that the partitioning software isn't doing anything and is stuck on that window.

:)

---

### Post by gazj on 2008-01-03
well personally i would scrap that, and let ubuntu's bootloader worry about the dual booting, it will do a much better job of it, basically becuase it's ubuntu supported way.

---

### Post by Graham1 on 2008-01-03
Personally, I prefer to use XOSL and have each OS install their bootloader in their own partition. This shouldn't cause any problems as I'm running this setup on my main computer (XP and Ubuntu 7.10) and tablet pc (Ubuntu 7.10, openSUSE 10.3 and Fedora 8 ). Maybe this is a problem with 7.10 on this laptop as 7.04 worked fine.

:)

Edit: Thinking about it, the only difference between this laptop (nx7010) and my other computer/tablet is that my data drive is now using ntfs. Would this have anything to do with it?

---

### Post by bigken on 2008-01-03
try the alternate cd or try creating your partitions with gparted live cd

---

### Post by Arkaniad on 2008-01-03
Grub would be better-

if you are installing linux before xp-

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

Vice-Versa-

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

i bet you can use a fat32 partition to swap files between win/ubuntu

---In the news----

MS planning to ditch XP later in 08
Either year of Penguin or Apple

Screw Vista- if you want an easy to use OS choose Ubuntu. 

Oh and yea- Ubuntu 7.10 runs with 256 mem (even the live cd)
Dell inspiron 7000 maxed out memory otherwise factory condition will run 7.10 or lower

---

### Post by Graham1 on 2008-01-03
> **bigken said:**
> try the alternate cd or try creating your partitions with gparted live cd

What is "the alternate cd"? To be honest, I'm a bit wary of using GParted Live CD as I used Parted Magic earlier today and it didn't seem to setup my partitions correctly (it was leaving the odd space here and there, not what I had setup). I ended up having to use Partition Magic to correct the problems.

:)

---

### Post by gazj on 2008-01-03
i wouldn't think your ntfs would be the problem, there are loads of installations out there that have gone through with ntfs around just fine.  It is a strange one.  Try setting your partitions first as suggested with gparted or cfdisk or fdisk in a command line from the ubuntu live cd.  See if you have anymore luck.

---

### Post by gazj on 2008-01-03
the alternate cd is available to download from the ubuntu website, instead of installing from a livecd, it is a standard installation cd like the win2k or winxp installation cd.  It's always worth a try when the live cd won't behave as in your case.  In fact it's my preferred way on installation.

Good Luck ;)

---

### Post by Graham1 on 2008-01-03
> **gazj said:**
> the alternate cd is available to download from the ubuntu website, instead of installing from a livecd, it is a standard installation cd like the win2k or winxp installation cd.  It's always worth a try when the live cd won't behave as in your case.  In fact it's my preferred way on installation.

Good Luck ;)

I've never heard of this cd. Thanks, I'll download this and give it a try.

:)

---

### Post by Graham1 on 2008-01-07
Strangly, after getting past the partitioning part (using the alternate cd), I was unable to install GRUB to sda0,1 (second partition). I tried the default hda0,1 first and then tried the following:-

/dev/hda2
(sda0,1)
/dev/sda2

Still no joy :(. Not sure why it wouldn't let me install. Also, having looked at my partition table (in XP), my boot and data partitions had become un-readable.

:)

Edit: Forgot to mention, I then reformatted my NTFS data partition to FAT32 and I was then able to use the original cd (past the partitioning part :) ). Still wasn't able to install GRUB though :(.

---

### Post by tdm on 2008-03-20
Make sure your XOSL bootloader doesn't have MBR virus protection turned on. Or your BIOS may have MBR virus protection on. :confused: :confused:

---

