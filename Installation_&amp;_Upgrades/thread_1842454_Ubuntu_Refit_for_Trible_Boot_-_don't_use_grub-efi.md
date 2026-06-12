---
title: "Ubuntu Refit for Trible Boot - don't use grub-efi"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by metapunk on 2011-09-11
I just wanted to share some of the trials and tribulations of my own trying to get Ubuntu working on my already dual boot iMac. 

Basically I already have Windows 7 and OS X 10.6 Snow Leopard working with reFit.

I hadn't partitioned my computer to incorporate Linux so I had to resize the Os/X partition. First I defragmented it with DriveGenius as it had previously been full. I'm not sure if diskutil resizeVolume would of worked without this. Being defragmented it went quickly and I shrunk my partition down to 320G from 1.8 terabytes. 

Then I installed Linux, from the 11.10 beta install CD for AMD64.This went fine but I think I installed grub incorrectly, or it wouldn't boot after the install from refit.

gptsync also wouldn't run as the MBR didn't have my new shrunken linux partition in it.

So I did the whole manual attempt to reinstall a grub loader onto the particular partition. It gave me an error about installing onto a blockless partition. If I had forced it things might of went through a lot better, but instead I googled and thought that I needed to install grub-efi and the amd64-efi packages. This was incorrect because Refit will boot into BIOS compatibility mode with the grub boot loader providing me with a unknown filesystem error. Eventually I installed grub-pc back and ran the command grub-install --recheck --force /dev/sda3 (the partition I have linux on). Upon rebooting my penguin icon worked.

Another interesting thing I ended up doing was creating my own hybrid MBR that allowed my windows partition to exist even though it was now past the normal alloted 4 primary partitions. [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html) is a great guide for how to use gdisks to do this.

So basically I just wanted to post in case someone else was running into this kind of issue with the hopes that this would help them.

---

