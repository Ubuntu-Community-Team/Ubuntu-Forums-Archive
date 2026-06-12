---
title: "Strange Screen After Kernel Update"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by Vimmander on 2010-07-24
Well, I haven't found this on the forums yet, though a few similar things have happened.

I just got the new kernel update (2.6.32-24-generic, according to "uname -r"), and I went to restart my computer as the system requested.  When I selected the new kernel from the boot menu, the Ubuntu splash screen came up, and then it did this subtle alternating shades of purple horizontal line thing.  Then a vertical line appeared towards the right of the screen, and then everything faded into this cloudy, bright white splotchy...thing.  The keyboard was still responsive, and hitting ctrl+alt+delete restarted the machine, at which point I tried to replicate the problem, but everything loaded normally this time.

My questions are:  What the heck happened?  Why?  Is it dangerous?  Why or why not?

My machine is a Dell Inspiron 1501, 2 GB RAM, 120 GB hard drive, ATI integrated graphics, AMD 64 Anthlon X2 processor.  I'm dual booting with Windows 7 as I learn Linux.

---

### Post by kmsalex on 2010-07-24
Linux can be a quarcy thing, on my desktop i'd say on in 10-15 boot's it never loads the login screen. i just restart and try again and it works. with my laptop the boot splash always looks weird (when it's displayed at all). a great man once said, "if it an broke don't fix it" now it booted normal the second time right? so don't fix it, or if you like use a different kernel. 

regards,
alex

---

### Post by Vimmander on 2010-07-24
The same thing just happened after doing

```
sudo apt-get autoremove
```

Which got rid of something related to a kernel header.  Perhaps it was mere coincidence that the same thing happened when booting into the kernel mentioned in the output of that command (2.5.31, or whatever comes with the 10.04 ISO).  Did crl+alt+delete again, and it restarted, I booted into the old kernel just fine.  You're right, kmsalex...Linux can be quirky at times.  It's probably my graphics card freaking out.  I wonder why the keyboard was non-responsive on one occasion, though......

---

