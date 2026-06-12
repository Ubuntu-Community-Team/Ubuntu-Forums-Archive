---
title: "Dual Boot 6.10 + Windows XP"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by evildrummer on 2007-01-07
I am trying to install a copy of 6.10 onto a machine that already has windows XP on, I need to keep the XP system intact though, I have started up and am using Ubuntu off the live CD, But I don't know where to go from here, I set up the install but when I try and re-size partitions it doesn't work, any advice?

---

### Post by teaker1s on 2007-01-07
scan disc and defrag before attempting to use live boot gparted cd

---

### Post by evildrummer on 2007-01-07
I tried but it was still on 1% for 20 mins so I thought it had crashed and I could just not need it, do I HAVE to defrag? How long would a 100Gb drive take?

---

### Post by Russty of Oz on 2007-01-07
I had the same problem with my new machine, so what I did was to use the live CD and use gparted to make a new ext3 partition from the unused space first.  Then do the install using that partition.

That worked for me.  

Good luck! 

Russty.

---

### Post by teaker1s on 2007-01-07
better if you defrag, it's possibly not defrag because of programs such as antivirus running in background try turning them off just while defraging
possibly use "msconfig"

---

### Post by Russty of Oz on 2007-01-07
By the way, it is a good idea to defrag first but if you are using the built in windows defragger that can take a l-o-n-g time, I use  Diskeeper, you can download the trial version and run it, it does the job much quicker than the basic one in windows.

---

### Post by ajgreeny on 2007-01-07
Definitely defrag windows first, maybe even do it twice, and I suggest you do it in safe mode, (keep tapping F8 at boot up, I think) but don't miss it out completely or you may have big problems after reducing the windows partition.

Defrag supplied with windows is very slow and can take a long time to start going as it is just collecting information at the start, but DO NOT OMIT THIS STEP.  If you do it twice, the second time will be much quicker than the first.

---

