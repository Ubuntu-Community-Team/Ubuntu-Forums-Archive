---
title: "Discover crashes when trying to use it ..."
date: 2019-09-13
forum: Installation &amp; Upgrades
---

### Post by dagmann on 2019-09-13
always crashes

this is the only problem I have noticed so far since I installed it about an hour or more ago

is there a way to fix Discover crashing?

thanks in advance

---

### Post by #&amp;thj^% on 2019-09-13
There sure seems to be a lot of reporting going on with Discover, but can you include the return for:
```
plasma-discover
```
Most of the Old Timers here just use CLI for package management, but I get the need for a GUI for Newer Users, and there is always Synaptic.
If you want to help out you could also send a bug report, with:
```
gdb plasma-discover
```
and:
```
start
```
That will start a Debug output. 
BTW: Try a full upgrade, to see if all is well.
```
sudo apt full-upgrade
```

---

### Post by dagmann on 2019-09-13
Okay, I got it working, for now anyway.  First know that I am a Linux noob. 

I rebooted and during the boot I was able to get into a menu that allowed me to update all packages.

So I did that and then continued to boot and when in KB all was okay again. We shall see if all stays okay.

I was wondering if when Discover starts up that it goes to the Internet to retrieve the list that it displays,
if that is true then maybe the connection failed or timed out and that caused the crash problem.
 Just guessing here.

---

### Post by #&amp;thj^% on 2019-09-13
> **dagmann said:**
> 
I was wondering if when Discover starts up that it goes to the Internet to retrieve the list that it displays,
if that is true then maybe the connection failed or timed out and that caused the crash problem.
 Just guessing here.
With out seeing what the terminal says, your right just a guess.
BTW: Can you tell us how you got it working? This is very helpful to others.

---

### Post by dagmann on 2019-09-23
Solved

---

