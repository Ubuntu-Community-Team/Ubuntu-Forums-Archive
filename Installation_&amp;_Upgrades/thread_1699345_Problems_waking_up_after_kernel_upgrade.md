---
title: "Problems waking up after kernel upgrade"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by ubu-man on 2011-03-03
I am running Ubuntu 10.10 on a Lenovo T60 and am having problems waking up from sleep every time I update the kernel.

I just got the upgrade from 2.6.35.25 to 2.6.35.27.

The problem I see now is that I get this message when coming back from sleep (I coped it down since after the message I couldn't do anything else):

pciehp 0000:00:1c.0 pcie04: Device 0000:02:00 already exists, cannot hot-add
pciehp 0000:00:1c.0 pcie04: Cannot add device at 0000:02:00


I checked my pci listing and the device on 0000:02:00 is my ethernet adapter:

shahars@shahars-ThinkPad-T60:~$ lspci | grep 02:00
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller

Anyone? :confused:

---

### Post by ubu-man on 2011-03-03
By the way, this issue isn't resolved when I fall back to a previous kernel version

---

### Post by ubu-man on 2011-03-05
Just did another update (including some driver updates), but I am still getting the same problem.

Hasn't anybody else seen this issue?

---

### Post by ubu-man on 2011-03-06
Well, I must have done something, because I don't see the problem any more!

Here is what I think made the difference (since just before doing so, I saw the same crash):
I put the computer to sleep, this time with the AC power in. Then I woke the laptop up and VOILA, I get the password.

I'd still like to understand what the made the difference (and hopefully get a more permanent fix for it).

So if anyone can understand from my diagnosis what went wrong, and what made it right, I'd be really happy.

---

