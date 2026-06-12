---
title: "Completely and Utterly Failed Dual Boot"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by Noodels on 2008-01-12
Okay, No-one can help me on irc, and my computer is completely disabled. Originally I had set out to do a dual boot, It shouldn't be too hard I thought, big mistake. Firstly I found that the livecd crashed frequently. After several tries it seemed to be fairly stable, so I continued with the install. I managed to partition off 90Gb of my hard drive for ubuntu, and 70/60Gb for windows (can't check, computer doesn't work). It was going well, it got about 85% through the install before crashing. Upon trying to boot the computer without the livecd, it said there was no boot sector. So I put the livecd back in, tried to try again, after several tries I didn't even manage to complete the preparing to install bit. I was directed to an alternate ubuntu cd that is supposedly less fussy. Over an hour I spent downloading this, having checked the box for alternate cd, only to find that after spending another 20 minutes burning it that I had as a matter of fact created a livecd that crashed even more often.

1) Can someone direct me to a link where I can download an alternate ubuntu disk for burning for an intel computer?

2) Do I need to completely wipe the hard drive now, or just the partition that ubuntu failed to install to. (Please oh god not a windows install...)

3) How do I tie a noose? :(

UPDATE:

I have now reinstalled windows leaving a free partition, All I need to do is run the ubuntu disk, change the free partition to ext3 and install ubuntu on it. Why can't I do it? The live cd keeps crashing! For some reason I am unable to download an alternative, if I ask for one I am only given the live. Is there some alternative link?

UPDATE:

Thanks to irc I was able to find an alternative iso for an alternative cd. The install was successful and windows is operational... As far as windows operational goes anyway. However, now I have run into a new problem, ubuntu on that computer just randomly crashes. Not fun. Last time I tried I didn't get as far as the desktop without the screen blanking out, but usually the screen just freezes. I will look for a solution in the meantime but if anyone could help I'd appreciate it.

---

### Post by tgilber1 on 2008-01-12
1.  You can download the text-based installer by selecting the checkbox underneath "Start Download" @ the following URL: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

2.  No, you do not have to completely wipe out your hard drive.  The Windows partition should be intact as long as you did not erase or format the drive.  What has happened is the MBR [Master Boot Record], i.e. the first 512 bytes of the hard drive has been overwritten.  You should be able fix this problem quickly - I provided a link that will give you some help.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=recover&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=recover&titlesearch=Titles)

hint;  research fdisk /MBR # command to issue from Windows - I think XP and Vista have different process now to recover MBR

---

