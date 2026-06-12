---
title: "New install, mouse and keyboard don't work"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by konedima on 2012-12-20
Just tried installing 12.10 (using Wubi). The installation in Windows goes fine (aside from Wubi only putting the files GRUB needs on the Windows C: drive, which isn't my boot drive, so GRUB can't find them, but I just have to put them on the right drive, so that's not the problem).

The actual problem is that my mouse and keyboard don't work once I get to the login screen. Not at all (can't even toggle num lock or anything on the keyboard). A tiny wireless (has its own USB dongle) mouse/keyboard combo does work, but it's FAR too uncomfortable (and slow) for prolonged use - it's designed mostly for presentations (but it is good enough to use it to try to fix my proper mouse and keyboard). I seem to recall having the same problem in 12.04 (didn't play around with that version much) but not before. It also doesn't work running 12.10 from a USB drive. I've already tried using various solutions dredged up by Google and none I've managed to find work. I'd be grateful for any advice.

Hardware:
Intel Core i7 2600K
Gigabyte GA-P67A-UD4-B3
8GB RAM (Corsair... although that probably doesn't matter)
Dual EVGA GeForce GTX 570
Various HDDs and an SSD (I'm trying to run Ubuntu from a Wubi virtual partiton on a WD HDD... again, probably not important).
Triple boot between Windows XP/Windows 7x64/Ubuntu 12.10 amd64 (using Wubi)

The keyboard and mouse that don't work are a Razer BlackWidow Ultimate and a Razer Naga Epic (I've tried both wired and wireless for the mouse, it doesn't seem to make a difference).

---

### Post by konedima on 2012-12-21
Update: I tried plugging the keyboard/mouse into different ports. Surprisingly, it worked. Both worked when plugged into my USB3 ports (unfortunately I only have two, and better things to use them with, so not really a permanent solution). The mouse would work sporadically when plugged into one of my front USB2 ports, but stopped entirely after a few minutes.

However, after installing the Nvidia drivers (from their website, I couldn't seem to find a way to do in a more Ubuntu-like manner (such as additional drivers or grabbing it from a repository) that didn't make it so Unity didn't load after I logged in - but I digress) - after installing the Nvidia drivers, the mouse will work reliably when plugged into the front USB ports, but the keyboard won't - it receives power, but won't accept any input (can't even toggle num lock)... wait, possibly never mind, while I was typing this, for kicks I decided to try plugging my keyboard into one of the front ports, it didn't work and the mouse stopped responding until I plugged it into one of my USB3 ports. Might be fixed on a reboot. I'm too tired to test that part right now.

Could it be something relating to chipset drivers or something? I know the USB3 ports aren't controlled by the chipset - the chipset I have doesn't natively support USB3.

---

