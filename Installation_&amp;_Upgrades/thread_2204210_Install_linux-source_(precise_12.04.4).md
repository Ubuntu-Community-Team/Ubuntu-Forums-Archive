---
title: "Install linux-source (precise 12.04.4)"
date: 2014-02-07
forum: Installation &amp; Upgrades
---

### Post by alexander13 on 2014-02-07
[FONT=Courier New]I install the package [FONT=Courier New]"[/FONT][/FONT]linux-source[FONT=Courier New][FONT=Courier New]" (Ubuntu 12.04.4)[/FONT]
[/FONT]
apt-get install linux-source
[FONT=Courier New]
it has the old version 3.2.0.[/FONT]
[FONT=Courier New]
The kernel source version must be 3.11.0-xx!

Where can I find the kernel source for [FONT=Courier New][FONT=Courier New]Ubuntu[/FONT] [/FONT][/FONT][FONT=Courier New]12.04.4[/FONT]?

---

### Post by TheFu on 2014-02-07
12.04 has different kernel levels based on how you've maintained the machine to get to that point. 
I have 3.2.x and 3.8.x kernels installed here based on which 3rd-dot release I installed. Different kernels for different releases.

* 3.8.0-35-generic - on a 12.04.3 fresh install box
* 3.2.0-58-generic-pae - on an older, upgraded from 12.04.0 install
Both are currently listed as "Ubuntu 12.04.4 LTS" in the lsb-release.

If you just want the newest kernel, it is available at kernel.org.
If you want the kernel installed on your current system, **uname -a** will get you the package name to be installed.  

At this point I went to see if I could find the source for my kernels in Synaptic.  I found the headers - install the meta-package for your specific system (linux-headers-generic-pae on one and linux-headers-generic on the other) to get those.  I see 2 packages with Linux source. Both match my 3.2.0.58.x kernel, which makes sense (that is the box synaptic is running under).  Looked using aptitude on the other box - it is a pure server running 3.8.0.35-* - and found "linux-source-3.2.0{a}" - not what was expected.

The correct header files ARE available based on the running kernel.

After all that - I haven't a clue where to get the 3.8.x kernel source, but felt the search was helpful to others.

---

