---
title: "How to export audio drivers/settings in Ubuntu 12.04 to use in 13.10"
date: 2014-02-12
forum: Installation &amp; Upgrades
---

### Post by filipluch on 2014-02-12
Now i have 13.10 installed on my laptop, i still did not remove 12.04, as i would like somehow to save the audio drivers and install on 13.10. I want to do this because the sound in 12.04 was even better than in the preinstalled windows when i bought the laptop from store. I tried many tutorials but none of them got me same audio quality

Laptop info:

HP 3040nr 
5.1 audio system
proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xc3700000 irq 56
 1 [Audio          ]: USB-Audio - HP Wireless Audio
                      Standard Microsystems Corp. HP Wireless Audio at usb-0000:00:1d.0-1.5, high spe

---

### Post by TheFu on 2014-02-12
First, let me say that I do not KNOW the answer to the question, however, as a long-time C/C++ developer, I don't think it will be possible without the source code for the drivers. Even then, the supporting libraries have almost certainly changed too much to support recompiling the older code.

The differences between 12.04 and 13.10 are more like WinXP to Win7 from a library perspective.

12.04 has support until 2017 - so you could run that release if audio is important.

Or you could compare the source code between the different released drivers to figure out what might cause the quality issue ... or hire someone to do this for you.

Sorry that I don't have a good, clear, answer.

---

### Post by filipluch on 2014-03-31
Thank you for your answer. At least I know what choices I have.

---

