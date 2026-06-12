---
title: "dpkg --configure -a crashes system"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by diomede on 2008-06-15
I'm somewhat new to Ubuntu, so bear with me..  not even sure if this is in the right category, in which case tell me to repost.

I'm running Hardy on a Thinkpad T43. and synaptic says there are 73 updates to be installed.  When I try to do so, I get the message

>> dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

However when I run that command, it starts trying to install linux-restricted-modules-2.6.24-18-generic, but doesn't make any progress and locks up after a while.  I can still move the mouse and open things, but nothing executes, and eventually things lock up.  Thoughts?  I've looked at some other threads on problems running dpkg --configure -a, one suggested cd-ing into /tmp and installing the package from there, but that again gave me a crash.

Thanks!

---

### Post by oldos2er on 2008-06-15
Try the command "sudo aptitude install -f"

---

### Post by Rocket2DMn on 2008-06-15
Did you run it with sudo?
```
sudo dpkg --configure -a
```
It does require these superuser privileges to execute correctly.

---

