---
title: "Have home folder from 8.10; can I access this in 9.04?"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tom66 on 2009-04-08
I have a separate (~100GB) home partition from 8.10 (it's a separate home partition). If it's possible, how can I use this partition as my home partition in 9.04?

Thanks, Tom

---

### Post by Penguin Guy on 2009-04-08
I believe if you have set the moutnpoint of that partition to /home/username then it should use that partition by default in Jaunty. Please wait for further verification before upgrading though.

---

### Post by okey666 on 2009-04-08
When you install 9.04, choose advanced partitioning when you install, select your home, click edit, and tell it to mount it as /home.

---

### Post by Lunx on 2009-04-08
> **tom66 said:**
> I have a separate (~100GB) home partition from 8.10 (it's a separate home partition). If it's possible, how can I use this partition as my home partition in 9.04?

Thanks, Tom
Can you see the other partion when you look in your places menu? Should be able to mount it by right-clicking. It will prompt you to enter your password, then it will put the drive icon onto your desktop and you can access as normal through nautilus

---

### Post by Lunx on 2009-04-08
Sorry, think I misread the OP

---

### Post by kpkeerthi on 2009-04-08
Are you dual booting 8.10 and 9.04 or just installing 9.04 over 8.10?

---

### Post by tom66 on 2009-04-08
I have already installed Jaunty and am enjoying it. I set up the mount point for the partition as /home but it doesn't seem to take effect. I can't see the partition at all in Places - only my 8.10 root partition is visible. I know my data is still there, because I can boot 8.10 fine and everything is there.

---

### Post by mcduck on 2009-04-08
> **tom66 said:**
> I have already installed Jaunty and am enjoying it. I set up the mount point for the partition as /home but it doesn't seem to take effect. I can't see the partition at all in Places - only my 8.10 root partition is visible. I know my data is still there, because I can boot 8.10 fine and everything is there.

If the partition is mounted as /home (or actually anything else than a directory inside /media) it won't show in the Places menu or desktop.

If you mount a partition as /home, you access it at /home and all your user home directories are in that partition. It really is that simple.

---

### Post by kpkeerthi on 2009-04-08
If you are dual booting, I suggest you keep you $HOMEs separate. 

You may create a separate partition for DATA and share it with multiple distros.

---

