---
title: "How I got wine to not crash with mci sound library"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by izak on 2007-03-12
I encountered the following error under wine 0.9.32 (and older versions aswell), which caused the application (Apprentice - a free program to play 'Magic the gathering' over the internet) to crash:

fixme:mci:MCI_LoadMciDriver Couldn't load driver for type L"WAVEAUDIO".
If you don't have a windows installation accessible from Wine,
you perhaps forgot to create a [mci] section in system.ini

This error was fixed (in wine 0.9.32) by changing a line in system.ini (take note that I don't really know what I'm doing! But it worked, the application now runs without crashing).

replace "waveaudio=mciwave.drv" with "waveadio=mciwave.dll"

I suspect a typo, since the installation doesn't contain a file named mciwave.drv, but does contain a mciwave.dll...

Hope this helps anyone out there with the same problem!

---

