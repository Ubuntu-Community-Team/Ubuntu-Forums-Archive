---
title: "No video after splash screen"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by lyrrad on 2006-09-20
Maybe I posted my question in the wrong place (Video & Sound)the first time since no one has responded, so I'll try again here.
I'm new to linux and want to learn.

I've installed the Ubuntu package onto my machine,
but it comes up as "Signal Over Range!!" on my (LCD)monitor.

I have an nVidia RIVA TNT2 64 graphics card so I tried
the code listed on this page to load the legacy driver,
but it comes back saying that it is not available.

How do I get the legacy drive on? Or is that even my problem?

lspci -n | grep 0300
0000:01:00.0 0300: 10de:002d (Rev 15)
lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (Rev 15)

I have since found further direction on this site concerning this problem, but
still no progress.

I downloaded the legacy driver to a CD but I keep seeing "Unable to locate any
package files. Perhaps this is not a Debian disk." Or is there a way to connect
online from the command line?

Any advice would be greatly appreciated. Thanks

---

