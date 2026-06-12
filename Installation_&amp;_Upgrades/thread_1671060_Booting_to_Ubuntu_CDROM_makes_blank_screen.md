---
title: "Booting to Ubuntu CDROM makes blank screen"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by ancient_ee on 2011-01-19
When I start my system on the Ubuntu 10.10 CDROM I get a tiny icon at the bottom, then the screen shuts off  due to no signal. So I cannot run the Live CDROM. Relevant here is that Debian CDROM runs just fine. (Lenny installs and runs good, but squeeze does not) Linux Mint (based on Ubuntu) gets me a pretty graphical welcome screen, then the monitor shuts off just like Ubuntu and Kubuntu.

WinXP installed and runs without a hitch.

My system: Gigabyte GA-P43-ES3G with 4Gb ram, 750 Gb SATA HDD, Nvidia Quadro video card.

I have gone through the BIOS settings looking for clues:
SATA AHCI mode is set to IDE (versus AHCI)
SATA port 0-3 native mode set to enabled (versus disabled which would be legacy IDE mode)
Azalia codec set to auto (verus disabled)

Is there anything else I should look for in the BIOS? Any other ideas?

---

### Post by gordintoronto on 2011-01-19
Ubuntu Community Documentation, using boot options to handle quirks with your hardware: BootOptions.

---

### Post by ancient_ee on 2011-01-19
The problem is that the live CD will not work, so there is no chance of a proper installation. Do I need to tweak files on the live CD? Please say no.

---

### Post by Code9 on 2011-01-19
I have the same issue as you and am awaiting a response. Do you have an Intel GMA by any chance?

---

### Post by ancient_ee on 2011-01-19
My Gigabyte motherboard manual lists no such chip as a graphics media accelerator.

My major suspicion, though, is that I have a video card that is a little too nice. I got this kick-*** Nvidia card so Solidworks objects would appear as shiny as can be (I am doing mechanical design work), but the drivers for such may not be featured yet in the Ubuntu live CD.

---

### Post by wojox on 2011-01-19
> I get a tiny icon at the bottom

Press enter at that spot. Pick your language and then press F6

Arrow down to "nomodeset" and press your space bar to set it then Esc key and enter again.

---

### Post by ancient_ee on 2011-01-20
Thanks, wojux, that got the live CD working. Now I just have to figure out why the HDD installation won't work, but that is another issue, so I will mark this one as "solved".

---

