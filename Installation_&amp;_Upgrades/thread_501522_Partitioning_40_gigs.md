---
title: "Partitioning 40 gigs"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by drudy on 2007-07-15
My previous install was up and running but I ran into problems and have decided to redo it.  This time I'd like to include a /home partition, which I didn't know about before.  I need some recommendations on partitioning schemes for a 40 gb hard drive.

In addition, could someone explain the purpose of the /tmp, /usr, /var etc. mount options and whether they should get their own partitions as well.  I'm new at this whole thing, Thanks for understanding.

---

### Post by Wim Sturkenboom on 2007-07-15
My rule for swap is 2x memory with a max of 1GB
10GB for / (if you install a lot of additional software, make it a big bigger)
rest for /home

Not sure of all other directories (mountpoints); on a desktop there is usually no need to separate them.
/var contains logs, printer spool directory etc
/tmp is just a directory where temporary stuff goes
/boot will contains the boot stuff

---

### Post by drudy on 2007-07-15
Thanks for the help, but there are other problems.  I prob did something wrong...

I did ~10 for /, <30 for /home, and ~.75 gig for swap.
But now I'm getting GRUB error 15, and I am unable to push esc for recovery mode.

What can I do on the live cd.  I tried unsuccessfully to reinstall grub, maybe I'm doing that wrong too.

---

### Post by drudy on 2007-07-15
I'm reinstalling with a guided partitioning, and if that works, I'll do the instructions for adding /home.

(This didn't work, still Error 15)

---

### Post by merlinus on 2007-07-15
You might try SuperGrub, which can boot ubuntu and restore grub.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by drudy on 2007-07-15
thanks, I'm trying it out

---

### Post by drudy on 2007-07-15
so no luck so far with superGRUB.  If it can't find the MBR, is that a hint something went wrong in the installation?

---

### Post by merlinus on 2007-07-15
Just to be clear --

Did you reinstall?  Or are you trying to rescue your original installation?

-merlin

---

### Post by drudy on 2007-07-15
Yes, I reinstalled, not attempting any recovery.

---

### Post by merlinus on 2007-07-15
Have you tried booting from the live cd into recovery (or restore) mode?

How did you try to reinstall grub?

-merlin

---

### Post by drudy on 2007-07-16
I used the instructions [here]("http://ubuntuforums.org/showthread.php?t=224351")

sudo grub, then

find /boot/grub/stage1

resulting in 
Error 15: File not found

---

### Post by drudy on 2007-07-16
In the meantime, I'm reinstalling with a manual partition that includes formatting them, which I didn't do before.

---

### Post by merlinus on 2007-07-16
OK.  Hopefully that will be successful.  

Let us know, and good luck!

-merlin

---

### Post by drudy on 2007-07-16
Up and running and reupgrading and reupdating.

Thanks again!

---

