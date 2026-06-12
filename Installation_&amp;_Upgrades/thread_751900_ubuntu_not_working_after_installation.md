---
title: "ubuntu not working after installation"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by asiancamel on 2008-04-11
Ubuntu gutsy 32bit Live CD works without problem. After installation, I could see the menu, but when I choose the first one which is normal selection, I could see "starting ...", then black screen with the round mouse cursor, ubuntu freezes. HD led light is off, so no access to HD, just hanging there. 

The following is detailed information of my pc, any suggestion will be appreciated.

MSI paltium P35 motherboard,
Intel Dual Core2 Quad 6600 cpu,
4G 667 memory,
two sata 250G HDs,
MSI nvinia ns8400gs video card,
extra d-link network card,
wireless-G card,
benq 20" widescreen lcd monitor.

I have NTFS partition on first sata HD 50G, in the rest I installed PCLINUXOS Gnome 2008(NOT miniMe). This is the second preference linux, and it works on my hardware. But I really want my Ubuntu working.

I don't know what the difference between the live cd and the one installed on my HD, why the live cd works, but installed one does not. 

What should I check? please advise..
I am assuming that one or more steps in the startup process failed, but I don't know which one, how can I check that?

HELP!!!

---

### Post by asiancamel on 2008-04-11
Finally, the problem has been solved.

My MSI NS8400GS card has VGA and DVI port, I connected both to my monitor. I have to disconnected the DVI to let Ubuntu startup correctly, then I was told to load NVIDIA driver, then reboot. At this time, connect the DVI.

With my old pc which has ATI 9000 Pro card, I connected both, no such problem.

:guitar:

I see the beautiful ubunt color again!!!

---

