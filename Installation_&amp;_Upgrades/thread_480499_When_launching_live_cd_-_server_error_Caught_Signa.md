---
title: "When launching live cd - server error: Caught Signal 11 Server Aborting"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by jamigre on 2007-06-21
Hi. So I'm super new to linux. And I read through the forums, and I looked online, and i even tried the "dpkg --configure" commands (but i'm not a superuser, and i dont know how to access that)... but basically, when I try to launch the live cd, i get tp to Mode1e6, and which then displays this message. 

Vesa (0) Not unsing mode "640x480" 
(WW) Vesa (0) No validations left. Trying less strict filer

Backtrace:

Fatal Server Error: Caught Signal 11. Server Aborting. 

I've tried on normal, on low quality, and I get the same message no matter what. I know it should be vesa, because I got through an elive installation with vesa drivers (as when prompted the radeon ones would crash the livecd and go to console (prompt?)), and now have it (elive) on my spare HDD, but I want to run Ubuntu instead of Elive, and for some reason can't get beyond this point. 

After looking online, I found steps that say "dpkg" may or may not fix this problem (i have no idea but was willing to try... but as I mentioned before the command requires superuser privilages, that I dont know how to access. 

So.... if there is anyone out there, who can help a total noob out, it would be super cool. 

Btw, here are my specs

Dell Inspiron E1505
1GB Ram
Core Duo 2.0Ghz
Ati Radeon X1400 (Mobile)
SATA 100MB HDD 7200RPM

Thanks a bagillion in advance. 
- Jam

---

### Post by empthollow on 2007-06-21
i believe the cd includes safe a safe graphics mode, you can read more options by using the function keys at the boot menu, i would keep trying different video settings a boot.

---

### Post by jamigre on 2007-06-23
did it, i tried everything, even changing vga settings, but Xserverfails to launch and i keep on getting the same problem
 :/

---

### Post by merlinus on 2007-06-23
You might try the Alternate Desktop install cd.  It is text-based, so should not present any video-related problems.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, Then click the text to start the process.

-merlin

---

### Post by empthollow on 2007-06-24
check this thread, this might be helpful
[http://www.linuxquestions.org/questions/showthread.php?t=256896](http://www.linuxquestions.org/questions/showthread.php?t=256896)

---

