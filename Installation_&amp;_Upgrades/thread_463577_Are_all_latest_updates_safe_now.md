---
title: "Are all latest updates safe now?"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by moitinh on 2007-06-03
I just installed 7.04 on my dual laptop running with WinXP.  This is probably the 10th time in 2 days already.  When I used Update Manager and installed all the latest updates.  I can't boot into Linux anymore because it hangs so I have to boot it from the CD and reinstall everything.  I'm using GAG and LILO to boot into Linux.

There are 50 updates now and I like to keep my Ubuntu up to date but I'm afraid to install them.  Any advices?  It's so frustrating in that I can't trust all the latest updates.

---

### Post by confused57 on 2007-06-03
> **moitinh said:**
> I just installed 7.04 on my dual laptop running with WinXP.  This is probably the 10th time in 2 days already.  When I used Update Manager and installed all the latest updates.  I can't boot into Linux anymore because it hangs so I have to boot it from the CD and reinstall everything.  I'm using GAG and LILO to boot into Linux.

There are 50 updates now and I like to keep my Ubuntu up to date but I'm afraid to install them.  Any advices?  It's so frustrating in that I can't trust all the latest updates.
Your problem was probably with the kernel update:
[http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)

In your previous install, did you try booting from the older kernel?

You could probably uncheck the kernel update, everything else "should" be OK to update.

---

### Post by moitinh on 2007-06-03
i unchecked everything and just installed Firefox and it pulled down the new kernel along with it.  i had to reinstall again :(

i'm using GAG and LILO to boot into my dual laptop so i don't have the menu to select old or new kernel.

shouldn't ubuntu QA the new kernel first to make sure it's working?  this is not right.  i'm tired of reinstalling.

---

### Post by zvacet on 2007-06-04
go to the synaptic and find linux image wich you use(that is your kernel)and mark it and go  to the package and select lock version.Maybe that will help.

---

### Post by vanadium on 2007-06-04
I am also a kernel victim. After an update, my desktop system would drop me on an emergency prompt. I find it worrying that an update can break a system so badly. Strange also that this just passes: the thread referred to does not post solutions, only a workaround ("do not use the updated kernel") and I did not find any sign elsewhere about this issue. To continue to use the previous kernel for now, several solutions came up. My approach was to edit /boot/grub/menu.lst and comment out all entry for the new kernel:

#title		Ubuntu, kernel 2.6.20-16-generic
#title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)

Indeed, the kernel that is on the top of the list is the one that is loaded by default.

---

