---
title: "Partition resizing problems"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by College_Trained on 2008-01-02
Here's the deal.
I'm trying to install Ubuntu 7.10 but I need to resize my windows partition to do so, so I can dual boot.
The problem is that even if I use GParted, QTparted on the Ubuntu 7.10 livecd, or the GParted livecd, the partition will not resize.

I have attatched a screenshot of the error I get when trying to resize using GParted from the Ubuntu 7.10 livecd.

My computer specs(that I know of) are:
IBM Thinkpad T60p
80GB Hard drive
80GB Windows partition

Any help would be greatly appreciated as I hope to have this running by mid-January when I go back to college.
Thanks,
Brendan

[[IMG]http://img110.imageshack.us/img110/4049/gpartedscreenshotxh6.th.jpg[/IMG]](http://img110.imageshack.us/my.php?image=gpartedscreenshotxh6.jpg)

---

### Post by sciencewhiz on 2008-01-03
how much space is free in the partition? Have you defragmented?

---

### Post by College_Trained on 2008-01-03
I have defragged and there is about 20+ gigs of space available.

Thanks to anyone that can help me.

---

### Post by logos34 on 2008-01-03
If it's Vista you have, then you need to shrink it with Vista's own built-in disk management tool.

---

### Post by College_Trained on 2008-01-03
It's not Vista. It's Windows XP Pro SP2.

---

### Post by sciencewhiz on 2008-01-03
What happens if you don't do such an aggressive resize, say 5 gigs?

---

### Post by erfahren on 2008-01-03
run Windows check disk on that partition 2 or 3 times (actually you should do that before defagging, but no one ever does!)

in my experience, all the errors won't get fixed the first time through (you can see the results of chkdsk in the Event Viewer under a "Winlogon" entry)

---

### Post by erfahren on 2008-01-03
you also might try running JKDefrag - it moves everything to the beginning of the drive better than the Windows one does (it's a standalone .exe and free of course): [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)
- disable as many running processes as you can when running it (antivirus, firewall, etc.)

- you said that you have ~+20 GB free? - so you have about 50GBs of data on there? you do want to back that stuff up if it's important - and since you'd have it backed up, clear some off to create some more room for the partitioner to work with.

then chkdsk it, and defrag it

---

### Post by College_Trained on 2008-01-03
This is the screenshot I got when I tried resizing it by only 10 GB.

---

### Post by lgambett on 2008-01-03
Defragging alone is not sufficient, it is necessary also to run Scandisk setting the fix error option. Windows performs this operation at the next reboot, because it is necessary that the disk is not in use.

---

### Post by College_Trained on 2008-01-03
This is what I got when I tried resizing by 5GB.

---

### Post by logos34 on 2008-01-03
Another possibility:

> 

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

"One problem you may encounter in defragmenting a Windows disk using the Windows Defragmenter is "unmovable files" (the green bars) located in inconvenient locations (on the right side of the display, near the end of your disk). The two most common unmovable laptop files are the Windows operating system paging file (pagefile.sys) and the hibernation file (hiberfil.sys), which stores the system state when the XP operating system goes into "hibernate" mode. An easy solution is to temporarily remove these files, then reinstall them after you've resized the NTFS partition. If you need help with this, see my eQuickFixes.com blog entry "Moving the Unmovable: Windows Disk Defragmentation Strategies."

---

### Post by College_Trained on 2008-01-03
I DID IT! I don't know how but I did it. I ran the 5 step chkdsk and then ran jkdefrag until it finished "Zone 2." I then quickly ran my Auslogics Disk Defrag and then finally the Windows Defrag. I restarted into the Ubuntu livecd machine, sudo gparted, and did a test for 1GB. To my surprise IT WORKED! So I then resized it for 20 like I originally wanted.

Thanks everyone for your help.

---

