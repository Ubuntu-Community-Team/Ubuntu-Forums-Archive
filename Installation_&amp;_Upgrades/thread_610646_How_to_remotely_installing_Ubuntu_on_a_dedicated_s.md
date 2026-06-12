---
title: "How to remotely installing Ubuntu on a dedicated server?"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by mneisen on 2007-11-12
Hi, 

consider the following situation: I have a dedicated server in a remote location. I can run an NFS-booted "rescue system" on the machine which is debian-based. I have SSH access to this rescue system. I cannot enter any CD-ROMs into the machine, and I do not have a VNC-style graphical access to the system.

Is there a way to install Ubuntu/Kubuntu on such a system? Is so, how?

Kind regards
Martin

P.S.: I read [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux) but this seem to require graphical access to the system which I do not have.

---

### Post by bartoni on 2007-12-05
I'm in the same situation.  Did you work this out?

---

### Post by mneisen on 2007-12-05
In the end, I did not have to work this out since the data center my server in question resides in ([http://www.hetzner.de](http://www.hetzner.de)) now offers Ubuntu images; I did some modifications (RAID level, ...) though.

So, no, I do still not know how to install Ubuntu remotely if you have some sort of net-booted rescue system.

Sorry :-D

---

### Post by calvinkim on 2008-03-11
I just found following link,
[http://www.underhanded.org/papers/debian-conversion/remotedeb.html](http://www.underhanded.org/papers/debian-conversion/remotedeb.html)

I'm not sure if this will work out well as I just found it out and didn't try it yet.

---

