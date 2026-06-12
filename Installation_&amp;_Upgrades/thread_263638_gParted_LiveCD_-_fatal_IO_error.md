---
title: "gParted LiveCD - fatal IO error?"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by dema on 2006-09-23
I've downloaded the gParted LiveCD.

When I boot up, select screen size (1024x800px) and dept (24bit) it comes with a "Fatal IO error 104".

I've tried to select an smaller screen size and dept but it doesn't help me :(

Can anybody help me?

---

### Post by meng on 2006-09-23
Only suggestions I have are try running it on another computer, see if it works there. Some funny issues can arise with corrupted downloads or bad CD burns.

---

### Post by dema on 2006-09-23
I've just tried the CD on another PC without problems :(

---

### Post by meng on 2006-09-23
Perhaps you should try another LiveCD with partitioning capability. What are you trying to achieve? If, for example, you just want to install Ubuntu to dual-boot with an existing OS, then the Ubuntu Live (or alternatively, text-only) installer should be able to manage the repartitioning itself.

---

### Post by dema on 2006-09-23
I would like to change the size of my Ubuntu partition. Of course I can't do this from Ubuntu, because the partition is mounted.

Therefore I would like to boot from a CD..can you tell my where to download another LiveCD?

---

### Post by meng on 2006-09-23
I've not used it myself, but what about SystemRescue?
[http://distrowatch.com/table.php?distribution=systemrescue](http://distrowatch.com/table.php?distribution=systemrescue)
otherwise perhaps you could run GParted from an Ubuntu Desktop LiveCD?

---

### Post by ifraser on 2008-04-06
I had a similar problem: here's the solution:

The Fatal Error IO 104 or whatever is a video card error, but you can avoid it easily.

Boot from the GParted Live CD, and go until you're given the option of running Beginner, Medium, or Advanced versions of the program.  Choose Advanced and click through the screens.  You'll get to a screen where it prompts you to select a video driver for X Server: make sure you select VESA.  Continue as usual.  That should fix the problem.

---

### Post by frafu on 2008-04-07
Hello, 

I moved this thread to the "Installation & Upgrades" forum, where it is more appropriate. 

Have a nice day. 

Francesco

---

