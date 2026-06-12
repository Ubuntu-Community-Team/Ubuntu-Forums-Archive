---
title: "problems with 7.10 upgrade"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by alexh on 2007-12-04
HI,

I have been sing ubuntu on my laptop for a few months now and i have never really had any problems with. I was using the 7.04 release but last week I upgraded to the 7.10 one and since then have been having a few problems; firstly my laptop doesn't like coming out of standby any more, it sometimes does and sometimes doesn't. Second i no longer have any sound, i still get the system beeps from the pc speaker when i do things like pull the power lead out but i don't get any other sound I can't watch a film of listen to music or anything, and i am fairly sure it isn't the speakers themselves as I have tried headphones etc. 

I have had a play and I can't seem to work out how to fix it - I am not too fused about the standby problem but i relly would like to get the sound sorted.

Cheers

---

### Post by mikewhatever on 2007-12-04
To get you started on the sound problem [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by alexh on 2007-12-04
that page was very helpful and i have got it sorted, 

cheers

---

### Post by khurrum1990 on 2007-12-04
Hi, I can help u about ur standby problem. You r probably using Ubuntu kernel 2.6.22-14. That kernel suspend is broken and there has been a bug report. You r going to have to use Ubuntu kernel 2.6.22-12 that was on the Ubuntu 7.10 beta release, I had the same problem. You can check which kernel u use by typing in terminal:
"uname -r"
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136387](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136387)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151016](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151016)
Visit these pages on info on the bug and where to download the 2.6.22-12 kernel for Gutsy.
Good Luck!

---

