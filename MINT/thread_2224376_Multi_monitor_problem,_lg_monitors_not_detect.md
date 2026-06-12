---
title: "Multi monitor problem, lg monitors not detect"
date: 2014-05-16
forum: MINT
---

### Post by allergygorilla23 on 2014-05-16
Hi guys, i'm having a really strange problem with my monitors. I have linux mint installed in a desktop pc, with this configuration: 2 23'' lg e2342 monitors (from now on monitors 1 and 2) and 1 46'' lcd tv (from now on monitor 3). My graphics card is an nvidia geforce gtx 650. Usually i only use the two 23'' monitors, and whenever i want to watch a movie or something i activate the third 46'' monitor, everything done through a script. I've configured everything with arandr successfully. 
The setup's been working for 2 years perfectly, but today when i wanted to activate the 46'' monitor the script wouldn't work. Assuming it was a minor problem i decided to reboot the pc and that was the last time the two 23'' monitors worked. After that, the monitors were never recognized again, not even when booting up (the bios screens usually showed up on the 23'' monitors, but now they only show up on the 46). If I change the card's output to which the tv is connected, they all work (i have one hdmi, one dvi, and another hdmi cable connected trough a dvi adapter to the card). I tried all 3 outputs with the tv and they all work. Even if after starting the pc i connect the tv's hdmi cable to one of the 23'' monitors, it works, but after rebooting it doesn't. Its like the card doesn't recognize these monitors as such, even booting in. I also have win7 installed in this computer and the same happened when i started it, the monitors dont show up. I tried with other pc's and the monitors do not work, unless i connect them trough a cable that was already receiving the signal (start the pc with a working monitor, disconnect the cable and connect the lg monitors). I tried switching the pci port of the graphic card, and re installing all nvidia drivers, everything without success. There are no working drivers for this monitors from LG, it says they should be detected automatically (and they've been for almost 2 years now) I've run out of ideas, any clue on how to proceed? 

Thanks in advance!

---

### Post by allergygorilla23 on 2014-05-17
Well, for anybody that might read this in the future, i solved the problem by connecting the 23 displays to a 4th computer with windows 7, they were recognized; later i just changed all the displays from dvi to hdmi, from hdmi to dvi and used a 3rd vga cable, and after messing around for an hour i got it working.

---

### Post by chris233 on 2014-05-17
I had a problem with multi-monitors awhile back with a MSI R6870 Hawk radeon HD 6870 and ended up solving it by installing the AMD catalyst control center program and it allowed me to detect both monitors and set it up just nice for all the AMD folks out there

---

