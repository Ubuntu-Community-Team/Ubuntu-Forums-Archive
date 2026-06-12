---
title: "another /bin/sh: cant access tty"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by rbprogrammer on 2007-08-26
so i get this error:
```

/bin/sh: can't access tty; job control off
(initramfs)

```

this is the *first *time i am installing feisty on this computer, so when i put in the live cd, the spalsh screen has the moving progress bar then i get that error.  it's a dell insprion 1720..

---

### Post by Pumalite on 2007-08-26
Problem with many faces. Multiple fixes. Here you have something to read: [http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

---

### Post by rbprogrammer on 2007-08-26
just remembered that i have a Core 2 Duo System on the laptop and i'm trying to install the 32bit version.  did not get to try the 64bit yet but i wanted to see if i can install ubuntu first..

---

### Post by rbprogrammer on 2007-08-26
> Problem with many faces. Multiple fixes. Here you have something to read: [http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

nope that didnt help.. its a really new computer and since the floppy has become obsolete with me, i dont see the need for one

so i dont know where to go from here..

---

### Post by Pumalite on 2007-08-26
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

[http://ubuntuforums.org/showthread.php?t=279721](http://ubuntuforums.org/showthread.php?t=279721)

[http://ubuntuforums.org/showthread.php?t=281459](http://ubuntuforums.org/showthread.php?t=281459)

[http://www.linuxquestions.org/questions/showthread.php?t=491380](http://www.linuxquestions.org/questions/showthread.php?t=491380)

If you are not making a living out of it try Ubuntu Gutsy Trive 4 or 5. I'm writing to you from a Core 2 Duo with tribe 4

---

### Post by rbprogrammer on 2007-08-26
i was going to use GParted to create the partitions, but would it work if i created partitions in windows??

since one of the solutions for someone was to just insert a floppy, does the empty space on the hard drive do the same thing to "fix" the error??

---

### Post by Pumalite on 2007-08-26
With XP, defrag several times, erase all temp files and then use Gparted to 'shrink' XP partition. With Vista; use Vista's partitioner, otherwise Vista will not let you run anything in your computer. (see my editing above)

---

### Post by BoomShaka on 2007-09-19
Hi

I see this thread is 3 weeks old, but in any case, I had the same problem, also on a brand new Dell Inspiron 1720 (a nice red one ;) ).
I found the solution here:
[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588) (in the first post)

I was then able to boot from the live CD, however it failed to detect my graphics correctly (not sure the correct terminalogy here).
I am now working on this issue... :D

---

### Post by BoomShaka on 2007-09-19
I think this thread may be pretty helpfull
[http://ubuntuforums.org/showthread.php?t=512576&highlight=1720](http://ubuntuforums.org/showthread.php?t=512576&highlight=1720)

---

