---
title: "Ubuntu 10.04 OS Freezes / Clean Install"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by intellinus on 2010-05-02
I just did a clean install of Ubuntu 10.04, my PC was running 9.10 and 9.04 before, no problems.

No problems on install (received some: end-request: i/o error, dev sr0, ....errors but as far as I know this doesnt mean anything but Cd Rom door open)

When I started Ubuntu everything runs ok, (even audio that didnt worked on 9.04 ..finally)

After 1 or to minutes PC just freezed, everytime i restarted same thing. Tried using liveCD, id does crash anyway.

I downloaded another ISO using bittorrent, installed, same result.

When I open the Computer Monitor i see the System Memory scale up to 100%, then it alternates between processor 1 and 2, it goes to 100% then to about 9 and the other processor goes to 100 one at a time.

1.6 Mhz Intel
HHDD Samsung 160GB

---

### Post by oldfred on 2010-05-02
You have some process running away.

In terminal start top and see if you can see which software is consuming 100%.
top

I had this one or two versions ago and had to uninstall something to stop it.

---

### Post by intellinus on 2010-05-03
Problem is heavier than I think.
 
Ubuntu 10.04 FREEZES up in less than 5 minutes.
 
I wouldnt recomend to use it on production enviroment unless this bug has been detected and fixed.
 
Today I just started my pc and when I tried to write TOP it just Freezed.
 
Tried again, then TOP worked but when it was showing me that no more than 10% of RAM was used it freezed again.
 
I think we have two problems now: 
 
1. there is some process that takes 100% Ram resources in a one processor at a time.
2. PC freezes without any reason in less than a minute of starting.
 
Please let me know how can i help you to send you information for fixing this.

---

### Post by DavidTangye on 2010-05-03
I think I would boot it in recovery mode, wait a while to see if all is OK, and then choose to open a terminal. Wait a while again to see if all is OK. This might help indicate it its a kernel issue, or a bug in the graphics and desktop etc software. This would help narrow down the source of the problem.

---

### Post by intellinus on 2010-05-05
I think it may be something about network access, I can ping any address, but cant access to web pages through firefox. Sometimes it hungs up when trying to connect to the network.

I dont find recovery mode, did a clean install and it doesnt start with Grub. I reinstalled 9.04, trying 10.04 on liveCD option until this is solved.

---

### Post by oldfred on 2010-05-05
In my case it was not RAM but one or both of my cpus.

I added a system monitor to the top panel so I could see processor use. 

And I had a System, Administration, system monitor window open to track cpu & memory. Then in top I tried to see what was running when it went to 100%.

---

### Post by intellinus on 2010-05-10
The problem is that it freezes also while processors and ram are not 100%.

It just freezes in less than a minute from start.

I tried login in safe mode, it works perfect, also tried turning off all startup applications, it keeps failing.

I tried downgrading to 9.10 (which i used before) and also fails, it doesnt fail in 9.04 (the one I m using now)...strange behaviour.

---

### Post by mikeashelby on 2010-05-13
I'm not sure if this is the same issue, but I have a freezing problem. With mine though, it literally locks the whole system up. Can't click anything, system monitor stops up dating. Mouse moves about and keyboard lights will change, but nothing in terms of interacting with the computer.

It doesn't happen randomly - it happens when I try to run blender, or Virtual Box OSE (so far...).

---

### Post by garryzn on 2010-05-18
I had similar problem, I could log in, but after a minute or so the system froze.

The problem was in Visual effects.

I did this...
System / Preferences / Appearance - under the "visual effects" tab, check the radial button for "None"

Problem solved.

For some reason the "Normal" and "Extra" options caused the system to freeze, maybe some boffin out there knows why?

---

