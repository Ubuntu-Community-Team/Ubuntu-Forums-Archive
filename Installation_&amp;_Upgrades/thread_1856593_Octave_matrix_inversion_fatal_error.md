---
title: "Octave: matrix inversion fatal error"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by creatron on 2011-10-08
Matrix inversion  not working. Octave was reinstalled with the same problem. This however works on various other platforms, (I tested the same octave version on open-suse 11.4 and it works- as it should be, for many moons)  

History:
Unbuntu 11.04 (desktop) => new install, just a week in operation, all updates loaded.  Problem detected. All default modules was re-installed.  Problem still exist, then all additional octave modules available in Synaptic Package manager was installed, with the same result.

Problem:
gerrie@open-suse-ubuntu:~$ octave
GNU Octave, version 3.2.4
....bla bla bla
Octave was configured for "i686-pc-linux-gnu".
 ....bla bla bla

octave:1> A=[1,2;3,4];
octave:2> B=inv(A);
panic: Illegal instruction -- stopping myself...
attempting to save variables to `octave-core'...
save to `octave-core' complete
Illegal instruction
>

uname produce the following:
Linux open-suse-ububtu 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 athlon i386 GNU/Linux

Stunned,
Any ideas?

---

