---
title: "Install Issue"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by sparky100 on 2005-11-12
I have tried to update Hoary to Breezy using Synaptic and the install guide. Unfortunately, the upgrade will not start X. I have tried various options to correct this to no avail and have decided to reinstall..

Using the Breezy CD CD I do not get an option to reuse my existing partitions only to erase the whole disk - if I use the manual partition option I can see my partitions. I am correct  in assuming that if I don't select an option to erase my disk it will reuse the existing partitions?

Any suggestions as to the best way forward.

Simon

---

### Post by aysiu on 2005-11-12
[QUOTE=sparky100]I have tried to update Hoary to Breezy using Synaptic and the install guide. Unfortunately, the upgrade will not start X. I have tried various options to correct this to no avail and have decided to reinstall..[/quote] What specifically have you tried?

> 
Using the Breezy CD CD I do not get an option to reuse my existing partitions only to erase the whole disk - if I use the manual partition option I can see my partitions. I am correct  in assuming that if I don't select an option to erase my disk it will reuse the existing partitions? Manually editing the partition table allows you the option to reuse existing partitions.

> 
Any suggestions as to the best way forward. Yeah, I had my install borked when I upgraded to Breezy using dist-upgrade. I found a clean install is best. My advice would be to use a live CD of some kind to recovery your data--then, just do a clean reinstall, perhaps now creating a separate /home partition so that new reinstalls won't erase your data.

If you don't have a live CD available, you may have to back up using the command line. I'm assuming you can boot into Breezy--you just can't get to a graphical user interface?

---

### Post by sparky100 on 2005-11-12
Thanks for the advice 

I now have X working...solved by reinstalling the X fonts base package

Although no sound... this was fine in Hoary ... my sound card ENSONIQ is not detected- another post loooming

Simon

---

