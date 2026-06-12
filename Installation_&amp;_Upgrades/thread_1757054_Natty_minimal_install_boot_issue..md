---
title: "Natty minimal install boot issue."
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by Madspyman on 2011-05-13
I did a command line install of Natty from a minimal install cd, I've done this before (Karmic, Lucid, Maverick) and never had any issues, however this time it wouldn't boot to the command prompt so I could login. Instead I got a blank screen followed by my monitor turning off.

I the hit ctrl+alt+delete and rebooted, same thing happened blank screen, monitor shutoff. After hitting ctrl+alt+delete again it rebooted, but this time grub loaded (grub is good) so I boot into recovery and got to the command prompt that way. I installed xorg and reboot to see if I could get to a command prompt, no dice. 

A few reboots later it's back into grub then recovery, I installed gdm and then reboot, a few seconds later gdm popped up just fine.

Problem is I don't want a display manager, I'm happy with using startx if needed, how can I get Natty to boot to the command prompt, and why is it only working with a display manager installed? 

I might also mention the Ubuntu Plymouth text boot never shows. In fact I only see purple at the recovery selection menu.

---

### Post by kacker on 2011-05-13
Here are a few suggestions:

1. Try redevicing the boot menu from the package sort startup

2. If the boot file is corrupt, the OSW might have to be reset before boot

3. The bootable usb might have 3.3rr tft missing from it. You can download that easily

Let me know if it works.

---

### Post by Madspyman on 2011-05-13
Re-installed (command line install) from a Maverick minimal cd and everything booted fine, so I ran "sudo do-release-upgrade" to see if upgrading to Natty this way would solve the problem. 

I was watching the updates install and everything seemed to be going fine, but then the screen went black (like a monitor shutoff) I let it sit for a few seconds then hit esc and the screen came back and it was finishing the upgrade, after it asked me to reboot, I did, but back to the same problem I was having after my minimal install from the Natty cd. I tried hitting escape, didn't help this time, didn't help last time either. 

I may just switch back to Maverick, just cause Natty has some weird boot problems. I've never had graphical issues after a command line installation before. In fact thought a minimal installation was supposed to be the answer to the graphical issues caused by a regular install with Unity.

Again, booting into recovery mode from Grub and installing xorg, and a display manager, graphically solves the blank screen at boot problem (I'm sure users having problems with a graphical boot envy my problem), however I still can't figure out how to get this thing to boot to the command line. Everything else works seems to be working fine though.

---

### Post by Madspyman on 2011-05-13
Found this,
 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658")
 
Followed the solution there and the problem was solved.

---

