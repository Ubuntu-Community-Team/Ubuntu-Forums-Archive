---
title: "Synaptic Package Manager can't download packages"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by dooberheim on 2011-08-01
I isntalled Ubuntu 10.04 LTS in a dual boot configuration with Windows 7 (new i5 desktop, 8 GB DDR3) , and after a few gliches solved, Ubuntu runs.  The problem I have is when I try to install software with the Synaptic Package Manager, no packages can be downloaded.  Also, after I attempt this, no other software can connect to the Internet (even if that software was able to connect before).  Rebooting restores connectivity.
 
Anyone dealt with this problem before?  I searched for other posts where people had this problem, but the solutions don't apply to my situation.  Thanks.

---

### Post by jerrrys on 2011-08-02
have you tried clicking on the reload button in synaptic package manager?

or open a terminal and enter 

sudo apt-get update

and post any errors that you get

---

### Post by dooberheim on 2011-08-03
p { margin-bottom: 0.08in; }  I got it to work after I opened SPM and saw a window saying I needed to run:

```
<ID removed>f@GeneMachine:~$ sudo apt-get install -f
[sudo] password for<ID removed>: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
<ID removed>@GeneMachine:~$ sudo dpkg --configure -a

```So I did, and got: many packages downloaded until I hit a:```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```Perhaps because I had SPM open already?

Anyway, I tried to download the package I wanted "startupmanager" and it worked, and I still have Internet connectivity.  So far so good.

I'll try to install some other stuff and see if it's really fixed.  Thankis jerrys.


On reboot this morning, I was able to download another package and install it, and am still able to reply to this thread.  So I guess it's working - not quite sure why, but sometimes one shouldn't care so much about that.

Mark

---

### Post by jerrrys on 2011-08-03
y (/var/lib/dpkg/), is another process using it?

you can have only one package manager open at a time

---

