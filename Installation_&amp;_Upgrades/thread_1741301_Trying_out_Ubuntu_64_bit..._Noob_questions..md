---
title: "Trying out Ubuntu 64 bit... Noob questions."
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by PickleSuit on 2011-04-27
I got Ubuntu 64 bit on a cd and I'm using it as a boot cd OS. I want to use it as a solution for more RAM on my computer because my computer can have 8gb of ram but XP 32 bit doesn't recognize anywhere near that. (HP Media Center m7650n with XP)

I figured out how to check out the ram usage with the free command and its eating up RAM like crazy without running. Is this just because it is booted from a CD? or is it that the 64 bit recognises alot of ram because its using this much?

             total       used       free     shared    buffers     cached
Mem:       2047576    1464764     582812          0     172552     701144

Any help would be appreciated.

---

### Post by mikewhatever on 2011-04-28
Let's look at the output of free -m:

```
~$ free -m
             total       used       free     shared    buffers     cached
Mem:           993        974         19          0         10        601
-/+ buffers/cache:        361        631
Swap:         1027          0       1027

```

You can see that 361MB is used while 631MB is free. The line you posted is only part of the output, so that it's impossible to tell what the memory usage is.

---

### Post by PickleSuit on 2011-04-28
So this is what it is using with nothing else open.  This is less than what windows XP was using. Is this a normal amount for the 64bit Ubuntu?
            total       used       free     shared    buffers     cached
Mem:       2047576    1538800     508776          0     190080     810280
-/+ buffers/cache:     538440    1509136
Swap:            0          0          0

---

### Post by mikewhatever on 2011-04-28
I don't know about WXP, but according to the output, 538440KB of your RAM is used, and the rest is free. Since free RAM is a wasted RAM, Linux uses it for caching stuff, and in your case, 810280KB has been cached. That number should grow as you use the system, because more stuff will get cached.
For a more user friendly representation, look at the System Monitor.

---

