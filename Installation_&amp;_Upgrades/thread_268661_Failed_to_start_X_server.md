---
title: "Failed to start X server"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by shahgols on 2006-09-30
Hi everyone,

I am trying to install ubuntu for the first time.  I have a question and I have a problem.

Question is, how does the installation start?  The first option during installation is for starting the Live CD or installing.  When I choose that option, it starts the Live CD without giving me a chance to choose between Live CD and installation on disk.  But that didn't turn out so bad after all.  Because the Live CD load fails with (and this is the problem) "Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly."  Portion of the logs show:

X Protocol Version 11, Revision 0, Release 7.0
Requesting insufficient memory Window! start:0xc010000 end: 0xc7ffffff size: 0xc000001 (there were lots of these)
(EE) ATI (0): Cannot read V-BIOS (3)
no screens found

FWIW, I am not using the the motherboard ATI video card, I have a nvidia GeForce 6800 card.

I lied, I have two questions.  There is another message that says "The X server is now disabled.  Restart GDM when it is configured correctly."  I ran

dpkg-reconfigure xserver-xorg

and went through the graphical card setup, etc.  Once I was done, I had no idea how to start the GDM.  What is the command to start GDM?

Thanks in advance.

---

### Post by Iarwain ben-adar on 2006-09-30
Hi,
the command to start GDM is ```
sudo gdm
```

or maybe try```
startgnome
```

Don't know if the latter works..


Iarwain

---

### Post by louieb on 2006-09-30
To start the GUI from the command line: ```
startx
```
But if read your post correctly the Live CD did not start the GUI but rather displayed the command line. How weird! Anyway I would probaly use the alternative CD in this case.

---

### Post by usererror on 2007-01-08
My X server is also failing on Install.  Going to try the alternative CD...if i can find it.  just trying to do a fresh install of Edgy.  X is not finding any screens.

I posted my solution here:

[http://www.ubuntuforums.org/showthread.php?t=299410](http://www.ubuntuforums.org/showthread.php?t=299410)

---

