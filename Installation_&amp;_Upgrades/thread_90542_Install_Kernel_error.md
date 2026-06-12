---
title: "Install Kernel error"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by sjkellyfetti on 2005-11-15
Hello,

  I am having a problem installing Breezy i386 on a box that was a Windows XP box.  I installed it once, but had some wireless network problems.  I read up and tried reinstalling, though i used Edubuntu that time, to check it out for putting on my daughters machine and everything worked fine.  The problem was I had Edubuntu, and i wanted Ubuntu, so I tried reinstalling Ubuntu.  

This time, a red screen comes up saying:

[!!] Install the base system
Unable to install the selected kernel
An error was returned while trying to install the kernel into the target system.
Kernel package: 'linux-386'.
Check /target/var/log/bootstap.log for the details

and I can Go Back or Continue

I have tried repartitioning (erasing my 100Gb hard drive) and reinstalling, but to no luck.

Forgive me if I have not provided info that would be helpful.  I am Windows experienced, but a Linux newbie (it still mystifies me).

One question is how do I get to the log and view it?
Another is why would it fail after working right once?  Does the partitioning and erase not get rid of all the old files?

Thanks for any help you can provide.

Sjkelly

---

### Post by suRoot on 2005-11-15
Sounds to me like your CD is bad.  Can you try downloading again & burning a new copy?

You should be able to press ctrl+alt+f1 during the install to get to a console where you can read the log.  I don't remember off-hand which tty the installer uses, so you may try different combinations of f-keys (eg ctrl+alt+f2 , ctrl+alt+f3,  etc).  One of them should get you to a console.  From there you should be able to do something like

```
less /path/to/log/file
```

---

### Post by sjkellyfetti on 2005-11-15
Hmmmm...  I was unsure of the CD being bad given that I had already installed Ubuntu on this machine from it once successfully (well, successfully, except that the Wireless network couldn't be found).  But, looking at the disk, it had some goob on the back side and the CDROM must have choked trying to read the kernel stuff.  Thanks for pointing me in that direction SU!

  On a different note I was able to get another console up (ctrl-alt-F2) but the /target/var/log/ directory had no bootstrap.log file to view!  How useful is that?

Sjkelly

---

