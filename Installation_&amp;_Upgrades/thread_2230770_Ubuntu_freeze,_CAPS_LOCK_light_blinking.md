---
title: "Ubuntu freeze, CAPS LOCK light blinking"
date: 2014-06-21
forum: Installation &amp; Upgrades
---

### Post by khai3 on 2014-06-21
Greeting everyone.

Recently I've installed Ubuntu 14.04 on my computer. The installation did complete successfully and I have also installed
my graphic card driver from Nvidia Website. The problem is that my laptop easily freeze and the Caps Lock light is blinking.
When it freeze, I cannot do anything even to open the terminal by pressing CTRL+ALT+F1. Can anyone explain to me what
could be wrong and how to overcome this.

Laptop Specs:
Processor: AMD Turion X2 Dual Core 2.20 GHz (64-bit OS Supported)
OS : Ubuntu 14.04 32-bit alongside with Windows 7 Professional 32-bit
Graphic: Nvidia GeForce 9100M G
RAM: 3.00 GB

---

### Post by nerdtron on 2014-06-21
Caps Lock blinking and computer freezes. Seems to me like a kernel panic. 64bit or 32bit Ubuntu 14.04?
Or try an older release of Ubuntu like 12.04.

---

### Post by khai3 on 2014-06-21
32-bit Ubuntu 14.04. Can you explain a little about kernel panic?

---

### Post by nerdtron on 2014-06-21
What is a kernel pacnic: [http://askubuntu.com/questions/35722/what-is-kernel-panic](http://askubuntu.com/questions/35722/what-is-kernel-panic)

Does it even boot properly? Do you get to the desktop and then it freezes? Or you do something (maybe a few hours) and then it freezes? Any errors on the screen? Is you hardware running properly on Windows?

---

### Post by khai3 on 2014-06-21
Does it even boot properly? 
Yes. It boots properly. During boot, the ubuntu bootloader allow me to choose either to load ubuntu or windows. Both of them boots properly.

Do you get to the desktop and then it  freezes? Or you do something (maybe a few hours) and then it freezes?
Yes. I managed to load until the desktop. It went okay until I run some programs, then it freezes. In one time, I only run CodeBlocks IDE and Rhythmbox, suddenly my laptop freeze.

Any errors on the screen?
Yes. My screen become distorted and i can't do anything since then.

Is you hardware running properly on Windows?
Yes. All my hardware running properly on windows.

---

### Post by Vladlenin5000 on 2014-06-21
> Graphic: Nvidia GeForce 9100M G

This card requires proprietary drivers for optimal performance. You can install the recommended version easily by going to System Settings > Software & Upadates and the rightmost tab "Additional drivers".

---

