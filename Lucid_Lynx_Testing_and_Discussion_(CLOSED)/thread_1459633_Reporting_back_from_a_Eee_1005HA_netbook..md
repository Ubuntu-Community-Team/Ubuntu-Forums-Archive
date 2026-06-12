---
title: "Reporting back from a Eee 1005HA netbook."
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Captain Smiley Pants on 2010-04-21
Kind of a mixed bag here, but over all pretty good.

I'm not getting a splash screen during boot up, but I've recently ran the command:

```
sudo update-initramfs -u
```

I will get around to rebooting sometime today to see if this clears anything up.

I've upgraded to the latest kernel, but even with the default kernel that came on the disk everything was working pretty well hardware wise. Wireless works, dual monitors is working out, sound cards check out and are producing sound, the webcam is working... I can't seem to get any reading from the internal microphone. Not sure how I'd fix that either.

Hotkeys aren't working out, for the most part. Brightness (dark/light) keys work. Haven't tried the sleeping one. Volume keys don't work. Monitor key doesn't work. Seems like only the brightness keys work.

In all honesty, I was VERY surprised that ICS worked out this time around from my system, without having to set up bridge utilities or anything. Usually, the process of going through the Network Connections, selecting the Wired connection, and editing the IPv4 settings to the "Shared to other computers" method would not work and I'd have to screw around with network interfaces until giving up in failure. This is the first time my Ubuntu box has managed to share it's wireless connection through the ethernet port. Well done.

I can't seem to get any video acceleration going, as in if I go to the Appearance Preferences and try to change the Visual Effects to Normal, I'm met with a dialogue box saying it is searching for drivers and, even when the Normal box is ticked, there are still not effects. The video card for this system is the Intel 950 GMA, which I'm sure is ancient and should be covered by now. Effects worked in Mint 8, and the only reason I dropped 8 was because they didn't have an xorg.conf file for me to try and fix these sort of errors. Figured I may as well test out 10.04 and report back.

If anyone is looking for anything specific let me know and I could try stuff out.

---

### Post by ktmom on 2010-04-23
I don't have one of these (yet), but I was researching and I saw this link [http://code.google.com/p/acpi-eeepc-generic/](http://code.google.com/p/acpi-eeepc-generic/)

I wonder if it will help you with the hotkeys.

---

### Post by dingo on 2010-04-23
Adding acpi_osi=Linux to the grub2 boot options fixed most of the function keys on my 1005HA-MU. There's a bug report that talks about this fix here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518007]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518007")

---

### Post by Rowan187 on 2010-04-25
I've got the 1005HA and have Ubuntu Netbook Edition 10.04 Beta 2 installed. From the start I've had a few issues. First is yeah, hotkeys for sound and such.

2nd, Multi-touch doesn't work. I've tried the fixes for 9.10 and the 1005HA, but they don't work anymore. I'm assuming since they were HAL integrated.

3rd would be that I can't use any of the advanced appearance features. This little EEE can run Windows 7 Aero perfectly, I'm sure it can run Compiz... Maybe I'm missing something..

I know the RC update is out, maybe I need to update, does that fix anything?

---

### Post by barrieluv on 2010-04-25
I've always been under the impression that the netbook interface didn't work with compiz and therefore isn't installed.
I'm running vanilla desktop with compiz doing it's desktop cube switching thing.  
Same issue with the hotkeys, but I'll apply the half-fix for it at some point.
The only real issue is not being able to use the external mic when using Google Talk voice/video calls with Pidgin.
Otherwise I'm happy with the latest release. :)

---

