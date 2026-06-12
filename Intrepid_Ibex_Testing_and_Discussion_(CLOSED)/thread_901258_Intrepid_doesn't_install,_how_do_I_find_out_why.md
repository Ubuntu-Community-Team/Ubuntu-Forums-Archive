---
title: "Intrepid doesn't install, how do I find out why?"
date: 2008-08-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xlinuks on 2008-08-26
Hi,
I downloaded today the latest daily build and while installing Ubuntu (Intrepid) hangs at about 80%, there is no progress anymore. I couldn't try a text install for I found only GUI options to install.
Please let me know what I can do to find out why it hangs, if there was a text install I could at least report _when_ it hanged and what it was doing, but all I see is a brown progress bar that stops at like 80%.
Any hint/help would be appreciated.

PS: downloaded the x86 version for an athlon 64 (I always use x86 versions for I still find x64 always troublesome), 1.5GB of RAM, GeForce 6800GS 256MB, motherboard K8N Neo3 (MSI).

---

### Post by Nullack on 2008-08-26
Youll probably have recurring issues with daily Ubuquity builds during Alpha. Use the alternate installer for a better chance. Or to be sure, use Alpha 4 either Ubuquity or alternate and update it to current.

---

### Post by xlinuks on 2008-08-26
Thanks,
the alternate version did install, but after trying to boot into the OS I get a scrambled screen, which is what I expected since many distros can't work with my video card.. gonna try my luck some time later, Ubuntu usually starts working with that video card after going beta or so.

ps: Going to a terminal (Alt+F3) and doing "sudo dpkg-reconfigure -phigh xserver-xorg" didn't help.

---

### Post by dabl on 2008-08-26
Did you try the "Fix X" utility in Recovery Mode?

---

### Post by xlinuks on 2008-08-26
Yeah.. didn't help.. after that I tried sudo dpkg-reconfigure -phigh... and none worked.

---

### Post by dabl on 2008-08-26
If it is running in text mode, you probably can review the log at /var/log/Xorg.0.log and see what is going wrong.

---

### Post by philinux on 2008-08-26
> **xlinuks said:**
> Yeah.. didn't help.. after that I tried sudo dpkg-reconfigure -phigh... and none worked.

xfix essentially runs that command. There's is no graphics info in xorg.conf any more. It's basically a stub file now.

---

### Post by meborc on 2008-08-26
> **xlinuks said:**
> ...which is what I expected since many distros can't work with my video card...

just out of curiosity, what is the mark and model of your card?

---

### Post by xlinuks on 2008-08-26
Please see my first post, I specified there my hardware configuration.

---

