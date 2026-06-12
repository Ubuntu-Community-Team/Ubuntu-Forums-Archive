---
title: "Xubuntu clean install help"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by CMXILies on 2011-12-18
Took my 30g hard drive out of a non-working computer of mine, installed Xubuntu on it for another old computer that needs a new OS, but when I travelled to test it out, after hooking up my HD the computer wouldn't even let me get into the GRUB menu, just sorta restarted over and over. Needless to say it works with the machine I used to install the OS.

a RAM issue perhaps? 
I still have to do some double checking (make sure I didn't break or fry it somehow) but that's where I'm at.

---

### Post by MAFoElffen on 2011-12-19
> **CMXILies said:**
> Took my 30g hard drive out of a non-working computer of mine, installed Xubuntu on it for another old computer that needs a new OS, but when I travelled to test it out, after hooking up my HD the computer wouldn't even let me get into the GRUB menu, just sorta restarted over and over. Needless to say it works with the machine I used to install the OS.

a RAM issue perhaps? 
I still have to do some double checking (make sure I didn't break or fry it somehow) but that's where I'm at.
What version of Xubuntu?

My thoughts - Video/Graphics Card?  The Ubuntu base system (CLI) underneath Xubuntu will boot and run with everything as a Text Console in less than 64MB's.  I knwo this as I'm putting together a text-based Ubuntu distro and have 4 Ubuntu Servers. Grub2, I never test the memory requirement, but I would say that it takes almost nothing to run on!

Graphics GPU's affect Xubuntu, but not really grub per say.  What you might want to know is that Some hardware combinations will prevent grub from showing with the shift hotkey.... But I found a hard coded way around that:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Forcing Grub to Show Menu**]("http://ubuntuforums.org/showpost.php?p=11469860&postcount=800")[/SIZE][/COLOR][/SIZE][/COLOR]

In fact, while you're there, look at Post's 1-3.  Good resource for a lot of diagnostics, triage and repair for various issues, beyond just graphics.

---

### Post by CMXILies on 2011-12-19
> **MAFoElffen said:**
> What version of Xubuntu?
11.04.

Those threads are very helpful (for many more problems than just this one). Looking forward to tackling this one.

---

