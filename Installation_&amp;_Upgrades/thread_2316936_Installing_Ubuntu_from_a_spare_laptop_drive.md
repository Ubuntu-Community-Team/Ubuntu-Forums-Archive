---
title: "Installing Ubuntu from a spare laptop drive"
date: 2016-03-12
forum: Installation &amp; Upgrades
---

### Post by Richard_Brown on 2016-03-12
Hi

I would like to make a copy of Ubuntu onto a laptop drive and then use it as an install for several laptops that need the data and os installed.

Is this possible please?

Thanks

Rich

---

### Post by kc1di on 2016-03-12
Hello Richard_Brown and welcome to Ubuntu,

What you ask has a lot of if's to it -- is each machine Identical?  if not then the confiuration files needed to run each machine may be different and cause problems.
I think the best way for you to go is to clone the installation on the first laptop and make a custom ISO and burn it to disc or Usb then install it in the other machines.

[This page]("http://askubuntu.com/questions/320826/is-it-possible-to-make-an-exact-iso-of-my-system-to-put-on-other-computers") may give you some tips on how to do that. 
good Luck.

---

### Post by Richard_Brown on 2016-03-12
Hi

Just changing the question slightly then, is it possible to make an installer using the laptop drive and add the files we need on the laptop drive as well please?

Thanks

Rich

---

### Post by Andy_Richardson on 2016-03-12
> **Richard_Brown said:**
> Hi

Just changing the question slightly then, is it possible to make an installer using the laptop drive and add the files we need on the laptop drive as well please?

Thanks

Rich

It is definitely possible to boot the ubuntu installer from a hard drive. If you also want to install to that drive, you would need to have separate partitions for the installer and installation.

---

### Post by goofprog on 2016-03-12
The easiest way I did it was to disconnect all drives and just install as a regular installation. I assume you are using a 2.5" external hard drive install.

---

### Post by oldfred on 2016-03-13
Are you then just using laptop drive as large flash drive?

You can do a new install and restore like recovering from a drive crash. Primarily /home and installed apps list. If systems not totally identical, settings in /etc may not then be the same.

I also like to script some of my install. I do not know scripting well and it maybe was my first. But all I did was copy commands I had run in terminal into a file and add the header so it knew it was a bash file.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

