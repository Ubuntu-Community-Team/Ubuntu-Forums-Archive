---
title: "Windows can't shrink volume?"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by Mr_Burkes on 2011-10-18
So I have a new Acer Laptop, and was going to run Ubuntu on a separate partition from Windows 7. My HDD is 591GB, but it only lets me shrink to 245GB. I ran a disk defragmenter, and I did a chkdsk and everything is okay. What could be causing the problem? :(

---

### Post by stracky on 2011-10-18
I had the same problem when I tried to shrink my partition for the first time.

First of all, Windows doesn't like it when you mess with it.  So it prevents you from shrinking the partition too far.

There is also the chance that your Windows partition simply has 245 GB of data on it, so obviously you can't shrink past that

If that isn't the case, and Windows is just being screwy, you need to resize the partition from *outside* Windows. (Using an Ubuntu Live CD).  Post back if you need help with this.


Also, 346 GB should be plenty to run Ubuntu.  I've only used 26 GB of my 75 GB partition.

---

### Post by stracky on 2011-11-28
If you have solved your problem, it is asked that you mark the thread as [SOLVED] using the thread tools at the top of the page.

Thanks!

---

### Post by turboscrew on 2011-11-29
Also, runnin windows tends to use a cluster at the end of partition. That makes the shrinking impossible.

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

There are defrag/consolidating programs that could help.
What were they... Auslogics, ultra defrag, smart defrag, ...
(First with Auslogics then with boot time drefrag.)

---

### Post by Hakunka-Matata on 2011-11-29
The OP states in Post #1 that he is running Windows7.  
The hyperlink you post is applicable to Windows Vista only.
It's OK to shrink the ntfs partition of a WindowsXP installed system using gparted.  
It's NOT OK to use **gparted **to shrink any Windows partition containing Windows OS: VISTA or Windows7.

This post is information only, no judgements intended or implied

---

### Post by ottosykora on 2011-11-29
> **Mr_Burkes said:**
> So I have a new Acer Laptop, and was going to run Ubuntu on a separate partition from Windows 7. My HDD is 591GB, but it only lets me shrink to 245GB. I ran a disk defragmenter, and I did a chkdsk and everything is okay. What could be causing the problem? :(

once on a small computer with similar big hard drive and nothing then rather 'empty' w7 installed, I managed to shrink the partition to half, then run all this checkdsk and so on, until all was stable again and surprise w7 had let me to shrink again to half, then again run all this chkdsk etc and all become stable and in fact something like 1/4 of the initial size.
Must be some special strategy behind it, no idea , but it could be made so people do not cut all in one go to minimum and then have no space for swapfile or what.

---

### Post by BC59 on 2011-11-29
Well I did once the resize to a Windows 7 partition, using gparted, because I needed desperately space.

The Windows spend 1 hour checking the system and finally started normally.

Sometimes you need luck.

---

### Post by Hakunka-Matata on 2011-11-29
> **ottosykora said:**
> once on a small computer with similar big hard drive and nothing then rather 'empty' w7 installed, I managed to shrink the partition to half, then run all this **checkdsk** and so on, until all was stable again and surprise w7 had let me to shrink again to half, then again run all this chkdsk etc and all become stable and in fact something like 1/4 of the initial size.
Must be some special strategy behind it, no idea , but it could be made so people do not cut all in one go to minimum and then have no space for swapfile or what.

**Reminder:**
Windows chkdsk /f or /p needs to be run repeatedly until it reports no errors fixed.  Or is it /f and /r?

look at some posts by "oldfred", he's Ubergood explaining these sorts of utilities.

---

### Post by lisati on 2011-11-29
+1 to the Windows shrink tool usually being better than using gparted for Vista. I've seen elsewhere in this forum that weird things have been known to happen. I've even had it happen myself where the copy of Vista on the laptop I'm using now mysteriously got broken after using gparted. I still haven't figured out how or why, and haven't bothered investigating since it was easily fixed.

---

### Post by Mark Phelps on 2011-11-29
Anybody else notice that this was a "one post OP" ... who never replied or returned after the original post over 6 weeks ago?

I think we're all just messaging one another here.

---

### Post by RawG on 2012-02-27
Thanks for the info!
I have question regarding shrinking of partitions in Windows 7 !

I am unable to recover windows due corruption of OS. I have only single partition in which Win 7 is installed. Can I somehow shrink the partition to create Unallocated space to perform a parallel installation to save my data?

If yes, I wud really appreciate the answer ....

---

