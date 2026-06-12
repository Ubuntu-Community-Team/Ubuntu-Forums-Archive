---
title: "Synaptic crashes, Ubuntu 11.10"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by manishp on 2011-10-18
Hi,

I updated to Ubuntu 11.10 a couple of days back and ever since my synaptic package manager has stopped working. 
If I try to run synaptic from the terminal, I get the following error:

manish@manish-HP-Pavilion-dv5-Notebook-PC:~$ sudo synaptic
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check

I know that ubuntu 11.10 does not install synaptic by default but that shouldn't make my original installation to crash, right?

I also tried to reinstall synaptic by using
sudo apt-get purge synaptic
sudo apt-get install synaptic
but I still get the same error.

Please advice

---

### Post by haresear on 2011-10-18
Another thread with the same problem:

[http://ubuntuforums.org/showthread.php?t=1864099](http://ubuntuforums.org/showthread.php?t=1864099)

Unfortunately, no solution found yet.

---

### Post by haresear on 2011-10-19
This apparently is a bug that has been reported. This thread has a solution in post #10:

[http://ubuntuforums.org/showthread.php?t=1854470](http://ubuntuforums.org/showthread.php?t=1854470)

---

### Post by 23dornot23d on 2011-10-19
The answer in the bug is this 

> 
If I toggle the screen reader on & off again (System  Settings->Universal Access->Screen Reader), it stops crashing.    If I enable the screenreader again, it starts crashing again.


---

### Post by johanlt on 2011-11-08
Toggeling screen reader on and off makes no difference om my system. Synaptic still crash every time, just flashing for a second at launch.

---

### Post by BillyBoa on 2011-11-08
I had this problem while I was trying 11.10 beta.
Then it disappeared and I feel that the bug was solved.
So if you update your system it should correct the bug.

---

