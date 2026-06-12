---
title: "libgtk1.2 exists but programs say no such file or directory"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by Elliander on 2008-11-19
I am trying to get a game to run, written for Linux, but I keep getting stuck with errors.

> elliander@elliander-ubuntu:~$ sudo linux32 /usr/local/games/creatures3/creatures3
Welcome to Creatures 3!
Querying language
/usr/local/games/creatures3/langpick: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
elliander@elliander-ubuntu:~$ 


I figured that meant I didn't have libgtk1.2 but...
> 
elliander@elliander-ubuntu:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
elliander@elliander-ubuntu:~$ 


And just to be safe, I checked the Synaptic Package Manager and it shows up in there too.

So I have the correct files. Yet it insists there is no such file or directory. What am I doing wrong? I am running Ubuntu 8.10 AMD64bit with all 32bit libraries installed.

---

### Post by Elliander on 2008-11-19
I just tried reinstalling everything shown as "libgtk" but same problem persists. Been checking various forums but have yet to find any mentioned solution.

---

### Post by Elliander on 2008-11-19
I just tried something else that didn't work:

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

I installed that, and but still get the same error.

---

### Post by Elliander on 2008-11-19
I made sure to install the dev files and every gtk I could find. I still have the same error.

Hello? Anyone out there?

---

### Post by Elliander on 2008-11-19
I tried something else that just gave me a different error. So far I have yet to see Ubuntu run any program made for either Linux or Windows that wasn't included in the Synaptic Package Manager. I am starting to feel like Ubuntu is just a closed garden like AOL and it's really annoying me.

> elliander@elliander-ubuntu:~$ export LD_ASSUME_KERNEL=2.2.5
elliander@elliander-ubuntu:~$ sudo linux32 /usr/local/games/creatures3/creatures3
sudo: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory

---

### Post by Elliander on 2008-11-19
In this thread someone had the same problem with the same errors with a similar program but what helped them didn't help me. I really need help!

[http://ubuntuforums.org/showthread.php?t=476514](http://ubuntuforums.org/showthread.php?t=476514)

---

