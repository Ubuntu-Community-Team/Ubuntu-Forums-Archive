---
title: "Upgrade from Feisty to Gutsy on Mac Mini - Kernel panic"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by danb35 on 2007-11-25
I just tried upgrading my Feisty installation on an Intel Mac Mini (1.66 Core Duo) to Gutsy, using the upgrade manager.  Everything appeared to proceed smoothly through the download, upgrade, and installation, but when I tried to reboot, I got the following on the screen:

[ 21.981823] i8042.c: No controller found
[ 21.982684] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

When I boot from the Gutsy CD, the drive is accessible.  However, the root partition is at /dev/sda3, which I think corresponds to grub notation of (0,2).  How can I fix this?

---

### Post by danb35 on 2007-11-25
Well, looks like I might have gotten it fixed after all.  Here's what I did, and it seems to be working:

[LIST]
[*]Booted from Gutsy CD
[*]Mounted /dev/sda3 to /media/sda3
[*]Verified that /boot/grub/menu.lst on /dev/sda3 had references to (0,2) instead of (0,0)
[*]Tried to run the update-grub script, and noticed that it was assuming that the root was /dev/hda1
[*]Edited update-grub to default to /dev/sda3
[*]Ran update-grub again
[/LIST]

The system now boots fine.

---

### Post by jken146 on 2007-11-26
I have the same problem.  How do you edit update-grub?

---

### Post by taistelutipu on 2007-11-29
Hi everyone,

finally I found someone with a similar problem. I don't know what to do anymore with the kernel panic so I hope someone can help me with it.

My sister ran Feisty on a COMPAQ Evo N610c laptop and everything worked fine. When she upgraded to Gutsy the first error was that the internet didn't work anymore. Since she had experienced already network problems in her dorm earlier she thought a restart might do the trick. But on restart the internet still didn't work. She tried to fix it in the network settings and for this she needed root rights. But the root login window didn't work either. It just froze. She decided then to restart again and then the computer didn't even boot anymore, it stopped right in the beginning of the booting process with the infamous message:
[ 8.898347] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

Does the upgrade from Feisty to Gutsy include also a kernel update? If so, it is possible that the kernel needs to be rebuilt or recompiled? When I entered the error message above in google I got hundreds of hits which hinted at similar problems when upgrading the kernel. On of the suggestions was the following: "You can either include the filesystem support in your kernel or create an initrd to load the module at startup."
Another problem could be the lilo entry not matching: "The problem was in lilo, i asumed that my loader was pointing to hda3; when in reality it was pointing to hda1"

I'd like to know how I can get these informations, e.g. which kernel version my sister uses or how her grub (she's not using lilo) entry looks like. The problem I encounter is that the blinking cursor at the end of the message freezes, i.e. I can't write anything in the command line.
Is there a way how to interrupt the erronous booting procedure before it freezes to get to these informations? I searched for hours in forums to get help for the problem but I didn't find anything. I guess it is considered common knowledge so that no-one includes it in the instructions how to deal with kernel related problems.

I run a debian distribution at home which my friend set up for me. I know how to maintain it but I never set anything up myself from the very beginning. So when it comes to the basics I'm a beginner. Further I haven't been present when he set up my sister's computer so I don't know anything about it (kernel version, file systems, modules etc.) I can't access anything with the knowledge I have right now since the booting process halts after a couple of seconds.

I suspect that the update somehow messed up the root account since my sister could not log in anymore, for example the directory appointed to root does not match reality anymore or something like that.

Can anyone tell me what I can do about it? My sister recently changed from Windows to Linux so she knows even less than I do. My friend mentioned above lives now in another country so he can't help us with it and I'm now in charge of our distributions. Thank you very much in advance for your advice. It's much appreciated.

Best wishes
taistelutipu

PS: Do you need any other technical specifications of the laptop? Which ones? It will be a bit hard to get them because I don't have the computer here, my sister lives far away but I'll try my best.

---

