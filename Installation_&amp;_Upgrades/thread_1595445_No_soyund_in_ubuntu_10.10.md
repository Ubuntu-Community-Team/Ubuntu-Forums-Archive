---
title: "No soyund in ubuntu 10.10"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by icchi on 2010-10-13
Hey guys,I did a fresh install of ubuntu 10.10 on my desktop pc and surprisingly there seems to be no sound for me.The sound preference menu also detects the hardware for sound,but "Test Speakers" option does not play any sound after clicking on "Test".

Heres the output of lshw -c sound command

```
root@Home:/home/ashwin# lshw -c sound
  *-multimedia            
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:20 memory:dbef8000-dbefbfff
```Some people have posted threads on similar issue but i couldn't find any solutions for it,moreover some of the users have sound in firefox  but  none outside from it.Can anyone please help me with this issue.
Thanks very much in advance


Sorry for the typo on the Thread Title :P

---

