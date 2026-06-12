---
title: "PC freezing/flashing at me"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by monsieurboz on 2010-05-13
Please accept my apologies if I am in the wrong place, or am asking the question in the wrong way, but this seemed right on both counts.
I recently upgraded my PC from the Ubuntu 9.1 which was on it, after an invitation from the upgrade manager. I'm now on 10.04 LTS
It was stable before (other than the fact that it did not return from hibernation) but now after as little as 10 minutes it will randomly pixelate the middle of the screen, report that it is checking the state of various things, including battery state, but that's the only one I understand, then the top half of the screen changes to vertical white bars and flashes.
The only way to recover is to power off.
It does not seem to matter whether I am working on the machine or not.
It nearly always occurs when left to its own devices for a while. Come to think of it it's just a development of the aforementioned hibernation problem, just happing more often and therefore more annoying.
The box is a "made from bits" PC, which worked happily with W***ows for a couple of years before I saw the light, and I had 9.1 Ubuntu on it for about 6 months. 
Does anyone have any ideas, please?
Thanks
MonsieurBOZ

---

### Post by dino99 on 2010-05-13
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

goto: system admin hardware driver to see if your video driver is activated.

have to know which graphic card is used and what driver is installed.

---

