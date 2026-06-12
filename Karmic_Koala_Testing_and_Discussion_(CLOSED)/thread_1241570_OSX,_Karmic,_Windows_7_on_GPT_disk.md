---
title: "OSX, Karmic, Windows 7 on GPT disk"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by entangled on 2009-08-16
Trying to get Mac OSX 4.11, Kubuntu (Karmic), and Windows 7 (trial) all to boot on a GPT disk using Grub2. My experiences may be useful to someone.

It works but the order of install seems to matter.
I eventually installed Mac OSX first (from a CCCloner backup of GPT disk, also has rEFIt), booted Karmic Alpha3 live CD and made new partition for Karmic.

Installed Karmic and it booted from Grub. The grub entry for Mac OSX failed.

Then installed Windows 7 in a fourth partition.

rEFIt then offered OSX and Windows boot but no Grub.

Had to reboot Karmic live CD to install grub to disk again.

Now rEFIt offers OSX, Linux and Windows, but Linux and Windows both go to grub menu.

Grub menu can boot Linux, Windows 7 and OSX, but OSX is useless because it does not have mouse and keyboard (both USB) when booted through grub. OSX boots OK if direct from the rEFIt menu.

Subsequent update to grub has resulted in a new grub entry for a Vista bootloader (on the same partition as Windows 7). If I use this new entry I get Windows 7 but with lower resolution (1024x768 instead of 1280x1024).

Conclusion - Grub2 can certainly boot all these OS on a GPT disk but not quite cleanly yet.

---

