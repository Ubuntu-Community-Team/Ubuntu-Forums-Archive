---
title: "Can't Install virtualbox on Gutsy, Help!"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by bokorpop on 2007-11-15
When I try to get Virtualbox going, here is the error message I get: 
[IMG]http://i235.photobucket.com/albums/ee27/bokorpop1/d.jpg[/IMG]

I have tried these solutions in terminal(gleaned from other forums), but  I don't understand what they mean:

"justin@justin-desktop:~$ sudo apt-get install --reinstall
virtualbox-ose-modules
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package virtualbox-ose-modules is a virtual package provided by:
 virtualbox-ose-modules-2.6.22-14-server 6
 virtualbox-ose-modules-2.6.22-14-generic 6
You should explicitly select one to install.
E: Package virtualbox-ose-modules has no installation candidate"

AND

"justin@justin-desktop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for justin:
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}"

---

### Post by scorp123 on 2007-11-15
How about reading the error message and actually doing what it suggests? VirtualBox fails because your user account doesn't yet have the proper permissions ... just as the first few lines of the error message tells you. :)

As for how to fix this:
[http://ubuntuforums.org/showthread.php?p=3766472#post3766472](http://ubuntuforums.org/showthread.php?p=3766472#post3766472)

And also --as the error message tells you-- logout and login back again or the changes will not take effect (a full reboot is not needed).

---

### Post by daengbo on 2007-11-15
scorp123 --
This forum frowns on RTFM-style answers (in this case, RTFEM). Keep it civil, eh?

---

### Post by bokorpop on 2007-11-15
problem solved

---

### Post by scorp123 on 2007-11-16
> **daengbo said:**
> This forum frowns on RTFM-style answers (in this case, RTFEM). Maybe so. But if the error message already tells you how to fix the problem that actually caused the error ... I mean, sorry. It can't get "friendlier" than that. All that's needed now is just the user actually to *read* this thing - the solution is already right there, on-screen, displayed in the error message. 

I mean it's not like in Windows where you get meaningless (from a Human language POV) errors telling you cryptic nonsense such as "Error -503, Exception at 00:FE:3D:33:blah something" ...

---

### Post by bokorpop on 2007-11-16
Listen, some of us are new to Ubuntu. I read the damn thing, but I didn't know HOW to do what it said.

---

### Post by scorp123 on 2007-11-16
> **bokorpop said:**
> Listen, some of us are new to Ubuntu. I read the damn thing, but I didn't know HOW to do what it said. Well ... look at the other thread I linked to. Same problem. But this guy made it clear from start that he knew what to do but didn't know how. That's OK, nobody blames him for this. I just find it strange that even though you --guessing from your answer above here-- saw and understood what needs to be done typed in commands that have nothing to do with the solution to the problem. That's sorta 'dangerous' because if you type in commands without really knowing what they do you're only going to worsen your situation. That's what I sort of "have an issue with" ... So please don't take this personally and sorry if I was kinda rough there ... :)

---

