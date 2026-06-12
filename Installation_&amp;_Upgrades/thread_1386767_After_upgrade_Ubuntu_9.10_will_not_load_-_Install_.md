---
title: "After upgrade Ubuntu 9.10 will not load - Install Kernal first message"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2010-01-21
9.10 Karmic Koala:

I have been checking and upgrading my Ubuntu at regular intervals.  My last upgrade included a system upgrade, if I recall 2.6.31-18....  BUT when I load it it stops and says "ERROR:  You need to load the kernal first"

I don't understand..  How do I fix this, please

---

### Post by tachuela on 2010-01-21
Post:
```
uname -a
```

---

### Post by Jonners59 on 2010-01-21
> **tachuela said:**
> Post:
```
uname -a
```
I was not sure what you were after in the uname -a, but took a guess it was either to be entered at boot or in the terminal in some way, so I gave them all a bash.

When in terminal I got the following
Linux ubuntu 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

This is the level before the one I have downloaded, naturally as the new one, that will not load is 2.6.31-18 -generic

Hope this helps.

---

### Post by Jonners59 on 2010-01-23
This is getting worse.  I have upgraded two further laptops since.  One has been a success but the other is also failing with a similar error.

It is slightly different.  It will start to load in Recovery but stops at:

"1.312024] Clocksource tsc unstable (delta = -280526511 ns)"

Can anyone help please?  As 2 out of three machines have now failed loading the new upgrade I am wondering if there is a fault in the new upgrade install.:-k

---

### Post by tachuela on 2010-01-23
How did you install the Video Driver initially?

---

### Post by Jonners59 on 2010-01-23
All I did was select System, Administrator Update Manager....

---

### Post by tachuela on 2010-01-23
How about 'Hardware Drivers'?
You might need a Video Driver in your new kernel

---

### Post by Jonners59 on 2010-01-27
Sorry Tachuela did not get a notification that you'd left a message.

How would I know, and how would I identify what I need?  My Toshiba Laptop uses NVIDIA GoForce Go 7600 for video.  The drivers were fine before, and when installing Ubuntu it included an NVIDIA device manager.  It seems to be OK.

The other machine is an old Dell.  Don't know what driver it has.....  But it worked OK before.

The Toshiba has now started throwing up a new alarm and will not install any further updates.  It seems to have stopped. at this "broken" point.  I have enclosed a screen shot FYI.

When updating it stops and throws up the enclosed warning.  It also, now, says there is a GNOME error too.  When I follow the instruction to load the updates manually in the Terminal window it gets to a point where it says *SOMETHING LIKE* "found Linux ubuntu 2.6.31-17-generil........" and keeps repeating this and goes no further for no matter how many hours it is left

---

### Post by Jonners59 on 2010-01-29
Screenshot

---

### Post by Jonners59 on 2010-02-01
[size=5]**help me please someone!!!!!!!**[/size]

---

### Post by hero1900 on 2010-02-01
i got this messege when i got no space in my system are you sure you got free space for upgrading
???

---

### Post by Jonners59 on 2010-02-01
Ah, interesting you say that.  I have another query out about that same subject.  I have a 300G HD partitioned in to three of which 150G is for Documents and the other is split in to 95G for Windows Vista (original OS) and Ubuntu, then a partition I assume created by Ubuntu, certainly not myself called something like winRE and is only a few Gig and not full.

The 95G partition has plenty of space too, but I am getting storage warnings and now I am starting to get Gnome start up warnings and upgrade issues tool.

I am glad you say they MAY be related, it means my suspicions are confirmed and fixing one will hopefully fix all.

The scan seems to indicate that the HOME/USER folder is at capacity (16G) as are Cache and Host.  My intrigue is that my experience of Windows is that folders grow with demand and partitions are fixed size.  I thought these were folders, so why do they not grow???  And now knowing they do not, how do I make them larger????

Why are they so small when they are for files, though I do not use them for such as I have a separate area for this?

Look forward to your feedback...  Please exuse my stupidity, I am learning.

---

