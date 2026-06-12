---
title: "Kernel panic on fresh 14.04 install on Barebone Brix Pro i5-4570R"
date: 2014-06-28
forum: Installation &amp; Upgrades
---

### Post by zeke3 on 2014-06-28
[COLOR=#333333][FONT=UbuntuRegular]I recently upgraded from the smaller AMD barebone brix to the brix pro. The new PC seems to make Ubuntu 14.04 crash on boot, a bug which I can't see anyone with the same PC having (too early?). I've attached the full log but here are the exact variables in play which, in this debugging case, are quite small (thankfully!):[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Brand new GB-BXi5-4570R. Corsair 4GB Kit (2x2GB) DDR3L - 1333 SOD/MM Crucial 256GB SSD The rest is not relevant (keyboard, mouse, ethernet)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]With a clean hard-drive, I've installed and reinstalled ubuntu 4 times, tried with different HDDs (not the SSD) and even with multiple Ubuntu bootable installs (different USBs and redownloading the ISO). Once the install is done, I reboot and works fine. I run the first update and restart and then I get that log. On one of the reinstallations, it didn't even get to the updating part, crashed on the first reboot. I tried installing as little as possible to see if something in particular is breaking it but all I can tell is that it happens in that update (I can restart multiple times before that with no problem).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]The big error comes towards the end of the log and seems to be a kernal panic error, known cause of malfunctioning drivers maybe?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][IMG]http://i.stack.imgur.com/l86u4.jpg[/IMG][/FONT][/COLOR]

---

### Post by w3#4F%M@§yAKt2 on 2014-09-19
FYI - I have Brix Pro 4770R - and I'm having exactly the same issue with ubuntu-gnome.
However Xubuntu 14.04 - installed without a hitch. Also - I have no idea.

[https://cdn.mediacru.sh/DGObOxYW-667.jpg](https://cdn.mediacru.sh/DGObOxYW-667.jpg)[IMG]https://cdn.mediacru.sh/DGObOxYW-667.jpg[/IMG]

---

