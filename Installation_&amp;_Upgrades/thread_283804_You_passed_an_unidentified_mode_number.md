---
title: "You passed an unidentified mode number"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by Bannet on 2006-10-24
:KS 8) I just upgraded to 6.10 had to gksudo "update-manager -c -d" after install to get it to work. 

Edit my grub for 800 600
## e.g. defoptions=vga=788 resume=/dev/hda5
# defoptions=quiet splash vga=788

Edit my  /etc/X11/xorg.conf
Section "Monitor"
        Identifier      "GENERIC MONITOR"
        Option          "DPMS"
        HorizSync       28-54
        VertRefresh     43-100


Everting seems fine exept my startup error.

"You passed an unidentified mode number.
Press <RETURN> to see video modes available, <SPACE> to continue or wait 30 secs"

Any help would be appreciated. 

Thanks in advance Bannet.

---

### Post by Mr. Picklesworth on 2006-11-30
I get this error in GRUB as well, after using Start-Up Manager.

Curiously, if I press Space everything works fine.
Where should I be looking to change this number from whatever it has been set to?

---

### Post by LLRNR on 2006-12-01
[HTML]Color depth      | 640x480  800x600  1024x768 1280x1024
-------------------------------------------------------
256        (8bit)|  769      771       773      775
32000     (15bit)|  784      787       790      793
65000     (16bit)|  785      788       791      794
16.7 Mill.(24bit)|  786      789       792      795[/HTML]

These are the only VGA values I know... I once found an article which had other resolutions, too, but I just can't find the link again...

LLRNR

---

### Post by K.Mandla on 2006-12-01
> **Bannet said:**
> ## e.g. defoptions=vga=788 resume=/dev/hda5
# defoptions=quiet splash vga=788
You might try using a different number for the VGA option. 

Unless I'm mistaken, this table gives options for that code.

```
[FONT=Courier New]Color depth      | 640x480  800x600  1024x768 1280x1024
-----------------+-------------------------------------
256        (8bit)|  769      771       773      775
32000     (15bit)|  784      787       790      793
65000     (16bit)|  785      788       791      794
16.7 Mill.(24bit)|  786      789       792      795[/FONT]
```I think if you hit upon an acceptable code, you should stop seeing that error message. But I have been wrong before. :D

Edit: DARN! LLRNR beat me to it. :D

---

### Post by LLRNR on 2006-12-01
> **K.Mandla said:**
> I think if you hit upon an acceptable code, you should stop seeing that error message. But I have been wrong before. :D

Edit: DARN! LLRNR beat me to it. :D

It's strange, I tried (on Edgy) all of these codes myself (only for 16 and 24 bits though) and they all worked with no problems at all... :-k Shouldn't I be getting errors too ? :D

LLRNR

---

### Post by Hachi-Roku on 2007-11-29
Im getting this too on my newly installed gusty. Never got it before. Im using VGA=791. I might try the 24 bit depth option.

Anyone had any luck with fixes yet?

---

### Post by Hachi-Roku on 2007-11-29
Ok it didnt work. I thought there might be a discrepancy of values in menu.lst and xorg.conf, but makes no difference.

back to the whiteboard!

---

