---
title: "Intel D845 will not install"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by ddavidd on 2011-03-20
Intel desktop board D845 GEBV2/D845 PESV, presumably Intel on-board graphics, Celeron 2 GHz, upgraded to 1 GB RAM

Computer ran a long time without problems under W2k,the only change was a new DVD burner, which I have now taken out again. I would like to install Ubuntu. 

The computer is absoutely determined not to install ubuntu, I have now tried everything I know for two days. 

Firsst CD, installed 10.10 without problems on another computer last week, endless problems, eventually I was able to run "check CD" and there were 3 file errors.

Burn a second CD. No file errors. 

The installation often stops for no apparent reason (typically blinking dash top left, no CD or disc noises or lights for a long time).

I have also tried the "try out" option, which sometimes got as far as a request to log on, although I had not configured any user. I found some suggestions what to try in the forums, but have not got so far again since.

I have tried switches acpi=off, noapic and nomodeset, seem to help but not solve problem.

The installation seems to go further (almost finished) when the screen resolution is very coarse (cannot see buttons at bottom of windows), which perhaps indicates a graphic driver problem? 

When I see an error, (seldom) examples are:
stop at ? print_cpu_info +0x2/0x129
syscall_call +0x7/0xb
error code +0x73/0x78

Tried 9.04, ended with error:
Kernel panic - not syncing: VFS:unable to mount root fs or wn-block (104.1)

Anyone got any suggestions?

---

### Post by ddavidd on 2011-03-20
This site offers Intel graphics drivers:
[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

but also says:
In general, Intel graphics driver is well integrated in Linux distributions so users won't worry about the driver setup. It should work out of the box with recent distributions.

---

