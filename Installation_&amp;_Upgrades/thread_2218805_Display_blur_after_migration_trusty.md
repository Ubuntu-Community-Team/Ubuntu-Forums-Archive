---
title: "Display blur after migration trusty"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by vincentmichaud on 2014-04-22
Hello,
Following a migration trusty ubuntu 14.04, I have a blurry screen display, except on the part of the cursor or mouse pointer. I have a nvidia graphic card, a 560ti GTX. A friend encounter the same problem with a laptop. I first used the nvidia proposed in deposits and I also tried the drivers xorg edgers unsuccessfully. The pilot currently in operation : 334.21. Importantly, even disconcerting, the display is normal in a guest session! Thank you for your help.

---

### Post by vincentmichaud on 2014-04-27
I unchecked all antiliasing options in nvidia-settings that I had changed and nvidia 331.38 driver works. Unchecked options: 
- Enable FXAA 
- Anisotropic filtering: Application setting overhide 
- Sharpening texture 
Do not forget to save via *nvidia-settings configuration* at the bottom of the list. 
Strange, because I did not meet this problem in my previous migrations, but I just solve this problem!

---

