---
title: "Help find debootsrap mistake or error"
date: 2021-01-07
forum: Installation &amp; Upgrades
---

### Post by forcecore on 2021-01-07
Hello, i have years used Ubuntu on my laptops and i find that Canonical minimal install is not what it should be as it is installing all bloat & fonts & apps and then deinstalls them which is counter-productive and still leaves stuff behind that is not needed for minimal barebone desktop(extra fonts, help browsers, manuals and so on). I digged up my old script and preparing this for 21.04 and for future versions but when i finish my iso then installing wont finish. Sadly script is in research stage and is meant to be copy&pasted manually until i find way to fully automate all.

If anyone could point out why it causes faulty .iso i would be grateful. Live-cd mode runs fine and i still have to add more extra packages what i want. I really hope Canonical adds barebone desktop option in future as a third choice.

I suspect it is something with grub but not sure. My goal is to make efi x64 installer, no ancient bios mode.


NB: This is not 21.04 or something thread, it is just to prepare, test, investigate and i plan to use this in far future too to get minimal .iso for barebone installs by correcting package changes and so on.
[ATTACH]287697[/ATTACH]

---

### Post by forcecore on 2021-01-12
Finally a solution from this github link, this person used same tutorial as basis like i did years ago and now he is made it even better than mine ever was. 

I applaud [https://github.com/mvallim/live-custom-ubuntu-from-scratch](https://github.com/mvallim/live-custom-ubuntu-from-scratch)

---

