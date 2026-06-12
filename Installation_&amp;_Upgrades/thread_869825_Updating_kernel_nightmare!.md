---
title: "Updating kernel nightmare!"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by spanner510 on 2008-07-25
Hi this will be long as I'm trying to give a smuch info as poss!!
I did the usual updates last week to my kubuntu 8.04 system. however there was a kernel upgrade( I'm currently on x.x.22-14!). 

I use dual boot(2 hard drives!)with windoze xp and during the upgrade it asked me the usual update grub bit and I panicked and selected keep local version. So no update visible when I restarted. I then decided to back up my menu.lst and learn some more about it (using the excellent grub web page). I am no longer afraid:)

I then decided to remove the newer kernels from my system using apt so I could force the system to let me upgrade (which didn't work). So i then reinstalled the new kernel using apt and then selected use package maintainers grub instead of local.
Great I rebooted saw the new kernel however I couldn't boot into it. Due to a graphics problem so I copied my back up of xorg.conf back in and i booted x but only in 640x256 screen i then reinstalled graphics using envy. When I restarted I lost my new kernel and it seemed to go back to my old menu.lst file and put me right back at square one.

Incidentally on first boot new kernel fail a message came up in the command line which I caught only error in /var/lib..... and I think dpkg may have been in the line so I assume I have a missing file/config in there.

My question is where has this amateur(that's me) gone wrong and how is the best way to update the kernel from my position.
Also what steps should I have taken during my boot problem
Sorry this is longwinded but I'm trying to supply as much as I can!

---

### Post by Archmage on 2008-07-25
I think envy did remove the new kernel.

First update your whole system and look if you still have this kind of problem.

---

### Post by spanner510 on 2008-07-25
I thought envy only installed the graphics though I wasn't expecting that to happen.
Annoyingly my system is not showing any updates available because the kernel is still in my /lib folder although it isn't listed in /boot or menu.lst obviously.
Oh and compiz fusion is really annoying when your running 640x256 resolution:lolflag:
Do you know of any purge or clean up commands that would clean my system up at all?

---

