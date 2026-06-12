---
title: "Graphics Card Problems"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by xptweakerntn on 2006-09-30
First I just want to state that I really want to use Ubuntu. I am having trouble with graphics though. I have a Compaq Presario SR1220NX with onboard graphics. I also have a Geforce FX5500 PCI card. If I take the card out, I can boot from the disk and Ubuntu works fine. I need the card though. I can't disable it in my BIOS, and don't know if  I can disable it on my motherboard. I am planning on dual booting with Windows. What do I need to do to be able to use Ubuntu with my card in? I was thinking taking the card out, installing Ubuntu, disabling my onboard withing Ubuntu, and then installing my card within it. But since I am new to *nix, I don't even know if this is possible. Could someone who knows about the subject help me and stick with me the whole way?

---

### Post by Iarwain ben-adar on 2006-09-30
Hi,
What do you get when you start Ubuntu with your Geforce?

Maybe you can try this
```
sudo dpkg-reconfigure xserver-xorg
```


Iarwain

---

### Post by xptweakerntn on 2006-09-30
Wehn I tried that it did the same think as usual when I have the card in. The last message I see is "Kernel panic-not syncing fatal exception in interrupt

---

### Post by Iarwain ben-adar on 2006-09-30
Then i don't know,
sorry


Iarwain

---

### Post by orb9220 on 2006-09-30
Nope you will have to disable it from the bios which I never heard of there not being an option for.

If your docs show the motherboard jumper settings then you can at least verify that it can be disabled on the motherboard. And will have to do it from there.

The other thing is to call a local Compaq Presario store or authorized dealer and ask them.

---

### Post by xptweakerntn on 2006-09-30
i chatted with a compaq person, he said that there was no way to disable it. i don't know if this is true. but anyway. if i was to take the card out, install linux. could i disable my onboard within linux, just like you have to do in windows. uninstall drivers for it and disable it or the like. what is my best bet?

---

### Post by tseliot on 2006-10-01
Try this guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

