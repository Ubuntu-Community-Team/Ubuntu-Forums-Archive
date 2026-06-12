---
title: "Ubuntu 7.10 won't run/instal on new machine"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by Krokr on 2008-04-19
Having successfully played with Ubuntu on an old machine, I bought a new machine planning to make the switch from MS, hopefully permanently.

My new system is Intel Core 2 Extreme X9650 3Ghz ,8Gb Dominator memory, XFX 780i 3-way SLI motherboard, Dual 8800GT in SLI, Dual 150Gb raptors & Dual WD 750Gb drives, Dual TSST SHS202 CD/DVD drives.

However, when I try to play/install the live Cd or DVD I get to the initial install screen and if I select run/install, or the safe graphics option, a error message is flashed up which says something about 'cannot allocate....' then the screen goes black, the disk lights flash and after about 20 secs the machine starts beeping and I end up having to reboot. After several failed attempts to catch the error message I've given up and gone back to Vista, for now.

I know there is nothing wrong with any of the hardware, as it runs Vista 64 surprisingly well, and I've tried both the AMD(64) and the alternate versions, both in CD and DVD format. Perhaps I've misunderstood and these are the wrong versions for Intel 64 bit processors, or perhaps the 7.10 versions don't support the new processors or graphics cards. I've started to download the 8.04 beta and will give it a try tomorrow, but any feedback which might help would be appreciated.

---

### Post by Pumalite on 2008-04-19
Try Alternate 8.04 Beta (64 bit).

---

### Post by prshah on 2008-04-19
> **Krokr said:**
> then the screen goes black, the disk lights flash and after about 20 secs the machine starts beeping and I end up having to reboot.  but any feedback which might help would be appreciated.

When the screen goes blank, switch to console 8 by pressing Ctrl+Alt+F8, and check for error messages there. Or alternately, if F8 is not helpful/blank, what does Ctrl+Alt+F1 show?

---

### Post by dangreaves on 2008-04-19
This could be completely useless information but anything's worth a try I suppose. It worked for my graphics card problems.

1. Boot your system from CD
2. As soon as you have confirmed CD Boot or selected Boot from CD in the BIOS, hold down the shift key
3. Press n to avoid boot graphics
4. Type "live vga=771" and press enter
5. This will then run the Live CD in safe graphics mode. It worked a treat for my graphics card problems, mine refused to run in normal mode.

Again, that could be completely useless but everything's worth a try.

---

### Post by Maintech on 2008-04-19
Try booting with the nomsi option.

---

### Post by Krokr on 2008-04-20
Thanks for the various replies and suggestions. 

Quick update - I completed my download of 8.04 and this morning I successfully ran in liveCD mode and then tried to install. Everything appeared to go well and the install completed, but when I rebooted there was no grub menu showing Ubuntu and my old Vista options, as had been the case when I installed 7.10 on my XP machine. I know that 8.04 is a beta, and perhaps it doesn't do a grub install, but perhaps I missed an option somewhere? I've got work to do so I'll give it another go later, or perhaps wait for the final release. Thanks again.

---

