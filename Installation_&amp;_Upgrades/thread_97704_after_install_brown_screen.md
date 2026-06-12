---
title: "after install brown screen"
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by dronepower on 2005-12-01
I did a nice install on my HDD, all went fine.  Typed my name + pw, then a nice brown screen. I could move my mouse.

Other topics I found about this are: 

[http://www.ubuntuforums.org/showthread.php?t=77209&highlight=brown+screen]("http://www.ubuntuforums.org/showthread.php?t=77209&highlight=brown+screen")
[http://www.ubuntuforums.org/showthread.php?t=25487]("http://www.ubuntuforums.org/showthread.php?t=25487")
[http://www.ubuntuforums.org/showthread.php?t=87586&highlight=brown+screen]("http://www.ubuntuforums.org/showthread.php?t=87586&highlight=brown+screen")
[http://www.ubuntuforums.org/showthread.php?t=84125&highlight=brown+screen]("http://www.ubuntuforums.org/showthread.php?t=84125&highlight=brown+screen")
[http://www.ubuntuforums.org/showthread.php?t=94233&highlight=brown+screen]("http://www.ubuntuforums.org/showthread.php?t=94233&highlight=brown+screen")

pls don't start telling my CD is corrupt cause it aint.

I got a venice 3000+ on a neo2 board, with a 6800LE for the pictures :) 

I hope someone knows what the problem is here.

---

### Post by aysiu on 2005-12-01
Any difference if you hit Control-Alt-F1?

---

### Post by 23meg on 2005-12-01
You need to install the proprietary nvidia driver, or switch to vesa. 

[http://www.ubuntuforums.org/showpost.php?p=536421&postcount=11](http://www.ubuntuforums.org/showpost.php?p=536421&postcount=11)

---

### Post by juusor on 2005-12-03
I have almost the same problem...  Except that with me it proceeds after about 5 minutes of blue-screen (because i have previously changed the desktop background to blue) and everything works fine.

But then when log-outing or rebooting there is again the same kind of freezement when its quiting Gnome/X11.

Text-based logins (like Alt-F1) works without problems.

I upgraded from hoary to breezy yesterday via apt-get.  Couple of first boots it went fine but then it started to do the freezy-thing... :(  

My graphic card is ATI Radeon 9600pro (if this problem has something to do with it, but I don't think so...)

---

### Post by 23meg on 2005-12-03
Try ```
sudo dkpg-reconfigure gdm
``` as well as installing a different GDM theme. Also try removing any programs you've added to your session startup.

---

