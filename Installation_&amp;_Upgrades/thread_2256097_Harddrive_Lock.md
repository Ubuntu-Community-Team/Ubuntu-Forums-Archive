---
title: "Harddrive Lock?"
date: 2014-12-09
forum: Installation &amp; Upgrades
---

### Post by jamesbeckjr on 2014-12-09
I received a laptop that didn't have a charger or OS. It would try booting from the Hard Drive but it would through "Disk read error. Press Ctrl+Alt+Del to restart. The bios was locked with a password. I used a livecd and CMOSpwd to blank the bios password. When I tried to install ubuntu to the hard drive that came with the laptop it would fail. The install asks me to connect to the internet, I did, then the next screen checks for available space, powersupply, and internet connectivity. There was a green checkmark by the available space and power and internet. I told it to use the entire disk, but when I past that screen, it throws an error 
input/output error during write on /dev/sdb

I tried livecd-ing and running the fdisk -l command, nothing. I am currently using a 20GB hard drive in the laptop, so the cd works
and so does everything else. I went into the manual partitioning option, I get ZERO errors when setting up the partitions. Manual setup 
yields the same input/output error. 

I know it sounds like a bad drive, but I have a bad drive that I tried using and I can't even get a green check mark by available space. So I 
am beginning to think that the harddrive is password protected like the BIOS were. How can I know for sure?

---

### Post by jamesbeckjr on 2014-12-09
The hard drive in question is:
HITACHI HDD 5K500 B-320 
320GB 5400RPM

The laptop I am currently using is a Gateway NEW95

---

### Post by tgalati4 on 2014-12-09
Use Hitachi's diagnostic tool to test it.  If it passes, then try a low-level format.  Some disk drives have a self-destruct feature (especially corporate computers) to prevent data leakage.  Because the price of disks is low, it might be better to buy a new hybrid drive (SSD and hard disk), or just an SSD or just a fast spinner.  A 5400 rpm drive is relatively slow for daily use.

---

