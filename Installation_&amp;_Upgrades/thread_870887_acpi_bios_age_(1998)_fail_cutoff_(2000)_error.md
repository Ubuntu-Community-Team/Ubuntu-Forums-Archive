---
title: "acpi: bios age (1998) fail cutoff (2000) error"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by dontknowmuch on 2008-07-26
Cheers everyone:

first post, never ever used ubuntu, xubuntu, linux.... only used windows so far...but ready to make a dramatic change... well,maybe, if I can past through my first problem.

I have an old computer, pentium II 333 mhz, 512 meg of ram. I want to install a light OS on it and Xubuntu looked like a good candidate.

I cannot install Xubuntu. CD is read and I get the error - acpi: bios age (1998 fail cutoff (2000), acpi=force is required to enable acpi -
I tried F6, then type acp=force like suggested in this thread [https://answers.launchpad.net/ubuntu/+question/38113](https://answers.launchpad.net/ubuntu/+question/38113) but this did not do the trick for me. I then got an error message - unable to load the system description table -

I am 150% totally new to xubuntu/ubuntu so do not assume I know much... I don't (but tonight I'll be smarter than this morning :-&)

Many thanks in advance for any pointer you may have.

---

### Post by oldos2er on 2008-07-26
I'm not sure the *buntus would be good distros to run on a Pentium II. Anyway, try searching the manufacturer's website to see if there are any BIOS updates available for your machine.

---

### Post by dmm99 on 2008-09-17
I have a very similar problem, with a slightly better machine.  It ran Win98 just fine, until a file in the OS got corrupted.  So I got out the Win98 CD but couldn't find the card with my registration number.  (AAARGH!  Why do I need that just to FIX an install?  Darn you, MS!!)

Anyway, to get back to Xubuntu, I decided to forget MS and just install Xubuntu.  But it won't install.  I get the same sort of error messages that the thread originator gets.

I don't understand why people are being told, "Xubuntu doesn't like those old systems."  I'm sorry, but that seems dumb to me.  If my system were only a few years older, it would be good enough to run regular Ubuntu.  So then what's the point of Xubuntu, if not to allow Ubuntu-lite on older PCs?  I realize that you are all volunteers, so I'm not trying to put you down.  I'm just frustrated.  I was all excited about "putting it to the man" (even though I already paid the man for my OS which no longer works), and now I'm told my PC is too old to run Xubuntu.  What the heck??  It ran Win98; I thought Xubuntu was LESS demanding.

---

### Post by oldos2er on 2008-09-17
> **dmm99 said:**
> 
I don't understand why people are being told, "Xubuntu doesn't like those old systems."  I'm sorry, but that seems dumb to me.  If my system were only a few years older, it would be good enough to run regular Ubuntu.  So then what's the point of Xubuntu, if not to allow Ubuntu-lite on older PCs?  I realize that you are all volunteers, so I'm not trying to put you down.  I'm just frustrated.  I was all excited about "putting it to the man" (even though I already paid the man for my OS which no longer works), and now I'm told my PC is too old to run Xubuntu.  What the heck??  It ran Win98; I thought Xubuntu was LESS demanding.

 No. Ubuntu and its derivatives are modern OSes that require relatively modern hardware to run efficiently. But, there are distros that will run on your hardware. You should check Damn Small Linux, and Puppy Linux.

---

### Post by dmm99 on 2008-09-18
Are those other OSs GUI-driven, with WYSIWYG replacements for Word, Powerpoint, etc.?  Because my current PC, even with Win98 crippled, still runs in DOS-only mode.  (I realize that Linux, like all Unix derivatives, is "so much more powerful, once you know what to do," but my wife doesn't care a fig about that.  She just wants a working computer -- and by "working" she means "it works, and I already know how to use it.")

---

### Post by dmm99 on 2008-09-18
My last post might not have been very clear.  My point is that I already have a text-only OS working on that PC, so there is no motivation for me to install a text-only Linux OS.  For all of its faults, DOS has the supreme advantage that my wife already knows how to use it.  I was hoping to replace the broken Win98 with a GUI-driven Linux that has a few key WYSIWYG apps.  Hence my question about Damn Small Linux and Puppy Linux.

Also, although I realize that Ann is trying to be helpful, she never did answer my question about Xubuntu.  What is the point of it?  I'm a total newbie with regard to Ubuntu, so feel free to talk down to me.

---

### Post by dmm99 on 2008-09-18
I've been reading about Puppy Linux on Wikipedia:
[http://en.wikipedia.org/wiki/Puppy_Linux](http://en.wikipedia.org/wiki/Puppy_Linux)
and on several web links listed there.
It sounds like it might be just what I need.
I'll let this forum know what happens.

---

### Post by oldos2er on 2008-09-18
> **dmm99 said:**
> 
Also, although I realize that Ann is trying to be helpful, she never did answer my question about Xubuntu.  What is the point of it?  I'm a total newbie with regard to Ubuntu, so feel free to talk down to me.

 I seriously doubt Puppy and/or DSL have "WYSIWYG replacements for Word, Powerpoint" although OpenOffice should work at least for word processing.

 The "point" of Xubuntu is that some people prefer xfce over Gnome or KDE, that's all.

---

### Post by Vivaldi Gloria on 2008-09-19
See 

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

for a list of OS for old computers.

Most lightweight distros come with abiword btw.

---

### Post by dmm99 on 2008-09-23
I downloaded Puppy Linux and tried it as a Live CD OS.  It works fine on a good new PC.  Abiword is included, and it's a decent WYSIWYG word processor.
Unfortunately, my old PC is now having hardware issues, so I can't test it out properly.  I did get it to run once, and the included apps were very responsive after the initial OS load.

---

### Post by oilchangeguy on 2008-09-23
> **dmm99 said:**
> I have a very similar problem, with a slightly better machine.  It ran Win98 just fine, until a file in the OS got corrupted.  So I got out the Win98 CD but couldn't find the card with my registration number.  (AAARGH!  Why do I need that just to FIX an install?  Darn you, MS!!)

Anyway, to get back to Xubuntu, I decided to forget MS and just install Xubuntu.  But it won't install.  I get the same sort of error messages that the thread originator gets.

I don't understand why people are being told, "Xubuntu doesn't like those old systems."  I'm sorry, but that seems dumb to me.  If my system were only a few years older, it would be good enough to run regular Ubuntu.  So then what's the point of Xubuntu, if not to allow Ubuntu-lite on older PCs?  I realize that you are all volunteers, so I'm not trying to put you down.  I'm just frustrated.  I was all excited about "putting it to the man" (even though I already paid the man for my OS which no longer works), and now I'm told my PC is too old to run Xubuntu.  What the heck??  It ran Win98; I thought Xubuntu was LESS demanding.

if you can still get windows to run, either normally or in safe mode read this.
[http://pcsupport.about.com/od/tipstricks/ht/find98key.htm](http://pcsupport.about.com/od/tipstricks/ht/find98key.htm)

---

