---
title: "Error number5 on install"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by Jeff G on 2010-12-31
I am attempting to install Ubuntu 10.04 on a Sony Vaio desktop (intel) and I am getting an error number 5 and the installer quits at the same place, 37% over several attempts.

I have tried several cd's and get the same error at the same place.

I have reset BIOS --same error at the same place

I have put a new hard drive in-- same error --same place.

I am at my wits end-- it is obviously -- something with the machine itself causing it to fail at the exact same place each time but I really don't know where to look for my next troubleshooting spot. Any ideas?

---

### Post by Quackers on 2010-12-31
I know that you've tried different cd's, but were they all burned from the same downloaded iso? Did you check the MD5SUM of that iso?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Jeff G on 2011-01-01
used 2 different isos and had same issue-- was going to try burning on a different machine but I still think this is the machine itself--- the live version on the cd will run fine-- just wont install.

---

### Post by Quackers on 2011-01-01
It could also be a bad burn or a bad read.
DId you check the cd for errors? During boot from the cd (or maybe at the purple screen, can't remember) press the Esc key and you should get a screen up giving you options. One of those options should offer to check the cd for errors.

---

### Post by presence1960 on 2011-01-01
[http://ubuntuforums.org/showthread.php?t=1207755&page=2](http://ubuntuforums.org/showthread.php?t=1207755&page=2)

Scroll down to post #20. Please note there is a spelling error in the command to run in terminal. It reads:

```
uniquity --no-migration-assistant
```

The correct command is:

```
ubiquity --no-migration-assistant
```

It can't hurt to try it. I have used this a couple of times on clients machines. The error actually is errno 5

---

### Post by Jeff G on 2011-01-01
Well I just managed to get 8.04 installed on the machine, and the software I need to run is supposed to work on this system also--- this is to run the touch screen controls on a large machine tool.  So I am going to play with what I have working and not bother updating it. install completed a couple minutes after 12-- do I get a prize for the first install of the new year?  LOL---thanks all.

---

### Post by Quackers on 2011-01-01
Well that's good :-)  No prize though :wink:

---

