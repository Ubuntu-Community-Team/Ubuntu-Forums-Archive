---
title: "Is it normal 4 fsckdsk 2 be running automatically at startup?"
date: 2010-01-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kevpan815 on 2010-01-10
Is it normal 4 fsckdsk 2 be running automatically at startup?

---

### Post by ranch hand on 2010-01-10
You are asking a lot of native english speakers with that type of language.  There are folks here who are not native english speakers and you are asking way too much of them by replacing words with numerals.  Please do not do that.

fsck will run every so many mounts on any OS.  If yours is running on every start I would boot recovery mode and see if there is some fault that is causing it to run that often.  I think on 10.04 the thing is set for every 28 mounts.

This does mean that if you access your /home or / partition through nautilus from another OS or chroot in to update the partitions will have been, over time, mounted a different number of times.  Therefore it is possible that a check would be run on more than one boot up in 28 boots.

Seeing how all of the OS' get auto mounted on every install I have it is possible that little used OS' will run fsck every time I boot to them because they were mounted in every other OS that I ran (I currently have 12 on my test platform).

---

### Post by cariboo on 2010-01-10
@kevpan815, please check out the [Forum Do's & Don'ts]("http://ubuntuforums.org/showthread.php?t=885580").

Fsck checks the hard drives on every boot to see it is time to run a full fsck scan. If it isn't needed, the boot process continues on, if it is needed then a scan is run.

---

### Post by VMC on 2010-01-10
Check your fstab, field six should be a "1",  I believe.


note:
The reason RH complained about word usage is something I would have never thought about - searching:
[SIZE="1"]Try not to circumvent the language filter using *'s and numbers etc[/SIZE]

---

### Post by ranch hand on 2010-01-10
If you are on 2 partitions then your fstab field 6 should indeed read "1" for your / but your /home should read "2".

---

