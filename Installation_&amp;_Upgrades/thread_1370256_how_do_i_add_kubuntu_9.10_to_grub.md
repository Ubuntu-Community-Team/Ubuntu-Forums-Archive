---
title: "how do i add kubuntu 9.10 to grub?"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by cgb223 on 2010-01-02
hi I just installed kubuntu on my fakeraid system and need help adding it to grub. I need to find the partition it is on. fdisk -l craps on me because of fake raid and i need to know what version of the kernel was installed. (in other words what version does the live cd install?) 

thanks!

---

### Post by Moozillaaa on 2010-01-02
Install this utility and run it, then post the results, which will be saved as a file on your desktop... It's written for Ubuntu users - I got it from another user here, and it helped solve a related problem...

[http://ubuntuforums.org/showthread.php?t=1368505](http://ubuntuforums.org/showthread.php?t=1368505)

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by cgb223 on 2010-01-02
figured it out anyway. went into menu.lst and after changing some numbers arround, for instance the hardrive numbers start at 0 and the raid volume numbers start at 1 threw me off. its all good now. it was 2.6.31-14 btw. is there a way to have the grub automatically find these new partitions and add them? windows too? (regretfully i use win 7 for word processing for lack of a better alternative (open office needs some work and grammar check in english that comes natively)) 

gonna check out the programs now. thanks

---

