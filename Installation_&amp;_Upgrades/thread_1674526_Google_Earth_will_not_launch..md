---
title: "Google Earth will not launch."
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by Nitrozzy7 on 2011-01-24
Hello,
I've just downloaded and installed the latest version of Google Earth but it won't launch no mater how many clicks I do to it. Is this a known bug or something? How can I launch it?

---

### Post by Elfy on 2011-01-24
If you get this message after trying to run it from a terminal

> Google Earth 6 not starting - /usr/lib/googleearth/googleearth-bin: not found

Try installing lsb-core

---

### Post by Savio2010 on 2011-01-24
Read this

[http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/)

"If Google Earth will not launch after installing, go to ***Applications –> Accessories –> Terminal*** and run the command......................"

---

### Post by Nitrozzy7 on 2011-01-24
@Savio,
Solved. The last command did the trick! I only wish I didn't had to contact the community to solve this. Google search didn't help you know.

---

### Post by Leeinfl on 2011-03-19
The last command line worked like a charm. Thanks a million. Now.. if you can figure out how to get an Alesis usb multimix8 to work... lol. Just kidding of course.

---

### Post by spearsem on 2011-08-31
I followed the instructions here, including installing lsb-core, and even though Google Earth appears in my Applications drop down, it will not launch (whether I invoke it graphically or from the command line). Any ideas?

---

### Post by phubert28 on 2012-06-12
I, too, tried all this but for ONE thing: my Software Center is a little bit hosed since I did an UPGRADE from 10.04 to 10.10 (I subsequently upgraded to 11.04) - "Install" doesn't function. It also does not function in Update Manager.

Is there any way to do this from either Synaptic or Terminal (command line)??

**

I know, I NEED to do a fresh install of 12.04 on another partition. I have both 32 bit and 64 bit DVDs - already installed 12.04 on a friend's machine, but *I* need to ditch Unity in my install (dual monitor, really cannot abide the wide launcher - LOVE the tiny icon launcher at the top of my left hand screen - NEVER use keyboard shortcuts).

***

Well, FOLLOWED the one-line instruction TO install at the end of the dpkg --force sequence and all is well!

---

