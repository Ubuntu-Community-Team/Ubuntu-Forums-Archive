---
title: "Nvidia Drivers Causing Kernel Panic"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rfdeshon on 2010-04-07
Hey all, I posted this in the normal support forums. Reposting it here since this is the better place for it (I was having a problem finding the Development forum, one of those days).

Just installed Ubuntu 10.04 beta 1 x64 on my MSI EX630 (AMD Turion X2, GeForce 9300M, MCP77 chipset). After the first install, I ran all the updates, installed the nvidia drivers (using the restricted driver manager) rebooted and found that it kernel panicked every reboot no matter which kernel I selected, even if going into single mode. Not a friendly KP either, a blinking scroll lock & caps lock, no error on the screen kind of KP.

Wiped, reinstalled, rebooted, installed only the nvidia drivers (didn't run ANY other updates), same thing. I've never seen a driver cause a KP even when booting into single mode like this. Does anyone have any ideas? I'm at a total loss here.

---

### Post by cariboo on 2010-04-07
Have you tried the nouveau drivers? If they work without a kernel panic, you may want to try the drivers from the [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") ppa, you should be able to use special effects with it.

---

### Post by rfdeshon on 2010-04-07
Provided that nouveau is used by default (which it is as far as I can tell) it doesn't cause kernel panics. It's only after installing the nvidia proprietary driver, though the Hardware Drivers interface, that my system KPs on every boot. I'll try the drivers from the ppa you provided when I have a chance to tweak with it.

Well, I've found one issue with the nouveau drivers. Switching VTs doesn't work. I just get a frozen image of the last thing gnome was displaying. Switching back to F7 unfreezes the screen and things continue as expected.

---

### Post by rfdeshon on 2010-04-07
I hate to jump on the hating plymouth bandwagon... but after doing some further research it does seem likely that my laptops problem lies in a problem between the nvidia driver and plymouth. While I do love good open source, I'd really like to be able to use all (or at least most) of the features of the graphics card I have, so while nouveau may be a stop-gap solution, I'd really like to see the proprietary drivers working. If theres anything I can do to provide feedback to help track the actual problem down, I'd like to know. I'd rather provide information on where and what the actual issue is as opposed to making do with nouveau.

---

### Post by rfdeshon on 2010-04-07
Sorry for the triple post here, the updates from edgers ppa work so far without noticable problems.

---

### Post by ToxicBurn on 2010-04-08
I am use to the Icon popping up on the tp of my screen telling me there are hardware drivers for my nvidia card and all i do is select enable and do a reboot. I need this to work 100% as i am a World of warcraft junkie and if the Nvidia drivers do not work i will not be doing an update to Lucid untill i know for sure things are not broken.

---

