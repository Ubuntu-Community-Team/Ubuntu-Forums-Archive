---
title: "HELP!!! - What 2 packages came yesterday - X not running anymore"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by AndreasMeier on 2005-06-22
Hi together,

I have Kubuntu Hoary running on my T42.
Yesterday I fetched the update for my apt-sources which are the standard, including universe.
I was able to update 2 packages.
The second one was tcpdump and the first one I didn't remember.

Fact is now, that my system starts, but when X is starting, it results in a black screen, no messages or anything.

Now my questions:
1.) Did anyone have (perhaps) the same problem ?
2.) Did anyone remember the first package (I think it starts with "g*" )
3.) Is there somewhere a logfile, where I can read, what packages are updated yesterday?

When I start in recovery mode, I'm able to start x via "sudo startx", but with messages, warnings about fonts etc., sorry I'm currently not able to give you the full messages.
But X is starting there.

Please help. I need a system, where I can work with, where I can rely on.

Thanks in advance,
regards,
Andreas

---

### Post by AndreasMeier on 2005-06-22
Can anyone give me please an answer ?

How can this happen, that 2 single packages can "destroy" a system? 
Are the packages not tested, or what? 

Sorry, I'm kind of pis..d off.
Thats the second time I ran into the same problem.

---

### Post by Lunde on 2005-06-22
Here's my log for the last few days. Let me know if you want anything furter back
[B]
Commit Log for Wed Jun 22 09:29:23 2005[/B]

Upgraded the following packages:
sudo (1.6.8p5-1ubuntu2) to 1.6.8p5-1ubuntu2.1
tcpdump (3.8.3-3ubuntu0.2) to 3.8.3-3ubuntu0.4
[B]
Commit Log for Tue Jun 21 09:07:19 2005[/B]

Upgraded the following packages:
chkrootkit (0.44-2) to 0.45-2~5.04ubp1
gaim (1:1.3.0-1~5.04ubp1) to 1:1.3.1~5.04ubp1
gaim-data (1:1.3.0-1~5.04ubp1) to 1:1.3.1~5.04ubp1
libnspr4 (2:1.7.8-1ubuntu2~5.04ubp1) to 2:1.7.8-1ubuntu2~5.04ubp2
libnss3 (2:1.7.8-1ubuntu2~5.04ubp1) to 2:1.7.8-1ubuntu2~5.04ubp2

Hope this helps..

---

### Post by AndreasMeier on 2005-06-22
Thank you very much !!
But where can I get this information? Which log do you mean?
Hope I dont have to re-install the whole system and can go back to the older versions of the packages.

Regards
Andreas

---

### Post by TheRealEdwin on 2005-06-22
Try ```
sudo apt-get install at-spi
```. It worked for me in another thread.

---

### Post by Lunde on 2005-06-22
[QUOTE=AndreasMeier]Thank you very much !!
But where can I get this information? Which log do you mean?
Hope I dont have to re-install the whole system and can go back to the older versions of the packages.

Regards
Andreas[/QUOTE]

Open Symnaptics, then:

File > History

---

### Post by AndreasMeier on 2005-06-23
The hint with File=>History
was great.
Can I somehow save this, e.g. per command line ?

Thanks in advance,
Regards
Andreas

---

### Post by Lunde on 2005-06-23
[QUOTE=AndreasMeier]The hint with File=>History
was great.
Can I somehow save this, e.g. per command line ?

Thanks in advance,
Regards
Andreas[/QUOTE]
 I'm sure it gets the information from a log file somewhere, hav'nt checked yet.

---

