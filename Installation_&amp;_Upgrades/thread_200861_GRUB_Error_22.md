---
title: "GRUB Error 22"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by deat on 2006-06-20
I installed Linux as a dual boot with WinXP Media Center Edition 2005, and it all went well until I tried booting Linux. It stalled on the "Mounting root filesystem" or something. So I played around, trying to figure out why. Every option I choose, Linux stalls on a command line that is similar to: "cannot allocate resouces with region 3" Then I decide to delete the partition and start over. I go into windows and delete it, and boot up again intending to redo it. Linux still freezes at the same spot. So I give up for the night thinking I'd do it the next day. I restarted the PC and got a GRUB error. It says it cannot load, then it says "error 22" How do i completely get rid of it to start over, even with linux unable to boot, and my windows unable to load. I cannot reformat my computer, because my win files are extremely important.

Any suggestions?
Thanks!

---

### Post by Heretic on 2006-06-20
Not sure if this will help, but you can use the Windows install cd to repair the MBR, booting windows again. [Basically gets rid of GRUB]. As this may not be a nice option for you, i had to use it to recover and boot into Windows again.

[http://ubuntuforums.org/showpost.php?p=1159414&postcount=8](http://ubuntuforums.org/showpost.php?p=1159414&postcount=8)

---

### Post by incubus on 2006-06-20
That's fast! I was going to suggest fixmbr as well.

Probably it's a good idea to google for that error or search this forum.  Also, make sure your Ubuntu CD was recorded correctly and that your hard drive is healthy.  After you're sure your windows files are safe (backup), give Ubuntu another try.

Funny, I had a similar problem with my system with windows media center (it's a DELL). I had to manually reinstall GRUB not only in the MBR but also in the boot partition, and that problem happened for apparenty no good reason.

incubus

---

### Post by deat on 2006-06-20
I'd love to use the Windows install CD, if I had one. I only have recovery disks, but if I use those, it'll reset everything to how it was when I first got the PC, which means I'd lose my files. :-/

---

### Post by tonyr on 2006-06-20
It looks to me like you can use the recovery cd to repair the MBR. Look at
[this]("http://support.microsoft.com/kb/314058/") article.  It describes how to set and use the Windows Recovery Console.  
The Windows MBR can be repaired using the **fixmbr** command.

---

### Post by confused57 on 2006-06-20
I believe you can use a Win98 boot floppy and type in:  fdisk /mbr
This boot floppy may work:
[http://www.bootdisk.com/](http://www.bootdisk.com/)

There's a thread I can't find at the moment that discusses this very issue, fixing XP mbr with the Win98 boot floppy.  Don't try it yet, just wanted you to be aware of a possible alternative,  I'll try to find the link:
[http://www.ubuntuforums.org/showthread.php?t=180607&highlight=windows+boot](http://www.ubuntuforums.org/showthread.php?t=180607&highlight=windows+boot)

Your grub 22 error could be something to do with pointing to the wrong partition on your hd to boot Ubuntu.

You might want to boot up with a live cd, open a terminal:

```
sudo fdisk -l
```
or, with the live cd it may only be:
```
fdisk -l
```
The -l is a lowercase "L"
This should show the partitioning of your hd.

You may just want to "try" reinstalling" Ubuntu(maybe trying a different install cd) onto the partition you have set aside for it, and make sure to install grub to the mbr...or you could attempt to restore grub.
[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---

### Post by tonyr on 2006-06-20
[Here]("http://www.uruk.org/orig-grub/errors.html") is a list of GRUB errors.
Good Luck interpreting #22.

---

