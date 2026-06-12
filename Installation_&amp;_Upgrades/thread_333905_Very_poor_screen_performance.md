---
title: "Very poor screen performance"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by gbond13 on 2007-01-08
I've upgraded from 6.06 to 6.10 Edgy and solved the miserable screen resolution problem using the instructions in FixVideoResolutionHowto. Screen res is now 1280x1024 by 24 bits, and I'm happy with that. What is driving me nuts is video behavior when dragging a window. Instead of getting a smooth movement I'm getting multiple traces behind the window as it moves across the screen (it's like a cursor set up to leave a track when moved).

Behavior inside windows is fine. Everything works as expected. This leads me to believe the problem a shortage of memory for my video card, an Intel 915GV. Where I'm hung up is figuring out how to allocate more memory (I have 2 GB available) to video.

Will someone please explain how to do it? With step-by-step instructions, if possible.

My computer is an HP Pavillion a1120n with 2GB of RAM, 2 USB  hard drives and a cable connection and wireless network.

Thanks in advance.

---

### Post by Jussi Kukkonen on 2007-01-08
It's an integrated card with shared memory?

In that case the answer may involve two steps:
1. your BIOS should have some settings about this (although it sounds like these might be fine as you have no problems in Windows)
2. With some chips, X has to be told about the choices you made in step 1.:  *dpkg-reconfigure xserver-xorg* should have a question about that 

If you don't want to run reconfigure because of your previous changes, you can just add the line "VideoRam 32768" in the Device-section of your xorg.conf (32768 being the amount of memory).

---

### Post by gbond13 on 2007-01-09
Jussi,

Thank you very much.  Increasing the amount of memory allocated to video seems to have done the trick, or mostly done. I'll experiment with increasing the amount of memory allocated and see if that smooths things out even more. Again, thanks.

George

---

### Post by ant1060 on 2007-01-09
Hi!
When I had this problem (Asus A6J) I just installed the NVidia driver (in Automatix) and it instantly solved the problem.
I separately had to solve the question of screen resolution and screen size though.
Good luck!

---

### Post by gbond13 on 2007-01-09
Thanks. I'll give that a try. I'm slowly getting the problem solved.

---

