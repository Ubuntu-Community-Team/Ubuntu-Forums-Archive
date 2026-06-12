---
title: "scrampled UI while instllation. unable to install ubuntu lucid lynx."
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by feistybee on 2010-05-02
I am a ubuntu lover from feisty version. Now I want to install Lucid Lynx and explore. Here are my system configuration,

AMD Athlon 64 X2
ASUS M2NPV VM motherboard with Nvidia GForce
DDR2 RAM: 4GB

I inserted Lucid Lynx 64 bit cd and restarted the pc. The ubuntu installation screen came with 5 white color dots and that are changing to red and white. After that I got the scrambled screen with multiple lines. I am unable to proceed after that. Somebody help me, to fix this issue and install Lucid Lynx.

Thanks in advance.

---

### Post by tristangrimaux on 2010-05-17
Have you tried safe graphics mode? F4 after choosing language.

Installing on the same board. I did a network install in text mode,  After installing I had no xorg.conf so I created a basic one with the "nv" driver to load the display manager. The nouveau drivers are not working with this nVidia GeForce 6150.

---

### Post by stasiana on 2010-05-29
Can you share what exactly the procedure is and how you created the new xorg.conf? I have a m2npv-vm board as well and I cannot figure out how to get this version of Ubuntu working.

---

### Post by EscapePod on 2010-05-31
> **tristangrimaux said:**
> Have you tried safe graphics mode? F4 after choosing language.

Installing on the same board. I did a network install in text mode,  After installing I had no xorg.conf so I created a basic one with the "nv" driver to load the display manager. The nouveau drivers are not working with this nVidia GeForce 6150.

Unlike all previous ubuntu versions, when you select F4 in Lucid Lynx, there is NO choice for "Safe Graphics Mode".

I believe this is a major flaw in 10.04.

I tried F6 and selecting nomodeset, however, this lets me start the install (or run from CD), and gets to the point of the 4 diamonds flashing across for a while, then the screen goes black.

F4 does have a choice to install drivers from CD, but I'm not sure how that is done -- I haven't been able to find any help on using that function.

---

