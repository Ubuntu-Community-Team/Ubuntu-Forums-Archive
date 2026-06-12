---
title: "Cups server"
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by daniminas on 2005-05-23
Hello

I want to work with my printer, so when i go to System->admin->Printers, do not appear the printers dialog, only the "Cups Server not found" message (in spanish).. I was checkin the Cups conf's, i open a Terminal and run cupsys start, but a few seconds later i get : "Chils procecess... status 13 finished" (in spanish)..

What am i missing?... What can be wrong?.

Thanks

Danielle

---

### Post by fastluck on 2005-06-30
I'm having the same problem.  But it occurred after apt-get upgrade.  What gives?  I verified the server is installed.  But depending on whether I'm using Gnome or KDE, it either says I don't have access or the server could not be contacted.

John

---

### Post by alexanderfrey on 2005-07-02
The same problem at mine.  I use kubuntu and when I try to start the printer manager it's says that I should check whether cups is installed or not. When I try to restart cups the following happens:
alex@ubuntu:~$ sudo /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd
cupsd: Child exited with status 99!


Hey, I really could need some help. If someone has an idea please post it.


Thanks, Alexander

---

### Post by fastluck on 2005-07-06
There's a module that disappeared in the last upgrade.  I can't remember what it was.  I think my solution was to remove CUPS and reinstall it.  I'll check my laptop tonight and see if I can find out what the module name is.

---

### Post by alexanderfrey on 2005-07-07
So you just reinstalled cups ?

---

### Post by fastluck on 2005-07-07
Alexander,

I'm not sure.  I meant to check that when I got home last night, but I forgot to.  There's one module that's missing.

---

### Post by Manny C on 2005-07-14
I have the same problem. Tried to reinstall different cups packages. Also tried removing and reinstalling. Restart cupsys and get child error.

This problem has also sprung up on the following thread (with no answer):
[http://ubuntuforums.org/showthread.php?t=33185](http://ubuntuforums.org/showthread.php?t=33185)

I tried the #Ubuntu...noone answered my question.

Someone help?

---

### Post by alexanderfrey on 2005-07-14
Strange, isn't it ?

I installed ubuntu on my girlfriends laptop and cannot print. No connection to cups !

I really love this distri, but it should be possible to print...
What the hell is going wrong ?

waiting, alexander

---

### Post by ajbaerg on 2005-07-27
This seems to be a general debian issue... I found this mailing list post that solved the problem for me:

[http://lists.debian.org/debian-user/2005/02/msg02235.html](http://lists.debian.org/debian-user/2005/02/msg02235.html)

---

