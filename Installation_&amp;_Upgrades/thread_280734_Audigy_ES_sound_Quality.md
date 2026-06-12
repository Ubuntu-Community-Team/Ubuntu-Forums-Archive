---
title: "Audigy ES sound Quality"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by victor_c26 on 2006-10-19
I'm dual-booting Ubuntu and Windows on seperate hard drives.

Now, I still use Windows XP (It's my main OS really), but I like having an Ubuntu install on the same machine. And since I use both operating systems, and play music on both, I noticed something. For some reason, the sound quality in Ubuntu isn't as clear and sharp compared to Windows XP.

Same sound card, only difference is that in Ubuntu, it's just using whatever came with the distro. With Windows, I have the Creative drivers loaded.

Is it a sound card driver issue? And if so, are there any other drivers out there that will improve the sound quality to that of the Windows XP drivers?

---

### Post by ReaderRat on 2006-10-19
Have you loaded the Creative sound drivers for Linux?
[**Creative Open-Source Website**](http://opensource.creative.com/)

---

### Post by victor_c26 on 2006-10-19
That site just mentions ALSA which is what is loaded in Ubuntu right now.

---

### Post by victor_c26 on 2006-10-24
After fiddling with alsamixer, it didn't really change anything to better the sound quality. It did raise the volume up though; PCM was at 48.

The only thing I can think of that might be wrong is that for some reason my Audigy ES is recognized as having a SigmaTel STAC9721,23 as the chipset.

Don't all Audigys have a emu10k1 or emu10k2?

---

### Post by JohnLM_the_Ghost on 2007-11-10
I'm encountering the same problem (if you can call it that way)

It's really a shame that Linux does't offer as good sound quality.
You might not have any differences on simple generic sound cards, but SBs is the card you want to get the most of it, especially if you have high-end 5.1 or 7.1 sound system.

Unfortunately, I don't know any workaround for this, but i'm pretty sure it's because of ALSA drivers. They're made to support sound cards and chipsets in general not one specific model. It's also "as long as it works" policy.

Hope this issue will be dealt within closest time.
It would be nice to have good sound quality in Ubuntu.

And yeah ALL Audigy cards have emu20k1(2) chips.

---

