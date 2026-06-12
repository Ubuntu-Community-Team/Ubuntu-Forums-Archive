---
title: "Netbook 11.10 install: missing buttons, dead pointers, and sleeping netbooks"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by brownbat on 2012-02-15
Been a while away from testing Ubuntu, and so I decided to throw it on my HP Mini 110 netbook using pendrivelinux.

A few things hit me off the bat that I want to jot down here before I start digging through launchpad:
1) On the "choose your avatar" stage of install, the "Next" / "Back" buttons are hidden below the screen, and the window cannot be moved back onscreen. All the other windows squeezed into my screen, so this seems like a straightforward "check monitor height to determine window size for every install window" fix.

2) I fell asleep during the biggest part of the install, so I missed some of the magic. When I woke up, my netbook would not. It had also gone to "sleep" (the screen was black, but all the lights were on), but no combo of buttons would rouse it short of a hard reboot. 

On reboot, I'm met with a claim that the disk drive for /dev/<something?>/ is not ready yet. However, after this warning, I was allowed to boot into the machine. Maybe that refers to my pendrive, which I casually left in the drive by mistake. After updates I'll have to try a reboot without that usb stick in there...

Even though I connected to a wired connection and indicated updates should be included with the installation, there were 328 updates left to install after that initial boot. Maybe this is expected, as some updates might come in stages, or maybe my internet connection got fried in the middle of the night, hard to say.

Oh, showstopper, the pointer would not respond to the touchpad.

Currently installing updates. Maybe using this as a dry run before throwing the 12.04 beta at it to look for bugs prerelease.

No specific question, but if any of these issues prompt strong reactions, feel free to jump in.

It's good to be back.

EDIT: Touchpad works post updates. :D

---

