---
title: "Help! Won't boot, locks up just as desktop appears"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by pikaia on 2007-08-16
Hey everyone.

I hope this gets someones attention as I've seem to run out of ideas and the ideas of one very helpful person.

I've been trying to get Ubuntu (Feisty) to load/boot on my main PC for a while now. I could not get ANY linux LiveCDs to boot (NOT ubuntu, kubuntu, fedora, or goblinx). I installed ubuntu onto a back up drive thru another system and am trying to boot with that drive on my main system.

It is now the ONLY drive on the machine. It freezes at various points during the boot, anywhere from right after the Ubuntu logo, to the Nvidia logo, to right after loading the desktop.

This is a quick rundown of *most* of what I've done.

- I've checked the BIOS, I do NOT have onboard video, and it is NOT enabled.
- I have tried booting with the vesa driver
- my RAM is working fine
- I had gotten an xserver error which says no screen but haven't seen that one in several boots
- I've installed the nvidia driver (all three) nv, nvidia and the nvidia-glx-new and tried booting with each individually to varying degrees of failure.
- I've swapped out the video card for another and it still will not boot.

Here is a list of basic information
- PC hardware
- Chaintech VNF-250
- 512MB 7600 GS AGP
- AMD 64 2800
- 1.5 GB RAM

I appreciate any and All help/comments. thanks.

I apologize for any confusion, but I'm trying to get as much info in here as possible. Thanks.

---

### Post by kraylus on 2007-08-16
son, it sounds like ubuntu's just an innocent bystander and that your old hardware is the problem. not being able to boot off of any cd is a pretty big red flag. you can tell me nothing's wrong with your hardware all day long, but i'd be disinclined to believe it based on your symptoms.

the freezing when it loads the video could suggest it doesnt like your driver selection OR the video hardware is conflicting with something else.

is the system usable WITHOUT trying to load X? have you tried mucking around the command line at all?

is your system not fully installed yet? you mentioned your boot discs not working so you installed it over the network? you want to explain what that entailed?

sorry if you gotta explain from scratch dude, good luck,

ryan

---

