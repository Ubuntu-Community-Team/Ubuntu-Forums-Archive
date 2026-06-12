---
title: "Ubuntu Precise 12 beta 2 completely unresponsive"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by obitori on 2012-04-22
I just installed the new beta 2 CD on an AMD64 4 core processor (+> 2ghz) with 4-6 gb memory and a 800 series Nvidia card (mid level).  I can't list the particulars because it is so sluggish that it is virtually inoperable.

The screen takes a long time to load and then the mouse alternates between being responsive and just going dead.  Any click that triggers backend processing sends it into a zombie state where I have no user responsiveness while the system deals with one click.  

I tried updating the nvidia driver to current-updates, but hte only thing that changed was that the top file menu did not load properly.  I went to a CLI and successfully "apt-get update" and "apt-get upgrade" to update everything.  That didn't help. 

Interestingly, I experienced the same problem after updating Kubuntu 11 on the same box, which is what prompted me to upgrade this machine.  The fact that the same problem cropped up on ubuntu and kubuntu makes me think it is not the window manager, but the nvidia driver.

Any thoughts/help would be appreciated.

---

### Post by sanderj on 2012-04-22
Just checking: you run Precise on the bare metal, or in a virtualmachine?

FWIW: Precise in a VM on my Ubuntu 11.10 is completely unusably slow.

---

