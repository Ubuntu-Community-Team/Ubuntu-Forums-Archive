---
title: "0 for 2 - Black Screen - Intel Video Graphics"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by gtg on 2008-10-30
Tried installing 8.10 on two machines (Dell & HP) that have both been running 8.04 (and 7.10).

Dell: clean install indicates success, reboot, login, tom-tom sound, plain tan screen, then black screen
HP: run preview from CD, select language, eventually get to black screen after seeing plain tan screen

Dell: Intel 82845G graphics
HP: Intel 845GV graphics

What to do?

Thanks.

---

### Post by jerrylamos on 2008-10-30
Sounds like the same black screen problem I've been getting with Intel graphics since Aug 13.  Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

Jerry

---

### Post by gtg on 2008-10-30
Thank you.  I will try this tomorrow when I have access to the Dell machine again and will let you know how this works (or if I continue to be confused).

---

### Post by gtg on 2008-10-31
That's the ticket!!

Many thanks to jerrylamos for the helpful reply (actually "replies" - the same good advice seems to have helped at least one other person].

I've clarified a couple of steps (below) to the process list for people like me who are not so well versed in the obvious.

> **jerrylamos said:**
> Sounds like the same black screen problem I've been getting with Intel graphics since Aug 13.  Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Select "... (recovery mode)" option
At the Recovery Menu option list, select "root   drop to root shell prompt"
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

Jerry

---

