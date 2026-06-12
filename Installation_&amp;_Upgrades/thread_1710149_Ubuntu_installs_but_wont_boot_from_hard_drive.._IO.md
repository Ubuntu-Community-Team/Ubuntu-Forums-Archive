---
title: "Ubuntu installs but wont boot from hard drive.. I/O errors after install"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by Tarhawk on 2011-03-19
I am new to Ubuntu, I have erased Windows 7 partition (I am never going back to the worthless world of MS so someone please help me get this ironed out) and am wanting to use Ubuntu exclusively.  I have tried to install both 10.10, and the 10.4 LTS and I am running into the same problem.  I have looked over the forums and cannot find a thread whose solutions have worked for my particular manifestation of the I/O error install problem.
To begin: My system is a lenovo thinkpad R400 dual core pentium.  I can run both 10.10 & 10.04 from the live cd.  I am burning ISO image to CD from website, I have tried different burning media and still same result, as well I have tried slower burn speeds with same result.  
Both 10.10, and 10.04 install fine and go through the entire setup like it should.  I get to the end of the setup, it asks me to restart, I restart system and it goes to DOS-like prompt(I am an amateur)where it looks like it is loading the system but then it spits out a long list of I/O sector errors at which point I press enter to restart the system and the system then boots from the live CD and not the hard drive.  I think that that my system is looking for something on the CD to close out the install but this is just a wild guess:  do I need to possibly format the disk differently before I burn it?  Like I said, I have tried this with both systems, and with different installation configurations and am always ending up with the same result.
I do not think it could be my media as I have switched it multiple times, I do not think it could be the burning hardware b/c I have used 3 different computers and burners to make the ISO CD. 
One last though hiccup: would install possibly be successful if I ran it from inside the live cd operating system, meaning could I install from with in the trial version of Ubuntu?

---

### Post by Hedgehog1 on 2011-03-19
I think the best place to being resolving this is to have you run this script from the LiveCD so we can see what is happening:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

This will tell us how system is trying to boot.

***The Hedge***

:KS

---

### Post by Tarhawk on 2011-03-19
OK: Problem solved for now.  I went through a second install of 10.04 LTS, restarted the machine... then it spit out a long I/O error report, then I press enter, however this time it booted from the hard drive.  Each subsequent boot from hard drive is flawless.  OS is working great from the hard drive now, so I am gonna call my problem: cured.

---

