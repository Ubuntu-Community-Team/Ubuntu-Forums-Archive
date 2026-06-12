---
title: "Partitioning Windows XP &amp; Ubuntu (Dual Boot)"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by Mokha on 2006-08-28
Hello,

Thanks for all the helpful suggestions that all of you have been posting. Well let me tell you a bit about my Linux experience.
I first bought Xandros, the problem was that it did not recognize my ethernet card. So I went to a Linux Expo in my area. Got Fedora Core 5 & Ubuntu version 6.06. No luck with Fedora, it too didn't recognise my ethernet card. But Ubuntu was a success. I managed to partition my hard drive in the following order.
C: NTFS (Windows XP)
Linux Ext3 (Ubuntu Installation)
Linux Swap (For Ram)
E: FAT32 (As this link suggested_http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/
)
Now I am wondering E:FAT32 is empty, do I need this? Cause I could use the Space for something Else. What is the purpose of this FAT32 Partition.
The Current allotment of my Partitions are as follows.
C:NTFS (Windows XP): Size:21GB Used: 5GB
Linux EXT3: (Ubuntu): Size:14GB Used:2.3GB
Swap Space: (For Ram): Size:1.2GB
E:FAT32: Size: 5.15GB Used:10.1MB
F:Multimedia: Size:10.14GB Used: 53.8 (Currently Empty)
Gata: Size:5.18GB Used: 28.2MB

My question is do I need to keep this E:FAT32 Partition or can I use it for other things such as increasing my F: Multimedia Partition by adding additional capacity to it & getting rid of FAT32.
Any help would be appreciated. I am a beginner to Linux (Ubuntu)

Thanks
Mokha

---

### Post by JimmyJazz on 2006-08-28
No, you do not probably need the FAT32 parition.

---

### Post by Mokha on 2006-08-28
Are you sure?

---

### Post by nobar on 2006-08-30
The HOWTO that you referenced used the FAT32 for exchanging some setup files between Linux and Windows.  There are other ways that you can do this (like using a thumb drive or email).

The nice thing about FAT32 is that both Linux and Windows can use it -- so it's good for sharing files.  I have a FAT32 partition that I put music files and pictures on.  Then I can get to those from either operating system.  If you don't want to share a lot of files between the two operating systems, there is probably no need to have the FAT32.

---

