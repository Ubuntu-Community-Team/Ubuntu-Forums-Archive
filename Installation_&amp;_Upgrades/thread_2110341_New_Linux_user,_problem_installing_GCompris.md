---
title: "New Linux user, problem installing GCompris"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by flashvenom on 2013-01-30
Love the commnuity and look&feel of Linux. I am very disappointed I didn't get into this stuff earlier. Anyways, I'm a tenderfoot and resurrected a pretty old Dell PC so my kids can have thier own computer. I found GCompris and badly want to install it. (I remember playing number muchers!)

Anyways, I followed these instructions:
[http://ubuntuforums.org/showthread.php?t=1280450](http://ubuntuforums.org/showthread.php?t=1280450)  And thought I was a super star. No errors, make and make install  worked great. But I can't find the app anywhere, AND when just typing  "gcompris" it says the app is not installed.



 Can anyone  give me some HINTS to a noob Linux user? I.e. Is there an app directory I  can look in, or did I not install it correctly, or? Also, what is  "Launcher" and how will I just add a GCompris icon to the desktop so my  kids can easily launch it? (I am quite surpsied this software wasn't in  Lubuntu's Software Center)


 I'm running the newest version of lubuntu and GComrpsi - I did this all right now. I'm not sure what other info will help.. If I tyupe make  now, I get a LOT of
```
make[5]: Entering directory `/home/nathan/Downloads/gcompris-12.05/src/target-activity/resources/target'
make[5]: Nothing to be done for `all'
```Which I don't remember seeing the first time...

and when I type make install I get a lot of
```
make[1]: Leaving directory `/home/nathan/Downloads/gcompris-12.05/src'
make: *** [install-recursive] Error 1
```Can anyone tell me what might be the trouble?


Thanks in advance!

---

### Post by Nr90 on 2013-01-30
I think you have to run make install as root:
sudo make install
Not an expert though.

---

### Post by Bucky Ball on 2013-01-30
Welcome to the forums.

Why are you trying to compile it? It is in the repositories. Find it in either Software Centre or Synaptics. You can should also be able to open a terminal and simply:

```
sudo apt-get install gcompris
```

yes, it is 'sudo make'.

---

### Post by flashvenom on 2013-01-30
So, I looked in the Lubuntu software repo and it wasn't there (bummer), so after I tried the link instructions, I tried launching it. It said it wasn't installed and asked if I wanted to install it... I put YES, and it in turn ran the exact sudo apt-get command you mentioned. So I basically installed (attempted anyways) twice! 

So after the second install (the one you suggested), then what? Because it runs a ton of code, but then I'm just back at command line. I try running and it says it's not installed, thus putting me in an endless loop. 

Running make and make install give me the errors I pasted above... Geez it sounds like I"m doing things right.. What am I missing here?

---

### Post by vasa1 on 2013-01-30
LSC currently has fewer programs. Try Synaptic or apt-get directly as advised.

---

