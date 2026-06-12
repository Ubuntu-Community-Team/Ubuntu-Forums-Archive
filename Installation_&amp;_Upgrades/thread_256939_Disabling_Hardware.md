---
title: "Disabling Hardware???"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by xptweakerntn on 2006-09-13
I never could get Ubuntu to work, then I realized it was because of my onboard graphics was interferring with my graphics card. I took out my graphics card and it works fine(awsome stuff, really). But I want to use my graphics card, so is there some way to disable my onboard(like there is in Window?). I found the device manager in Ubuntu, but I didn't see anywhere to disable my onboard. My card is a Geforce FX550, and i can't turn off onboard within my bios, i can just select primary video adapter

---

### Post by K.Mandla on 2006-09-14
My only idea is to add pci=conf1 in your boot line. I don't know if it will work for you (I don't even know when or why it *should *work), but I had a similar problem trying to force Linux to ignore onboard video and it (kind of) worked. Good luck!

---

### Post by xptweakerntn on 2006-09-14
is there someway i can instal ubuntu, disable the onboard(like you have to do within windows, and then install the card?

---

### Post by Shay Stephens on 2006-09-14
You might check the motherboard for a jumper to disable the onboard graphics, or maybe a setting in the bios configuration.  Worth a look anyway if you can't do it via ubuntu.

---

