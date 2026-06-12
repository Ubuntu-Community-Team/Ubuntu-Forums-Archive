---
title: "Can't install Lucid on HP ProBook 4510s"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by jeromewilson on 2010-05-10
Hi,

I'm having some problems installing Ubuntu 10.04 64 bit on my laptop - I tried first using the CD but selecting 'Install Ubuntu' from the menu did nothing at all so I'm using wubi instead. The initial wubi install was fine but attempting to boot into Ubuntu initial setup results in lock up. Booting without the graphic workaround option gets as far as:

agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xC0000000

However with the workaround it gets further and the final log output is:

set up 63M of stolen space

Then complete lockup.

Can anyone help, please? :)

Here's the laptop spec:

CPU: Intel Mobile Core 2 Duo T5870  @ 2.00GHz
MB: HP 3072 / Chipset: Intel GM45/GM47 / Southbridge: Intel 82801IM (ICH9-M)
Graphics: VX2260WM on Mobile Intel 4 Series Express Chipset Family
HD: 312.57GB Western Digital WDC WD3200BEKT-60F3T1 ATA Device (IDE)
DVD: hp DVD RW AD-7561S ATA
Sound: SoundMAX Integrated Digital HD Audio

---

### Post by jeromewilson on 2010-05-11
So I managed to get it to install by sticking 'nomodeset' in the command line somewhere. However, now it's installed it won't boot. Do I still need to add 'nomodeset'? I tried adding it to the command line starting 'linux...' but it didn't seem to help.

---

### Post by Tiede on 2010-09-07
Hello, Jerome. I too have an HP Probook 4510s, with the same specs as yours.
I was wondering if you had your issue solved?
I installed ubuntu on my laptop last year without (installation) problems...
If you still need help, maybe I can help you out.

PS: After installation, you may need to fix a bug in the Soundcard driver, where sound can only be heard by using headphones... Just let me know :)

---

