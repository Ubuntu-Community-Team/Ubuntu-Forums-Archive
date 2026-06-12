---
title: "edgy-&gt;feisty upgrade failed but forum helped me fix it"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by cwgpress on 2007-05-20
Just a quick THANK YOU to all the people who have posted information here.:p Here's my story:

I tried to do an upgrade using all the automatic stuff. It was supposed to take a little over an hour to load and install packages. I fell asleep for several hours; when I woke up the screensaver was on, the activity light on the computer was off, and there was no response to either keyboard or mouse. I didn't hear any disk activity.

In order to get the puter to do anything at all I had to hold the power button in long enough for a forced power down. When I restarted, I tried the grub option for the same system I'd been running. It failed very quickly with something about block(0,0) having to do with /hda2 and kernel synchronization.

Once again I had to restart with a full power off sequence. I tried recovery mode for the same version, with the same result.

Again with the power off restart, I tried the previous version of Ubuntu from grub. The system appeared to boot normally but there was no desktop. The background came in but nothing else. Fortunately I remembered that ctrl-alt-shift-f1 would bring up a terminal, and that worked. Unfortunately I didn't have a clue what to do from there. I tried to run fsck on hda2 but it warned me against fscking a mounted device so I cancelled it. I decided to restart (sudo reboot).

At this point I let win2kpro boot and sat back to think about things a little bit. Later, I restarted again, using the previous Ubuntu to get to a terminal, and came to this forum from my new pc that's running Vista. I tried the standard upgrade [ gksu "update-manager -c"] but it wouldn't run because there were no working graphics. Looking over things people had tried to fix other problems, since there seemed to be no exact match, I tried running aptitude. It came up fine, so I tried to update.

Aptitude told me that I had to manually run dpkg to fix the problem. I did so [sudo dpkg --configure -a] and the system took off and ran with that for quite a while. Once it was done, I ran aptitude again, and the update was possible this time. I decided it was time for the acid test, so I restarted.

Amazingly enough, there were two new entries at the top of the grub menu. I picked the first one and I am now running Feisty. KEWL!

Chuck

---

