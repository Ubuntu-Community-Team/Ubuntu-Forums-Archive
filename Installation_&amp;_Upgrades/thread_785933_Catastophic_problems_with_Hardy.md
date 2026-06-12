---
title: "Catastophic problems with Hardy"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by janothar on 2008-05-07
Hi...I'm still pretty new at linux, and am having a rather nasty problem.  I attempted the Hardy Heron upgrade in Kubuntu, and things have gone rather massively downhill from there.  My laptop (a Dell that came with Ubuntu pre-installed) no longer recognizes DVDs, external hard drives, or either wired or wireless internet access.  I have some very important files on there that I stupidly failed to backup before attempting to upgrade and I need to try to recover.  I really don't know what I'm doing, so I don't have detailed error logs (though if someone tells me how to find the appropriate ones, I'll get them).

So the short of it is, without internet access, and working in Kubuntu, is there any way to roll back to Gutsy versions of things, at least enough so that one of these three things will work?

---

### Post by Pumalite on 2008-05-07
This might be a partial solution:
[http://ubuntuforums.org/showthread.php?t=623058](http://ubuntuforums.org/showthread.php?t=623058)

---

### Post by janothar on 2008-05-07
Ok...that made things much, MUCH worse.  I completed the first command, and then things crashed, and when the computer rebooted, it put me into a command line type of environment asking me to login, but then didn't accept my username and password, so now I'm completely locked out.

---

### Post by Pumalite on 2008-05-07
Get a Knoppix Live CD, save your data and reinstall.

---

### Post by gs_berg on 2008-05-07
Do you have a copy of Knoppix live DVD or CD at hand.  I sometimes use it in similar situations.  It should recognize all your partitions and display their icons on the Knoppix desktop, so you can easily open any partition simply by clicking its icon.  Then you can copy your lost files to a usb stick or external disk.  Besides, it has many other programs and tools that may be helpful.

---

### Post by janothar on 2008-05-07
Ok, I've booted into Knoppix, but being new at this and fairly incompetent, I have no idea how to get access to my hard drive from here.

My USB drive is detected on startup, but the hard drive for the laptop isn't.  And I know it's not encrypted or anything, so it isn't that. (well, I'm fairly sure)

---

### Post by Pumalite on 2008-05-07
It should already be mounted on your Desktop. If not; look in /media. It should be on your Desktop though.

---

### Post by janothar on 2008-05-07
It isn't on the desktop and there is no media folder.

---

### Post by Pumalite on 2008-05-07
Try this one. Burn a new CD:
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by janothar on 2008-05-08
Thanks a lot, that seems to have fixed it.

---

### Post by Pumalite on 2008-05-08
You are welcome. Good luck.

---

