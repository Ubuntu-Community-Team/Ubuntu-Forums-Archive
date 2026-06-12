---
title: "Does it matter where I install Ubuntu?"
date: 2021-07-18
forum: Installation &amp; Upgrades
---

### Post by juntjoo2 on 2021-07-18
[http://imgur.com/a/ddzTmAY](http://imgur.com/a/ddzTmAY)

So as you can see I have two partitions I made a long time ago I'm guessing for when I set my system up for a dual booting with windows.  And I set aside the large one for files. So idk how it got here exactly but:

1) does it matter where the partition is that I install the OS? And... 

2) how would I combine or edit / rearrange the two partitions to my desire?

3) I might or might not want to install windows but the option later would be nice. Will I be able to later? 

Thanks!

Edit:

Latest situation. How do I combine these partitions?

How to combine partitions https://imgur.com/a/uU8xY60

---

### Post by Impavidus on 2021-07-18
1: No, it doesn't matter.
2: Partitions cannot be merged or split. Partitions can be deleted, new partitions can be created in unallocated space, partition can be shrunk (creating unallocated space) and partitions can be expanded into unallocated space.
3: You can first install Ubuntu, then Windows, but Windows has a habit of damaging Ubuntu when Windows is installed last. This can usually be fixed, but may take some effort.

Further, Ubuntu can only be installed in a Linux partition (like ext4) and Windows can only be installed in a Windows partition (NTFS). It's recommended not to use unsupported Windows releases (everything before Win8) and Win8 and up really want to be in UEFI mode on a GPT partitioned drive, especially when dual booting with Ubuntu. Ubuntu and Windows must be in the same mode. On an MBR partitioned hard drive (which is not what you should use), you can only have 4 primary partitions or 3 primary and a number of logical partitions, but there can't be any primary partition between two logical partitions.

---

### Post by juntjoo2 on 2021-07-18
I'm guessing my hard drive is MBR partitioned, as I'm having "MBRboot" errors with my Windows 7 stall. But I still have valuable data on the drive. Would I be able to change it from MBR to whatever you recommend? What would that be BTW? Or if I don't do a dual boot is MBR fine for just my Ubuntu?

---

### Post by juntjoo2 on 2021-07-18
I guess you cannot expand a partition into empty space on the other other side of an adjacent partition right? I'm trying to get that empty space to the right of my NTFS partition over to the left side

---

### Post by juntjoo2 on 2021-07-18
SQUASHFS ERROR [https://imgur.com/a/GUhwZFp](https://imgur.com/a/GUhwZFp)

Just tried to install after setting the partitions and got this squash error? What's this about?

---

### Post by tea for one on 2021-07-18
It is not easy to follow what you are trying to do?

Do you have back-ups of your data?
Do you want to use Windows 10?
Do you want to use Ubuntu?
Do you want to dual boot Windows 10 and Ubuntu on one disk?

---

### Post by juntjoo2 on 2021-07-18
Well at this point it looks like I want to start fresh and use a SD card in place of my Ubuntu CD as it keeps failing during install. I'm guessing it's the hardware, this external disc drive. I can copy an ISO image to SD card right? If so point me in the right direction would you? I wanted to have the option to have  dual boot system if I could but wither way I just need to get this laptop going and I'm trying to get Ubuntu on it for now. Windows is another challenge, windows 7 as I have a copy, just need a new serial number or something  windows issue.  Anyway, can I put a install file on SD card?

---

### Post by tea for one on 2021-07-18
I notice that you failed to answer my question.

Do you have back ups of your personal files?
If you do not have back ups, can we assume that your data is unimportant?
Then we can proceed?

As a side note, Windows 7 has reached end of life is is now unsupported.

---

### Post by juntjoo2 on 2021-07-18
No, my data is important but I'm not touching that partition. Right now I am downloading the Ubuntu installation and it looks like I can put it on an SD card. And yes, windows 7 they're not helping with, although they did a couple years ago give me an install file/image but I guess not any more

---

### Post by oldfred on 2021-07-18
If you do not have backups, your data is not important.
Users often make mistakes on installing, and many from Windows do not understand difference between a drive & partition.
And you cannot just copy an ISO to a flash drive, but have to install it, so it is extracted & converted to be bootable.
Many systems do not directly boot from SD cards. You may be able to put a SD card into an adapter so seen as a flash drive as newer systems will boot flash drives.

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by tea for one on 2021-07-18
If  you do not have back ups of your important data, then it would be irresponsible to attempt to install another operating system. 

The installation will adjust your partitions and, just imagine, unexpected power failure ....................

Please back up first.

---

### Post by juntjoo2 on 2021-07-18
Are you saying if I try to install Ubuntu on a particular partition it will mess with my other 350+gb ntfs partition?

---

### Post by TheFu on 2021-07-18
> **juntjoo2 said:**
> Are you saying if I try to install Ubuntu on a particular partition it will mess with my other 350+gb ntfs partition?

No. They are saying that new users often make mistakes and wipe partitions accidentally.  The boot areas are shared and those will be touched by every OS booting using UEFI. That's part of the standard and expected.

And in general, it is best to install any Linux into multiple partitions, but we can't know your needs for today, next month, Xmas, and the next 2+ yrs. Heck, I don't know my own needs for those timeframes.  In general, I install into 3 partitions and 4 logical volumes.  The partitions are
[LIST]
[*]/boot
[*]/boot/efi
[*]a partition to hold all the LVM PV, VG, and multiple LVs for (/, /home, /stuff, swap)
[/LIST]
That assumes only 1 storage device. If I have multiple SSDs/HDDs, then storage gets more complex.

You can do whatever you like.  But we all think you should backup anything you don't want to lose BEFORE doing anything else. That comes from experience. I've certainly wiped the wrong partition before during an install. I'd bet everyone here has too.  Fortunately, I haven't done that in well over 20 yrs, so it isn't a worry for me today.  I still make mistakes and do dumb things, however.  Almost daily.  Backups have saved me a few issues this week, not system-wipe level issues, but I have restored a few files that were deleted by accident.

---

### Post by yancek on 2021-07-19
The image in your initial post shows that you have a 76GB swap partition.  In your case, 4-8GB would be more than enough so that is a lot of wasted space.  Also, the swap partition is a logical partitiion.  The only primary partition you have is sda1 which is in ext4 (Linux) format.   Your only windows partition is sda5 which is also a logical partition.  Windows will not boot unless you have its boot files on a primary partition which you do not have.  Is that partition (sda5) just a data partition?  You could shrink sda1 and create another primary partition there for a boot partition if you are familiar with installing windows 7.  Pretty unusual partition set up. 

I'd suggest that you back up your personal data and install windows (if you want) then install Ubuntu.  I'd also suggest you do more reading on using and installing Ubuntu before you begin.

---

