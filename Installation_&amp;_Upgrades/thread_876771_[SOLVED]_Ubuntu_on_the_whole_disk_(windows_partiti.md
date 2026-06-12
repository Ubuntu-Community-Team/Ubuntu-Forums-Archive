---
title: "[SOLVED] Ubuntu on the whole disk (windows partition deleted)"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by Steistas on 2008-08-01
Good time of the day to you all,

My younger brother just done one big mistake and is trying to get information back. He has hard drive with 4 partitions (all NTFS), on 1st partition was windows xp, 2nd and 3rd had important information, 4th partition was empty, when he was installing ubuntu, he has chosen the whole disk and without asking me (his english isn't very good) assumed that Ubuntu will find empty partition and install itself into it :). Well, obviously it didn't happened, but all the 4 partitions on the hard drive were deleted together with study and work information. Is it possible to restore the old partitions or at least some information from them and how? Thanks a lot in advance.

---

### Post by iaculallad on 2008-08-01
With that problem, the solution could probably be [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by Steistas on 2008-08-01
Yes, thanks a lot - TestDisk is a GREAT software, it did restore all the information and brother was saying that everything is very simply done.

---

### Post by Cool Surfer on 2008-08-01
Ya it formatted my full c drive too. I have installed different linux distros for a long time, including ubuntus previous versions. But the latest vesion formatted the whole c drive. :(

---

### Post by timjohn7 on 2008-08-01
> **iaculallad said:**
> With that problem, the solution could probably be [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

I installed TestDisk from the repos but cant find it on my Applications or System menu lists.  Where does one find it?

---

### Post by dje on 2008-08-01
> **timjohn7 said:**
> I installed TestDisk from the repos but cant find it on my Applications or System menu lists.  Where does one find it?

it is a command line app, open a terminal (Applications >> Accessories >> Terminal) and type:
```
testdisk
```

hope that helps,
dje

---

### Post by timjohn7 on 2008-08-01
> **dje said:**
> it is a command line app, open a terminal (Applications >> Accessories >> Terminal) and type:
```
testdisk
```

hope that helps,
dje

Thanks... I tried that and get a message saying that TestDisk requires 25 lines? I don't know how to change terminal size to get more lines.  Excuse my noobness.  I also dont want to fill this thread with irrelevant problems.

---

### Post by dje on 2008-08-01
> **timjohn7 said:**
> Thanks... I tried that and get a message saying that TestDisk requires 25 lines? I don't know how to change terminal size to get more lines.  Excuse my noobness.  I also dont want to fill this thread with irrelevant problems.

just maximise the terminal ;)

dje

---

