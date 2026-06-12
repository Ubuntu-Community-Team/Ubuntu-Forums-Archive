---
title: "Huge frame-rate drop"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by tenmoi on 2010-07-12
Hi all,

My machine: 
Lucid 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
Radeon hd 3870: 512 M of GRAM
ati driver: 10.6

Ati info:
lucid64:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3870
OpenGL version string: 3.3.9901 Compatibility Profile Context

Glxgears:
 glxgears
301 frames in 5.0 seconds
300 frames in 5.0 seconds
300 frames in 5.0 seconds
300 frames in 5.0 seconds
300 frames in 5.0 seconds

Compiz:
Is running great and everything else is very fast and responsive.


My problem is: I am running FLighgear and it is very unresponsive in regards to changing views. When I press v, it takes some 6 - 8 seconds to change views.

P.S.
I read that glxgears is CPU-bound but I have tested it on Fedora 13, which runs mesa, and I can get some 3000 frames/5 seconds.

Thank you.

---

