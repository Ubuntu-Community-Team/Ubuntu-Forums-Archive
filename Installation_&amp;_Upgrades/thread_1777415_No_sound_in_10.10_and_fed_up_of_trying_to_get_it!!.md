---
title: "No sound in 10.10 and fed up of trying to get it!!!!"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by skeebs on 2011-06-07
Hi,

I've been trying various suggestions of how to get sound in ubuntu 10.10 from people who had similar problems when upgrading but they keep making the situation worse! I've had to re-install it because I followed something from the ubuntu support pages and it wouldn't let me past logging in. Now trying someone else's solution I've lost the sound that came out of the speaker test in system>preferences>sound!

All the obvious things were covered like check for mute/user privileges set to audio etc.

If it's any help, output of sudo lshw -c sound

> *-multimedia            
       description: Audio device
       product: MCP67 High Definition Audio
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:20 memory:fdff8000-fdffbfff
  *-multimedia
       description: Multimedia audio controller
       product: 5880B [AudioPCI]
       vendor: Ensoniq
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ENS1371 latency=64 maxlatency=128 mingnt=12
       resources: irq:19 ioport:ec00(size=64)


I've had a problem with the sound on my motherboard sound card so stuck another one in which worked so have two possible ones to use.

I am so so fed up of trying to sort this out and I'll probably have to re-install this version for the third time just to get back to where I was so I'm willing to try any sensible suggestions right now!

Thanks :(

---

### Post by mörgæs on 2011-06-08
Do you get sound in a live boot of 11.04?

---

### Post by skeebs on 2011-06-14
DONE IT!!!

For everyone going through the same problem, and tried all the obvious volume related things, my problem was a MISSING DRIVER.

I went to system>administration>additional drivers and activated NVIDIA accelerated graphics driver and now everything works: youtube, mp3s, cds.

Hope this helps people and you are spared the endless, soundless searching I had to go through to solve it :D:D:D

---

