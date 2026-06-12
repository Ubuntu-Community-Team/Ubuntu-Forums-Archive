---
title: "Lucid reboot problems (ACPI-related?)"
date: 2010-02-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2010-02-16
I thought I'd check to see if anyone else was having a similar problem (or had heard of it before).

My Acer laptop has started to not reboot correctly, instead hanging in POST. It then reboots itself and hangs again, and if I press the power button to power off it immediately powers back up and hangs! If I remove the battery (and AC supply) for a couple of seconds, reinsert and power on it boots fine.

Normally I'd think - hardware issue. But it only happens when I'm rebooting from Lucid! If I reboot from Windows (or OSX) it's fine and reboots correctly every time.

The problem started a couple of months ago and I put it down to the new kernel. I'm getting a load of ACPI errors printed to the console so I thought no more of it. About three weeks ago the problem abated slightly, which coincided with a new NVidia driver. Again, I thought, great, fixed. Yesterday and today, however, every time I reboot it hangs in POST. It's a little annoying.

The only difference is that I'd disabled wireless via nm-applet (I thought I'd try a CAT cable instead - and wow, faster network, surprise!). I'm going to try ripping the wireless cards out and see if it makes a difference.

If nothing else works I'll have to go back to a clean install and see if it's down to a PPA I've added. :(

I think my question was - has anyone else had anything similar?

---

### Post by ratcheer on 2010-02-16
I have another thread on this, but I am posting to say I have a similar issue. Sometimes Lucid installation fails on my machine, but other times I have gotten seemingly perfect installs that reboot, successfully, at the end of the installation, but then will never reboot again. They don't even get far enough to give me any messages about what might be causing the problem.  Tim

---

### Post by dino99 on 2010-02-16
if plymouth is installed, remove / purge it.

---

### Post by VMC on 2010-02-16
> **dino99 said:**
> if plymouth is installed, remove / purge it.

When I remove plymouth I always purge it: '*sudo aptitude purge plymouth*'. Otherwise there's other error messages on bootup.

If removing plymouth fixes your boot up issues then you need to re-install it and join one of the launchpad bug discussions to help debug plymouth:

[Bug#511175]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/521175")
or
[Bug#518352]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/518352")

Just to name two of Plymouth problems.

---

### Post by jfernyhough on 2010-02-16
Well, removing plymouth appears to have fixed it. Two reboots with different combinations of hardware insertions (e.g. USB headphones and Wacom Graphire which I thought might have had an effect) and two successful POSTs.

I'll keep an eye on it and have a look at Launchpad.

Thanks peeps! You're all :KSs

---

