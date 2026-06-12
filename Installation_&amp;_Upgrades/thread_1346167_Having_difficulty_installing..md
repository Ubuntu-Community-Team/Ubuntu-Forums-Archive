---
title: "Having difficulty installing."
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by drowelfx on 2009-12-04
I downloaded Ubuntu 9.10 today in an attempt to access files on my laptop.
Last night, my laptop suddenly stopped working and could not boot after restarting. 
After burning my Ubuntu disk, I could not find a way to run the OS from the disk, so I attempted to partition the drive in order to install it.

I realize that you are supposed to defrag before partitioning, but I cannot access any of vista, so I just went for it. Bad idea, the partition froze, and I had to shut the computer down.

Now, the program will not let me partition the drive, and I'm not sure that it will even install.

What do I do?

---

### Post by u.b.u.n.t.u on 2009-12-04
Welcome to the Ubuntu community.

What was the original operating system on your laptop?

When you start your laptop, at what error message or event does it stop working?

---

### Post by drowelfx on 2009-12-04
It was originally a vista.

Usually what happens is, after starting, it will go to the loading screen and stay there until either the end of time or a BSoD, it then tells me there is a problem communicating with a device with status: 0xc00000e9
I've tried running startup repair, but the loading screen gets to ~15% before freezing and taking me to the same error screen. Safe mode also freezes while loading.

---

### Post by u.b.u.n.t.u on 2009-12-04
What was your computer use prior to the error? In other words, what if anything did you do just prior to Vista becoming corrupted?

---

### Post by drowelfx on 2009-12-04
I hadn't installed anything major in the days prior to the crash, and just before the crash, I was only working on a powerpoint for a class (pretty much the only reason I for needing a partition).
There was one odd thing that happened right before the crash. When I went to turn the computer on, I discovered that despite the lid being closed for almost a full day, the computer was still not in either hibernation mode or sleep mode. At this point, I just want to retrieve the powerpoint if it is still possible.

---

### Post by u.b.u.n.t.u on 2009-12-04
> **drowelfx said:**
> At this point, I just want to retrieve the powerpoint if it is still possible.

A live CD should enable you to access the HDD. Then it just becomes a simple matter of transfering files to a usb pen.

I am still somewhat unclear about this. You have mentioned Vista as being the original operating system. So is that the only operating system on the laptop or is there another?

Have you partitioned your laptop HDD?

---

### Post by drowelfx on 2009-12-04
At this point, Vista is the only OS on the system.
I attempted to partition the harddrive through the Ubuntu install disk.
My original plan was the "test" ubuntu at first to see if I could save any data or fix any problems. Unfortunately, I couldn't figure out how to run from the CD ( I was under the impression that you could do this, but the only options were Install Ubuntu, Check disk, Test memory, Boot from first, and Rescue a Broken System.)

---

### Post by u.b.u.n.t.u on 2009-12-04
> **drowelfx said:**
> At this point, Vista is the only OS on the system.

So the priority is to get Vista working.

> **drowelfx said:**
> I attempted to partition the harddrive through the Ubuntu install disk.

Did you create any partitions with Ubuntu?

Do you have your Vista CD?

---

### Post by drowelfx on 2009-12-04
I do not have an Vista disk.

I tried to partition through the install disk, but the process was frozen at 0% for over an hour, so I was forced to shut the whole computer down.

Now when I try to partition, the background of the install turns red and says that it will not work

---

### Post by u.b.u.n.t.u on 2009-12-04
The problem is trying to determine what is actually wrong.

If the problem is only the boot loader, then that can hopefully be fixed.

If the problem is corrupted Vista system files then that becomes a case of data rescue, reformat the HDD to ensure NTFS integrity and reinstall Vista.

Have you ever backed up Vista with their backup program? That is, have you used Vista to backup Vista onto your HDD?

You need a Vista CD!

Have a careful read of the following and then please let me know what you think.

"Recovering the Vista Bootloader with EasyBCD"
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD)

---

