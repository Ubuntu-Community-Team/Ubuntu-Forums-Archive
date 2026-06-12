---
title: "Install Help...Please!"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by sarsippius on 2008-04-24
I have a Dell Dimention 3000.

I have tried both Ubuntu and Kubuntu, but they both lock up during the initial boot.

No matter if I choose to install or start Ubunt, I get to the same point, where it locks up the computer.

I currently have Ubuntu 7.10 running on my system, and would like to upgrade to 8.04, but I am having major heck getting past this one point.

Where it gets stuck:
When the CD is booting, it gets to the part where the bar is moving back and forth.  Then it starts to load.  It only gets about 1/8 of the way and locks up.

If anybody has any ideas, I'm all ears!

Thanks in advance!

---

### Post by Partyboi2 on 2008-04-24
When you are at the main menu screen press F6 to change boot options and change the word splash to ```
nosplash
``` then press enter to boot.

---

### Post by sarsippius on 2008-04-24
Thanks for the tip.

Here is what error I got this time around:

[61.229509] b44: Invalid MAC address found in EPROM
[61.229552] b44 ssb0:1: Problem fetching invariants of chip, aborting

Setting Keymap  [OK]
Preparing Restricted Drivers  [OK]
Setting System Clock
Starting Basic Networking  [OK]
Starting Kernel Event Manager  [OK]
Loading Hardware Drivers  (LOCK UP)

Is there anyway to see what might be going on to cause the lockup?

Thanks!

---

### Post by Partyboi2 on 2008-04-24
can you post your system specs please

---

### Post by sarsippius on 2008-04-24
3GHz Intel
80Gb Drvie
512Mb Memory

Not too sure on the motherboard though.  Ubuntu 7.10 runs perfectly on this same machine.

---

