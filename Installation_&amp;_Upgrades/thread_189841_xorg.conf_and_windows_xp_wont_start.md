---
title: "xorg.conf and windows xp wont start"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by dj1120 on 2006-06-05
Ok I goofed something up  I install dapper 6.06 from the cd onto my second(brand new) wd 400gb sata hard drive. windows xp is running on the the drive a 250 gd sata drive. Dapper worked fine all weekend but when I booted the machine this am I got error message stating that xorg  failed to start and/or may not be configured properly. In addition my windows hard drive won't boot as well.

 I was dual booting with and 80gb ide drive untill this weekend when I installed the new sata drive  with no problem?

How do I recover and or reconfigure xorg?

 ( windows xp I will attempt to repair with the cd)
I

---

### Post by oldmanstan on 2006-06-05
You should be able to get into the terminal even with xorg not working, if this is not the case then your problems are more serious...

It should prompt you to view the error message xorg is returning, near the bottom (probably) should be a message that basically tells you what part of the xorg.conf is the problem. it might say something like "no screens found" or something, post what it says.

also, post the contents of your xorg.conf file in /etc/X11/ if you can

---

### Post by dj1120 on 2006-06-05
ok it says xserver failed to start. I am able to look at the contents of my home folder but do not know how to look at xserver/xorg from root. I see log file "/var/log/xorg.o.log" then "/etc/x11/xorg.conf

---

### Post by dj1120 on 2006-06-05
forgot to add  the next error message "xf86closeconsole:kdesetmode failed bad file descriptor"

---

### Post by oldmanstan on 2006-06-06
hmmm... i have never seen that particular error

you may want to do a fresh install unless you have files that can't be deleted in a reformat

the other option is to google the error message you got or check the x.org wiki at [http://wiki.x.org/wiki/](http://wiki.x.org/wiki/)

most of the time when my X won't start it is because i made a typo editing it, if you changed it before installing the new HD check the changes

---

### Post by dj1120 on 2006-06-06
Yeah I did a fresh reinstall of xp (on the 250 gb hd) and dapper (on the 400 gb hd) last night . I am a little worried as to how my boot config for both drives got wiped out though.

---

