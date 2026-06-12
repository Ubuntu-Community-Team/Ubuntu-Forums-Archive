---
title: "Can't edit xorg.conf"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by Nozomi on 2006-07-05
I tried to install ubuntu 6 from live CD several times on my inspiron 1100 and found a  problem as same as everyone who use the laptop.:confused: 

;) I tried to search & read from many thread including

[http://ubuntuforums.org/showthread.php?t=183285](http://ubuntuforums.org/showthread.php?t=183285)
[http://ubuntuforums.org/showthread.php?t=147307](http://ubuntuforums.org/showthread.php?t=147307)

so I know how to solve the problem but it doesn't work.:( 

When I tried to open by using command from terminal windows, it take a long time to open (10 minutes and in sometime have a application crash or longer no responding) and show a blank text file not have anything.;) 

;-) Then I tried to open the file from "File system > ect/X11/xorg.conf". I can edit but can't save, may be it's a file on CD and can't changes.:confused: 

What can I do ? please help me.
Sorry for my english not good and make you confusing or misunderstand.

---

### Post by taurus on 2006-07-05
Do you plan to install Dapper on your machine?  You can download and use the alternate CD if you are having problem with your video card...

---

### Post by linear on 2006-07-06
To edit xorg.conf, you need root privileges. At a terminal prompt, type:
 
```
sudo nano /etc/X11/xorg.conf
```
 
If you get a blank window, check spelling and case - it's "X11", not "x11".

---

### Post by Nozomi on 2006-07-09
Thanks a lot. For solved the problem I used alternative CD. It's okay and easy to install as same as liveCD. This is a screenshot my desktop.:D 
[IMG]http://photos1.blogger.com/blogger/5483/1718/1600/Screenshot.png[/IMG]

---

