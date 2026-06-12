---
title: "How do I install nVidia graphics driver automatically?"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by Learn_w_Graffix on 2007-09-15
I'm a Ubuntu Noobie who really wants to avoid Vista!
I there a way to "automatically" install nVidia drivers? Every post I have read ends up with very involved and confusing instructions, including referring people to the nVidia site. I've gone there, and found further instructions (for example, to disable or get out of "X", whatever that is!).
As there are only 2 major graphics manufacturers (ATI and nVidia), I assume I am missing something. Plus, "help" seems to tell me to use the auto package manager to install things.
Notes:
1) If your instruction starts with, "Type ...", you are assuming to much of me, and probably cannot help me!
2) If your instructions starts with, "Click this, then this, to bring up the console, and then type ..." you might be able to help!
3) If the answer is, "There is no easy way to do that," I can accept that--but is there any way to help develop an easy way?
Thanks!

---

### Post by Pumalite on 2007-09-15
What card do you have?
There are two possibilities:
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-glx-new

---

### Post by Learn_w_Graffix on 2007-09-16
My video card is 8800 GTS 320 MB (NVIDIA).
I presume you are saying get into the console and type "sudo . . ."
What about downloading the driver? Does the ubuntu include the driver in its auto-updates? And if so, how do I start 3D? (I tried that before, and ubuntu wouldn't launch; I re-installed it, tried it again, and again it wouldn't launch; I had to do some extremely obscure command-line stuff to get it going again.)
Isn't there some kind of "autoexec.bat" command that can be run to install the drivers, if the auto-update feature of ubuntu isn't used?

---

### Post by mikewhatever on 2007-09-16
[ENVY]("http://albertomilone.com/") is a program that downloads and installs the nvidia driver. About Beryl (3D), there is no way to install and configure it without using 'obscure' commands. If you want it, but do not want to deal with CLI, try using Sabayon or Linux Mint, both have nvidia drivers and Beryl by default.

---

