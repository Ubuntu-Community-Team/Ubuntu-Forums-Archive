---
title: "Grub package fails to install"
date: 2006-05-09
forum: Installation &amp; Upgrades
---

### Post by crazybilly on 2006-05-09
I'm a 100% linux newb working on installing Ubunutu on an older laptop.  I'm getting to the grub install part and it keeps failing.  I get the following error message:  

[FONT="Courier New"]The grub package failed to install into /target/.  Installing GRUB as a boot loader is a required step.  The install problem might howeer be unrelated to GRUB, so continuing the installation may be possible.

GRUB installation failed.  Continue anyway?
[/FONT]

I get the same when I try to install LILO (on either the mbr or the ubuntu part.).  

After continuing w/ the install w/o a boot loader (I figure I can reformat and reinstall pretty easily), I get an 'Error loading operating system' error (big suprise).  I tried booting from the cd w/ the following command:  linux /dev/hda1 root=/dev/hda1 (the installer suggested that I boot manually with [FONT="Courier New"]the kernel on partition /dev/hda1 and root=/dev/hda1 passed as kernel argument[/FONT].

That ended up w/ a kernel panic - not syncing error, and the computer stopping.  

I'm going to try reinstalling. Anybody got any suggestions as I do?   Thanks!

---

### Post by Sef on 2006-05-09
Before installing, I would use GParted and delete all the partitions.  Then during install, then reinstall the partitions that you want.  If you do manual partitioning, they should be root, home and swap.

I had a similar problem like that once and deleting and reinstalling the partitions got my system up and running.

---

### Post by crazybilly on 2006-05-09
I went ahead and tried reinstalling, just to see what would happen.  This time, I used LVM to repartition.  I just used the default settings, and it got me in. 

Strange.  But the problem seems to be solved now.  Now, if these packages would ever finish installing so I could go to bed :D

---

### Post by Sef on 2006-05-09
I hope all works for you, and you can sleep knowing you have an installed Ubuntu system.

---

### Post by crazybilly on 2006-05-09
seems to be working good.  thanks for the help--I'm looking forward to getting a feel for this linux stuff!

---

### Post by Sef on 2006-05-09
You're welcome.  And please post any more questions that you have.

---

### Post by shergill on 2006-05-09
Any idea what the issue might be with my installation?

[http://www.ubuntuforums.org/showthread.php?t=172621](http://www.ubuntuforums.org/showthread.php?t=172621)

---

### Post by Sef on 2006-05-09
Click on your link, shergill.  I wrote what to do to get your system up and running.

---

