---
title: "Compiling a new kernel in Hardy Heron loses audio"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by rlb1961 on 2008-06-19
Okay, so I am a relative noob when it comes to Linux, but I am a pretty quick study.  I have a home-built system with the following configuration:

Intel Core2Duo processor
ECS 7100/610 motherboard
EVGA nVidia 8600 GT video card with 512 Mb vram
2 Maxtor 250-GB SATA HDD
4 GB RAM
Ubuntu 8.04 (kernel 2.6.24-19-generic)

Ubuntu installed with no problems, but I was having the usual problems with the video drivers loading above 4 GB.  If I remove 2 GB of RAM, I can get the nVidia driver to work correctly.  I tried running the 64-bit kernel, but ran into some problems with Flash and other applications.  I tried installing the 32-bit server kernel, but the nVidia driver wouldn't compile because the standard Hardy kernel has Xen enabled.  So I decided to try to compile a custom kernel to enable the HIGHMEM-64GB option.

I followed the instruction on the tutorial here on the site.  I copied the existing config file and edited it using "make xconfig".  The only change I made was to enable the 64GB memory option.  I saves the config and successfully built the kernel - or so I thought.

After installing the kernel and rebooting, I was able to log into the new kernel successfully.  However, when I tried to go to a virtual terminal (Ctrl+Alt+F1 - F6), I got a multicolored screen with random text scattered about and no prompt.  I was able to return to my Desktop with Ctrl+Alt+F7, but that was all.  I also discovered that my audio no longer worked.

Does anyone have any idea what may have happened? :confused:

---

