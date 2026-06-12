---
title: "Hardy ntfs resize"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by Rich43 on 2008-12-01
I heard of a guy in my class that tried resizing his windows ntfs partition with ubuntu's installer.

How stable is this?
Can you all post here if it worked for you or if it didnt please?

---

### Post by zotkop on 2008-12-01
Gparted has worked several times like a charm for me.
But as it's documentations states, it's wise to create a back-up of your files before doing so :)
Just think of the "what if"

---

### Post by pansz on 2008-12-01
As long as you keep your power stable when resizing, it is very stable.

The only failure happens 3 years ago for me, because I had a broken power adapter, the output voltage is not stable enough. After that I've got a new power adapter and everything works till now.

If your data is critical, please backup your data, or backup your power (i.e. UPS).

---

### Post by Mark Phelps on 2008-12-02
The answer to your question is -- it depends ... on whether or not the "Windows" system is XP or Vista.  If the former, no problem; if the latter -- then, maybe. 

Before you try it on a Vista machine, ensure that you have either a Vista DVD or a Vista Recovery CD, because if it fails (and sometimes it does), you will have to boot using a Vista CD/DVD and run Startup Repair to get your Vista boot back.

---

### Post by MiD-AwE on 2008-12-02
If you are resizing or moving a vista partition, expect it to fail, chances are it will not work. Vista will detect that the partion has changed and even if the resize/move works Vista will refuse to work. I have home premium 64bit and have had to reinstall several times while experimenting with what you are asking.

---

### Post by Mark Phelps on 2008-12-03
Mid-Awe:  You shouldn't need to reinstall to fix the broken Vista boot problem.  All you should have to do is boot from a Vista DVD or Vista Recovery CD and run Startup Repair.

If you don't have either of these, go to the Neosmart.net forums.  They provide a link for downloading a Vista Recovery CD that you can then burn and boot from to repair Vista.

Hope this helps.

---

### Post by Herman on 2008-12-03
:) I have been hanging around here and keeping an eye on these forums since around late 2004 or early 2005 when I replaced a virus-ridden Windows 98 in a second hand computer of mine with Ubuntu Warty Warthog, (the very first version of Ubuntu).
Warty Warthog fixed my computer.

Back in those days, there were a few real problems with using Linux apps to resize NTFS or do anything with NTFS, but things quickly improved and ever since the second version of Ubuntu, codenamed 'Hoary Hedgehog 5.04', there have been very few complaints about the Ubuntu's installer's ability to resize NTFS. Scary warnings remained in Ubuntu's own documentation for years in spite of the fact, just to be on the safe side.

Of course, there are always things that can go wrong when doing anything with anything, and I myself, having spent a particularly large amount of time mucking about with partitioning programs and Ubuntu installation disks, have experienced the occasional 'train wreck'. In my case on the rare times when I have had problems, they seem to have been caused by invisible dust or dirt getting on a CD, (even though I handle them carefully), or on the optical lense of a CD/DVD drive, and not programming errors in the software. Cleaning my hardware fixed the problems every time for me, (I happen to live in a dusty climate- the Australian 'outback').
I can well imagine that power supply glitches could likewise wreak havoc if they happened to interfere with an installation in progress.

Still. I don't think that it's possible to say that there are porportionally more reports of people having trouble resizing NTFS that any other file system.
Actually, if we take a minute to think about this, it seems to me that the majority of Windows users would have been using NTFS for the past few years now, so it seems logical to think that there would be quite a lot more resizing of NTFS partitions happening these days. 
Since I've been watching the forums, there have sometimes been up to 1000 new users per day joining the forums, especailly right after a new release, and I don't see that many complaints about difficulties resizing NTFS.

Gutsy Gibbon I think, was the first version of Ubuntu to feature full write support for the NTFS file system,  brought to us by the good folks at [ntfsprogs]("http://www.linux-ntfs.org/doku.php") and I didn't see many problems with that. Before that it was considered experimental and possibly risky to mount an NTFS file system and write to it from Linux.

The main thing we still can't do is run a file system check in an NTFS partition.
There is a program in ntfsprogs called '[ntfsfix]("http://www.linux-ntfs.org/doku.php?id=ntfsfix")', but if you take a few minutes to read about that, you'll see that it isn't designed to run a file system check itself, but merely stimulate Windows to do it next time we boot Windows.

Now, if we read the documentation at GParted Lice CD's website, (the Ubuntu 'Desktop' live CD's installer uses GParted as it's hard disk partitioning program), we can see that it is recommended to run a file system check, CHKDSK, after resizing an NTFS partition with GParted. See this link if you want to check for yourself, [How to Resize a Partition With GParted]("http://gparted.sourceforge.net/larry/resize/resizing.htm").

So you see, it is perfectly normal and expected for Windows to run a file system check after having been resized with GParted or the Ubuntu Live CD. If it didn't happen, I would advise people do do so manually, as a file system check is always good for any file system, and generally wards off evil.
I don't understand why Windows users are so frightened of file system checks.
Most linux users I think, feel that file system checks are a good thing, and we have file system checks set to run at regular intervals. 
In Windows, I'm not sure but I think file system checks are run less often, and are more likely only to be seen after the file system has suffered some mishap and possible damage. No wonder Windows users find file system checks to be alarming, especailly since you're used to running an operating system that uses scare tactics against it's users so much.
 However, in the case of having been resized by Linux, it doesn't necessarily follow that just because a file system check is run, that Linux has damaged the file system, but rather that Linux is being careful with your file system, and has set the 'dirty flag' itself with ntfsfix probably, to induce Windows to run CHKDSK next time you boot Windows.

---

### Post by Rich43 on 2008-12-04
expensive windows software usually moves data to a different part of the drive first and then resizes it to prevent data loss, does linux do this too?

---

### Post by Herman on 2008-12-04
I imagine that GParted probably moves it closer to the beginning of the partition, especially if it will be in the way, yes, I suppose it would have to put them somewhere. In any case, GParted doesn't destroy any files.
There aren't a lot of posts here in Ubuntu Web Forums complaining about it, and I'm sure there would be if that was happening.

We still need to make a backup of our files though of course, just in case. 
But I think it is quite rare these days for people to lose files because of problems resizing with GParted.

---

