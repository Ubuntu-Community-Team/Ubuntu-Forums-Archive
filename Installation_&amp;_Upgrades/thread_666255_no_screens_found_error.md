---
title: "no screens found error"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by ArchCorsair on 2008-01-13
Wen attempting to boot into live cd using x server I get this error:
```
Fatal server error
no screens found
```
my gfx card: geforce 8800 GTS G92 512 mb

Any suggestions?
thnx in advance!

---

### Post by overdrank on 2008-01-13
> **ArchCorsair said:**
> Wen attempting to boot into live cd using x server I get this error:
```
Fatal server error
no screens found
```
my gfx card: geforce 8800 GTS G92 512 mb

Any suggestions?
thnx in advance!

HI and welcome,  you can try at the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add vga=771 before the -- then press enter. Then b to boot. You may also replace 771 with 775 and hopefully this will allow you to boot the live cd. Good luck!

---

### Post by ArchCorsair on 2008-01-13
Thank you so much, I'm going to try it now

---

### Post by ArchCorsair on 2008-01-13
> **overdrank said:**
> HI and welcome,  you can try at the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add vga=771 before the -- then press enter. Then b to boot. You may also replace 771 with 775 and hopefully this will allow you to boot the live cd. Good luck!

Nope :(

I tried 771 and 775 and it hangs at a blank screen, I let it go for 30 minutes and it just hangs there. What else can be done?

---

### Post by overdrank on 2008-01-13
> **ArchCorsair said:**
> Nope :(

I tried 771 and 775 and it hangs at a blank screen, I let it go for 30 minutes and it just hangs there. What else can be done?

HI and have you check cd for errors and maybe you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by ArchCorsair on 2008-01-13
> **overdrank said:**
> HI and have you check cd for errors and maybe you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I'm very sure the checksum is correct because I got these ubuntu CDs mailed toi me by ubuntu. Two. Versions, 32 bit and 64 bit, both resulted in the same error.

---

### Post by Jake90 on 2008-01-14
> **ArchCorsair said:**
> Wen attempting to boot into live cd using x server I get this error:
```
Fatal server error
no screens found
```
my gfx card: geforce 8800 GTS G92 512 mb

Any suggestions?
thnx in advance!
I have the same problem and I already installed (feisty). You can try adding noapic at the end of the line (right after quiet splash, remember to make a space) but that didn't work for me maybe you'll have better luck. If I solve it I'll let you know.

---

### Post by macm10 on 2008-01-14
i am having a similar problem with my ati mobility radeon x1800...

---

### Post by Setomidor on 2008-01-31
Same problem with x1600 mobility radeon, running hardy alpha 3.

replacing quiet splash with vga=771 resulted in some disc activity, but stuck at a blank screen.
vga=775 gave me the option of specifying video mode, and then a lot of startup output before resulting in "no screens found" again.

More detailed output is

(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
....
(II) VESA(0): Not using built-in mode "320x200" (hsync out of range)
(EE) VESA(0): No valid modes
(EE) Screen(s) found, but none have a usable configuration

---

### Post by PmDematagoda on 2008-01-31
I think in the case of the Nvidia 8800 card, the easiest way of installing Ubuntu is by using the Alternate CD, after you install Ubuntu the process of installing the required Nvidia drivers is quite easy.

---

