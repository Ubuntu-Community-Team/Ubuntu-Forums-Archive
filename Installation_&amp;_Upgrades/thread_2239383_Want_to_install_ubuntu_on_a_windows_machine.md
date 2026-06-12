---
title: "Want to install ubuntu on a windows machine"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by RedRat on 2014-08-13
OK, my existing HP computer seems to have crashed and I am going to replace it (it is roughly 7 years old and I got my use out of it). What I want to do is get a new computer, preferably an HP with Windows installed. I want to install Ubuntu on as my prefered operating system. I will then fall back on Windows where that is the only place I can run certain programs. 

My problem: I have seen here in the forum several mentions of settings either UFI or EFI or something to that effect. What are these? I have seen the acronyms but not seen them explained. Which is preferrable?

Further, I am not necessarily interested in running Win8 but could get along with Win7, any opinions about that in terms of compatibility with having a second partition with Ubuntu on it??

---

### Post by bradwilliams923 on 2014-08-13
I have no personal experience with Windows 8, but can attest that Windows 7 will run just fine side-by-side with Linux, provided that Windows is installed into its partition first. Initially there were some problems with reaching the bootloader with Windows 8 computers, but I believe those issues have been resolved. Perhaps someone more knowledgeable can elaborate on that.

---

### Post by kansasnoob on 2014-08-13
I haven't kept up with the latest tech so I'll have to leave that to others but I want to make you acutely aware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

I know it can be worked around but wanted you to be aware ;)

---

### Post by guccimucci on 2014-08-13
I have a laptop which is 1,5 years old (UEFI) and it had Win 8 preinstalled. I just completed my dual-boot couple of days ago and no problems occured. 

Important is to install Win 8 before Ubuntu. I followed a guide I found in here [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) - I think it'll work with win7 too (should be even easier). Also you have to turn off fast boot and secure boot, which are mentioned in the link I added. I personally skipped the first 3 chapters as I didn't need a backup and I used manual partitioning while installing Ubuntu (worked fine). I left my Windows around 100GB and moved most of my hard drive to Ubuntu. Also liked the partitioning guide in there, because I now have a /home partition for programs, pictures, movies etc and system on a different partition, so whenever I want to change my Ubuntu version or try Mint for example, my personal files and configurations will remain.

Most of the guides I found about this issue seemed to be legit. I recommend to read a lot before doing it. :)

---

### Post by ajgreeny on 2014-08-13
I think any new machine you buy these days is likely to use UEFI. This is the modern equivalent of the old BIOS, and it removes a lot of the restrictions that legacy BIOS gave, such as a maximum number of four primary partitions, or three primary plus one extended partitions, the latter of which can have a large number of logical partitions inside.

Partitions on a UEFI machine must be formatted using a GPT partition table, but that will all be dealt with by the installer in the medium you use to install, whether DVD or USB.  You must, however, boot the installer in the manner you want to install, which if you have Win8 will almost inevitably be UEFI.

Have a good long read through [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") which shuld tell you a lot more about the whole story and how to deal successfully with it.

---

### Post by RedRat on 2014-08-14
Jeesh, things are complicated. I makes me wonder if I should just build a box, order a copy of Win7 and install in legacy mode. From the various comments and here ([https://help.ubuntu.com/community/UEFI#SecureBoot](https://help.ubuntu.com/community/UEFI#SecureBoot)) if does appear that the Ubuntu installer has problems that might not have been resolved yet. I really only need Windows for a a couple of graphics/photo programs that are out there. Ubuntu does not have any such programs currently available, most that exist are just too buggy to be useful. 

At the end of the day, the take home lesson here is to have a copy of Windows install disks in hand just in case that Windows partition is wiped I guess.

---

### Post by oldfred on 2014-08-14
Even if you have a Windows 8 computer with gpt partitioning, Windows 7 installed in BIOS mode does not correctly convert drive from gpt to MBR(msdos) parititioning. It leaves backup gpt partition table. Then Linux tools see both MBR & gpt and get confused on what you really want.

You can install Windows 7 in UEFI mode, but some DVDs only work in BIOS mode and you have to copy to flash drive & update.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
    
And some of the high end laptops are Ultrabooks with dual video which adds complications and Intel SRT which is seen as RAID which prevents grub from installing correctly.

HPs and Sony only boot Windows. They modified UEFI internally to only boot UEFI entry with Windows. That is not UEFI standard and Ubuntu has a position paper against that. But there are mulitiple work arounds that many different users have used.

---

