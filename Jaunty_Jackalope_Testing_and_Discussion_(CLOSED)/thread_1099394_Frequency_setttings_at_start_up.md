---
title: "Frequency setttings at start up"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by waspbr on 2009-03-18
Hello everyone,

I have been running the latest jaunty  on a 64 bit laptop, though lately I have noticed something a little worrying. during start up the computer will heat up a lot  (fan blowing), and if it is not from a cold boot it may not even start. 

and when it does start I notice that the frequency settings are set to performance instead of onDemand. is there a way to set the frequency to onDemand by default? ie. which file should I edit?

---

### Post by taavikko on 2009-03-18
It's a known bug at the moment, but no idea when to be fixed at all

You can use tools from "cpufrequtils" to set governor for cpu's

---

### Post by scaine on 2009-03-19
Bug details here :
[https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/344252](https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/344252)

---

