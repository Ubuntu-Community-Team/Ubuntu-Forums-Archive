---
title: "Feisty Install Hangs"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Kyyn on 2007-04-21
I recently downloaded and burned to the i386 Feisty installation CD. Whenever I select "Start or install Ubuntu," The screen goes blank, except for the following message at the bottom:
```
Int 14: CR2 cf800000 err 00000000 EIP c020c384 cs 00000060 flags 00010007
Stack: c00f7da0 c03f129b c0371d8c 00000002 c00f7da9 000f7da0 00000000 00000000
```
Then it hangs. Also, when I try the same with the Edgy CD, the screen simply goes black(actually goes black, the monitor is still on). I have previously installed Edgy, but I want to do a clean install.

I have tried the noapic, noacpi, and nolapic commands, to no avail.

Help is greatly appreciated.

---

### Post by Swab on 2007-04-21
Looks like some sort of memory problem.

Run the RAM checking utility.. perhaps you have a hardware issue.

---

