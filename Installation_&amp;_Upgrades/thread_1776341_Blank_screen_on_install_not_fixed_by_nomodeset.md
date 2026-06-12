---
title: "Blank screen on install not fixed by nomodeset"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by CyClyst on 2011-06-06
Hello all

I have had this problem on another computer. After install on first boot my screen goes blank and says no VGA input (I do hear the little drum noise). I thought it would be a similar fix as last time (I followed these instructions: [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)) however that did not solve the problem! 


What are the next most common solutions to this? Thank you very much!

EDIT: The fix I tried was getting rid of quiet splash and  adding nomodeset to the grub boot command.

SOLVED: When I installed ubuntu I had "install updates" checked. I reinstalled without this and I was able to login. I am still having problems figuring out which driver is the right one to use for my graphics card.

---

### Post by CyClyst on 2011-06-06
Does anybody have any ideas??

---

### Post by Quackers on 2011-06-06
What graphics card is in use on each computer?

---

### Post by CyClyst on 2011-06-06
The one I am working on now has:

Nvidia GeForce 8600M GT


but the other one had some ATI graphics card (I used xforcevesa on that one)

---

### Post by wojox on 2011-06-06
Which version of Ubuntu?

---

### Post by Quackers on 2011-06-06
> **CyClyst said:**
> The one I am working on now has:

Nvidia GeForce 8600M GT


but the other one had some ATI graphics card (I used xforcevesa on that one)

That's interesting. I have the same card and I have never had any graphics problem with any Ubuntu live cd from 10-04 to date.
Does an attempted boot end with the Num Lock and Shift Lock keys flashing?

---

### Post by CyClyst on 2011-06-06
I will give more background:

I had vista installed on a laptop. One day it fell and some part of the monitor broke so I have resorted to just plugging it into a monitor.

I haven't been using it and since I was having motherboard issues with my new desktop I thought I could dig up my old laptop and install ubuntu 11.04 on it. So I tried resizing my partitions but when that failed (vista...argh) I decided to just wipe out vista completely and install ubuntu over it.

**SHORT ANSWER:**

I had vista installed, I wiped it out to install ubuntu 11.04 from disk. and no, no icons are flashing on the keyboard.

---

### Post by linuxinstalledfromhdd on 2011-06-06
Did Vista work before you installed Ubuntu?

---

### Post by CyClyst on 2011-06-06
Yes it did, although I was having a problem shrinking my partition which is a known downfall of vista ([http://www.ghacks.net/2009/01/11/windows-vista-shrink-volume-problems/](http://www.ghacks.net/2009/01/11/windows-vista-shrink-volume-problems/))

---

### Post by jramshu on 2011-06-06
I had a busted monitor on my compaq with an 8xxx series card and the gpu was detecting the busted monitor. I had to take it apart and disconnect the old monitor before I could get an external monitor to work. 
This is just my experience and may not apply to you.

EDIT: The exact card I have is :[GeForce 8200M G] (rev a2)

---

### Post by jramshu on 2011-06-06
> **CyClyst said:**
> Yes it did, although I was having a problem shrinking my partition which is a known downfall of vista ([http://www.ghacks.net/2009/01/11/windows-vista-shrink-volume-problems/](http://www.ghacks.net/2009/01/11/windows-vista-shrink-volume-problems/))

This really should be in another thread.

To get the most out of vista I did this:
Deleted every program I never used. 
Backed up and deleted all my personal files.
Used disk cleanup and cleaned out all the crap there.
Used disk cleanup and deleted all but most recent restore info.
Used System Mechanic to clear out reg errors.
Defrag.

That freed about 80 or so gigs.
Before that I could only get about 10 gigs out of it.

---

### Post by CyClyst on 2011-06-07
Vista is already off the computer...so that is all sort of superfluous. I did many things to clean up the vista install (a couple of third party defrag tools, tons of deleting and backing up etc) but that is all in the past



So you think the GPU is still detecting the broken monitor? Even though when the computer starts up it shows up on the external monitor all the way until ubuntu boots up (with the little drum diddle)? What should I do?

---

