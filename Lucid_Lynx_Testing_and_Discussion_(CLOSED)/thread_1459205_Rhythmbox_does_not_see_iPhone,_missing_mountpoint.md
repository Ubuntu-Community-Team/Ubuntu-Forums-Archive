---
title: "Rhythmbox does not see iPhone, missing mountpoint"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by RatSAT on 2010-04-21
I just upgraded my desktop from karmic to lucid beta2 and wanted to sync some music to my iPhone, but sadly Rhythmbox does not see it.  gtkpod also does not detect the device, however I can browse the device in nautilus.

Now the strange thing is I previously also upgraded my netbook to lucid as well and there the rhythmbox sees and can can sync to the iPhone without problem.

I tried to see what is different and noticed that on my netbook a mountpoint to my iPhone is created in ~/.gvfs, but this mountpoint is not created on my desktop. I think now that rhythmbox uses this mountpoint to detect the device. 

How can I fix this so that a mountpoint is created when I plug in the iPhone?

---

### Post by RatSAT on 2010-04-21
even when manually creating a mountpoint using ifuse, rhythmbox fails to see it.

My desktop using 64 bits ubuntu, my netbook 32 bits... if it matters.

---

