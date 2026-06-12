---
title: "Trouble installing ubuntu on a philips x59"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by dAnnny on 2007-08-07
Hi there, i have been reading afew posts on these forums about people having trouble installing fiesty on a philips x5*. 

I have tried the fixes sugguested but most require the install to acctually start, my problem however is that when i select install on the live cd ( or alternate cd) the program freezes on the scrolling horizontal bars that sugguest something is loading ( under the ubuntu graphic). 

I am new to linux and ubuntu but have previously managed to get versions working on my desktop without hassle, i like this distro and would much like to get it working on my laptop.

Any help would be much appreciated.

---

### Post by merlinus on 2007-08-07
Post specs, including RAM and video card.

-merlin

---

### Post by dAnnny on 2007-08-07
INTEL CORE 2 DUO T5500 Processor 1.66GHz
1gb ram
224MB Intel GMA 950 Integrated Graphics

Vista installed on hdd (sata), partition ready for ubuntu install.

---

### Post by merlinus on 2007-08-07
How did you create the partition for installing ubuntu?

Also, there may be difficulties with your graphic adapter, as you stated.  It may also be related to sata.
-merlin

---

### Post by dAnnny on 2007-08-07
i shrunk the windows partition on vista, it is still ntfs but i remembered from last time that ubunutu had good partition tools when you install it, i assume the file system can be changed?

I tried the alternate live cd install again and it got to the point where it detects hardware and hangs on 0%.

---

### Post by merlinus on 2007-08-07
As long as you shrunk the vista partition using its disk manager, it should be good to go with ubuntu.

But clearly something with your hardware is causing problems, and it may be the sata drive.

Hopefully someone more knowledgeable about that will chime in.  Usually the alternate install cd does not have video problems.

-merlin

---

### Post by neott on 2007-09-11
Hi, you will find it is the wired ethernet card that is hanging your system :)

I succesfully got feisty running on my X59 last week using info I found in this thread:
[**http://www.linuxquestions.org/questions/showthread.php?p=2775746#post2775746**]("http://www.linuxquestions.org/questions/showthread.php?p=2775746#post2775746")
post 72 links to this site: [**http://www.fitzenreiter.de/averatec/index-e.htm**]("http://www.fitzenreiter.de/averatec/index-e.htm") where there are links to torrents for a custom live CD with the offending modules disabled.

This should be all you need to get up and running.

Hope this helps :)

---

### Post by marktuson on 2007-12-27
Will this problem be properly addressed in Hardy?

I'd love to have a proper Linux on my laptop, and am downloading the fixed version as we speak, but I believe that it means that updating can break the installation, doesn't it? Will the problem be fixed for the next version?

---

