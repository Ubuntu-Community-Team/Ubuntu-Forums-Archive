---
title: "Slow applications after 12.04 upgrade"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by leptonrover on 2012-05-10
I have just upgraded to 12.04 and my computer is now very slow on all applications.
Up to 5 secs from mouse click to response. 

The only problem I noticed during the upgrade was in the last stage, cleanup, when the upgrade stopped and put up a notice re a problem but it did not stay on screen long enough to note it.
I have restarted a couple of times but no change.
I would appreciate help in diagnosing the problem.

Is there a pointer in the fact that routines run in terminal seem OK. 
e.g.
roger@rdg-desktop:/$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)        
roger@rdg-desktop:/$

---

### Post by 2F4U on 2012-05-10
There can  be a couple of reasons why applications are running slow. First of all you should tell something more about your hardware. Second, what is the situation regarding memory, how much is installed, how much used. Do you have a swap partition? What processes are running?

---

### Post by leptonrover on 2012-05-10
Thank you.
I attach a  .odt file which contains the output of :/$ lshw - all 12 pages, which I ran after consulting several other postings on this forum. I am afraid it means very little to me. However I do note that there are 4Gb of memory.

Applications I am currently running:
Firefox browser - which I also note has come in for some criticism 
Libre Office
Gramps - family history database
Gwenview

:KS

---

### Post by leptonrover on 2012-05-10
You also asked about partitions. Not too sure about that, my system was set up by my son who is my Linux expert but he is 120 miles away.
However I believe my main disk to be in 2 partitions with a RAID system in operation.

---

### Post by leptonrover on 2012-05-12
I have moved forward a bit.
I concluded that the delays occurred when movng between windows/applications or when scrolling within an application. 

I decided to try Unity which had to be installed- it was not installed on th 12.04 upgrade. That seems to have cured the problem. Working in Unity does not seem to have the same problems.

I now need to put my efforts into making best use of Unity and see how we go.

---

