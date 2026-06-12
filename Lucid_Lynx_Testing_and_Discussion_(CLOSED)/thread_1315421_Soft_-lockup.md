---
title: "Soft -lockup"
date: 2009-11-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by celticbhoy on 2009-11-05
After todays updates I am getting a weird boot up, everything works ok when booted but I get a psychedelic usplash and then it drops to text saying :-

BUG : soft-lockup - cpu#0 stopped for 61s [network manager]

(wording might not be exact) it then drops to xsplash and works fine until I shutdown and get the weird usplash again!

The only changes to vanilla install is the bootup ppa added.

Anyone else getting similar?

---

### Post by VMC on 2009-11-05
> **celticbhoy said:**
> After todays updates I am getting a weird boot up, everything works ok when booted but I get a psychedelic usplash and then it drops to text saying :-

BUG : soft-lockup - cpu#0 stopped for 61s [network manager]

(wording might not be exact) it then drops to xsplash and works fine until I shutdown and get the weird usplash again!

The only changes to vanilla install is the bootup ppa added.

Anyone else getting similar?

Your right, its usplash and not xsplash as I thought. That colorful usplash came with the newest kernel. Maybe a change in one of the modules your computer didn't like. Anything in the var logs?

---

