---
title: "No sound with delta 66 and karmic koala"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by m0ksha on 2009-10-08
Recently upgraded from Jaunty to Karmic. Unfortunately my M-Audio Delta 66 stopped working.  

Ubuntu detects the card and I've installed envy24control and tried different combinations with poor results.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M66 [M Audio Delta 66], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

My guess is that it is pulseaudio-related.

Any ideas?

---

### Post by dednikko on 2009-10-15
I can confirm that this problem also affects the M-Audio Delta 44 pci sound card as well. At first i assumed it was that i hadn't disabled the onboard audio in BIOS, but no luck after i did that. I am currently dual booting 9.10 and 9.04, and 9.04 is spot on perfect for me. I am using ALSA with Ardour, AynAddSubFX and pretty much anything ALSA compatible with no problems. I have a Biostar mobo, and was wondering if it might actually be a motherboard support issue? What should i do to help troubleshoot?

---

### Post by ministoat on 2009-10-16
I have the same card - run alsamixer from terminal for your card and see what your settings are. I needed to set my left and right outputs to 'Digital' and then I got sound.

problem is this disappeared with the latest update ><

---

