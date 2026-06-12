---
title: "Keep Getting Errors in CD Integrity Check; Installer freezes otherwise"
date: 2005-07-21
forum: Installation &amp; Upgrades
---

### Post by Dural on 2005-07-21
My brother and I just finished building a new computer. The computer's components are an AMD Sempron 3100+ with two hard drives (A 40 GB Samsung SV4012H and a 80 GB Maxtor DiamondBack 9 Plus), a MSI K8T Neo motherboard, and a Radeon 8500 video card. We are trying to make a dual boot system with two hard drives. The 40 GB hard drive will run into Ubnutu while the 80 GB hard drive will run Windows XP. My brother and I had already had a little experience with Linux through the Knoppix Live CD and we mostly enjoyed it save for the difficulty in setting up a connection to the home network in order to connect to the Internet.

After several failures at installing Windows XP, we decided instead to install Linux first. After searching for the right distro, we decided on Ubuntu because it seemed easy to install and use.

First, my brother downloaded Kubuntu in order to try it out, but after several installation attempts, it would start out well, then freeze. I noticed the integrity check integrated in Kubuntu and realized that one of the files had an incorrect checksum. We used winMd5sum (as recommended in the Ubunutu Wiki) to check the md5checksum of the iso (i386 Install CD version) to see if it was incorrect and the iso was fine. At the time, we thought that maybe the modified version would not work on our computer, so we went with Ubuntu.

We downloaded Ubuntu (i386 Install CD version) and checked the checksum of the iso; the checksum of the iso matched that of the checksum listed in the MD5SUM text file.However, every time we burned the iso even at the slowest speed of 4X (I think that is 600 b/s in Nero), the integrity check would always say that the CD is corrupted even though the MD5 checksum of the ISO was correct. In fact, the corrupted file was: ./pool/main/l/language-pack-ru-base/language-pack-ru-base-20050406-all.deb

I loaded the latest CD we burned and replicated the error and also noticed that when the integrity check runs, it runs fine until it reaches 15%. Then the screen begins the blink until the integrity check fails.

If anyone can help us with this problem, it would be much appreciated.

---

