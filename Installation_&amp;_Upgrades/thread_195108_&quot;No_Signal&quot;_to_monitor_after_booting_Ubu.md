---
title: "&quot;No Signal&quot; to monitor after booting Ubuntu desktop CD"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by grimfang on 2006-06-12
Hi, I'm new to ubuntu (and installing linux), and I'm having some trouble with the Ubuntu 6.06 Desktop CD.  Specifically, when I select either of the first to menu options (try/install, or install in graphics safe mode), the kernal will load, file system will mount, a bunch of things happen OK, then the monitor switches to "No Signal".  I've checked the CD (it passes) and memory (also passes).  

I've got an ABIT KD7-RAID motherboard, Athlon XP 2600 processor, and nVidia geforce fx 5200 (I think).  The disk I want to install Linux in is not in a RAID array, but I do have two disks that are in a RAID array.  Any help would be appreciated.  Thanks!

---

### Post by davidsxls on 2006-06-12
wrong resolution and / or refresh rate?

---

### Post by grimfang on 2006-06-12
No, I've tried adjusting the resolution, and it didn't help.

---

### Post by varkey on 2006-06-12
i have got exactly the same prob. somebody please let me know wht shud be done.

---

### Post by grimfang on 2006-06-12
I'm going to download the alternate CD and try that...

---

### Post by grimfang on 2006-06-12
A little more information:
The list goes through Starting system log... OK, then a blinking underscore appears for a few second, and then the system blanks out.  
Is this a video driver issue? I've tried setting vga=771 without success.  Do I need nVidia drivers?  If so, how do I get them, given I can't boot?
Thanks for your help!

---

### Post by xpeeblix on 2006-06-12
Check out this thread, we're having the same problems....

[http://ubuntuforums.org/showthread.php?p=1130631](http://ubuntuforums.org/showthread.php?p=1130631)

---

### Post by halcyon-life on 2006-06-12
[QUOTE=grimfang]A little more information:
The list goes through Starting system log... OK, then a blinking underscore appears for a few second, and then the system blanks out.  
Is this a video driver issue? I've tried setting vga=771 without success.  Do I need nVidia drivers?  If so, how do I get them, given I can't boot?
Thanks for your help![/QUOTE]

I've got exactly the same problem, I am guessing it's a problem with X or with Gnome and not the ubuntu base install because i've gotten 5.10 running fine on this hardware and the server 6.06 install boots no problem, it also gets through the graphical boot with the Ubuntu logo and then blanks out, sometiems puching the whole screen to the left which would suggest, again, a graphical problem.  

I'll have to go through the solutions in the thread linked to by xpeeblix and see if those fix this problem.

---

### Post by varkey on 2006-06-13
i started the cd with safemode graphics and it worked. try that

---

### Post by halcyon-life on 2006-06-13
[QUOTE=varkey]i started the cd with safemode graphics and it worked. try that[/QUOTE]

i'm not sure how to do that, thanks for the tip though.

---

