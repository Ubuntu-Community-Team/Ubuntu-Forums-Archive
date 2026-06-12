---
title: "Ubuntu on MSI Mega 865"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by Torben Lund on 2006-06-20
I am trying to get Ubuntu to work on my MSI Mega 865 Barebones PC. The liveCD was so cool, I elbowed Windoze over on my HDD and did an Ubuntu Desktop install.  It's brilliant and I want to keep it :D 

There is a slight glitch that I can't figure-out though: The MSI has a push-pull fan arrangement to cool the processor - in the normal boot sequence, the fan starts at its full, and very noisy maximum speed. As soon as Windows loads, it slows to a much lower level, only speeding-up again if the processor gets a big warm.  Under Ubuntu, the fan never drops below the maximum speed - even when the processor is only working at 2%.  Unfortunately, this noise makes it unrealistic to work in Ubuntu for more than a few minutes at a time - after that, the noise is too much and I have to reboot into Windows :( 

Has anyone solved this problem? - I'd even consider a hardware hack if that's the only way....

[COLOR=Red]**EDIT: Fixed it!!**[/COLOR]

Many thanks to Ubuntu member "mzilhao" who sent me a PM with the fix:

>  ...it was as simple as downgrading the BIOS version (to version 1.1 i think...).

my system is now running just fine, and i don't need windows anymore

I also down-graded my BIOS to version 1.1 and now Ubuntu slows the fan to the proper rate when it loads.

---

