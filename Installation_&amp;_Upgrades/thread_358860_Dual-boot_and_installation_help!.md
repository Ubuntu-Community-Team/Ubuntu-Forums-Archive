---
title: "Dual-boot and installation help!"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by PhoenixFhire on 2007-02-11
I'm trying to dual-boot WinXP Pro and Ubuntu 6.10 on a partitioned 100gb HD.  Not knowing which to install first, I made a guess and chose XP Pro.  That worked out alright.  So then I popped in the Ubuntu CD and rebooted.

The Ubuntu menu came up and tried to start/install it.  Then it goes into the splash screen thing but just stays there forever.  The CD drive isn't even doing anything.  I tried to use the safe graphics mode, but the same thing happened.

Is there a way to install without the graphics?  Should I have installed Ubuntu first?

Any help would be appreciated! Thanks!

---

### Post by Kateikyoushi on 2007-02-11
I would also install Windows first and then ubuntu, no need to install grub one more time after windows overwrites it.
Could you tell us more about what hardware do you use ? Then we might help you to proceed with the install.

---

### Post by PhoenixFhire on 2007-02-11
Thanks for the quick reply!

Intel D845HV Mobo
1.5 GHz P4
512Mb SDRAM (PC100/133)
Nvidia GeForce2 MX 100/200
Seagate 100Gb IDE 

Did I forget anything?

---

### Post by PhoenixFhire on 2007-02-11
Alright...So I tried the alternative CD, and still nothing.  I looked around the forums some more and someone said to take out "splash" from the boot options (F6).

I did so, and a whole bunch of lines came up.  Then it ended with**[17179636.140000] <0>Kernel panic - not syncing: Fatal exception in interrupt**


Does anyone know what this means?  How can I get around this?

---

### Post by Kateikyoushi on 2007-02-11
I looked around a bit, this could be hardware issue like your memory, can test it with the ubuntu live disc, select test memory after boot.
See this thread for example. [LINK]("http://ubuntuforums.org/showthread.php?t=343148")
You could also make a new thread with an updated title maybe that catches someone's attention.

---

