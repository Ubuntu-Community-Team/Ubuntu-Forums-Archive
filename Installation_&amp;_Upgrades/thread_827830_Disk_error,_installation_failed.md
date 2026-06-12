---
title: "Disk error, installation failed"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by maxbear on 2008-06-13
Hello,

I got a Seagate 160GB sata disk (has been RMA). This disk installed server edition before. And Now I want to totally reinstall to ubuntu desktop. But after I select use entire drive to install ubuntu, it just said there might be problem or damage on your disk, asked me to manually config the partition. But even I did that, the installation process still failed. 

I tried several things:

- use seatool (seagate harddisk tool) to scan the drive, long and short test, no problem.
- low level format the drive.
- fix mbr
- move the drive to a windows machine and format there, windows also said they can't format the drive.
- try to install windows on this drive, when it come to format the drive, it got failed as well.
- then I use Acronis Disk Director to format the drive, it can be format and I can move files to that drive.
- then I install ubuntu again, and still got failed.

The strange thing is seatool doesn't report any problem about the  drive. But why ubuntu and widnows said the drive might be damage? Any idea? Thanks a lot.

---

### Post by dstew on 2008-06-13
Try this. Boot an Ubuntu Live CD, and open a terminal window (Applications --> Accessories --> Terminal). On the terminal command line enter```
sudo fdisk -l
```Post the output to the forum.

If the fdisk output shows that there are partitions on the drive, you can use the fsck program to see if the file systems are intact. If you want to check the /dev/sda1 file system, use the command```
sudo fsck -V /dev/sda1
```The -V option gives you a verbose output. If this reports errors, post the output to the forum.

It is also possible that the operating systems are having trouble accessing the drive due to driver software not interacting with the drive interface properly. We can look at this after you try fdisk and fsck.

---

### Post by Gonzalo_VC on 2008-06-13
[COLOR="Blue"]Hi, pals!
I deleted a Ubuntu distro from my laptop because I was going to change the partitions (enlarge the "\" )to install a new one.
But now the laptop does not reboot, because grub is still there and I can't modify the partitions from the live-CD of Ubuntu.

Neither can boot the laptop with a WindowsXP CD because it ask me for a drive A (diskette) that it doesn't have.

How can I format the MBR from a live-CD of Linu!!??
THANKS![/COLOR]

---

