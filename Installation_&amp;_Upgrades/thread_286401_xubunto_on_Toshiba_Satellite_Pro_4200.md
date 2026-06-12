---
title: "xubunto on Toshiba Satellite Pro 4200"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by luistrigueiros on 2006-10-27
Hi,
I am trying to install Xubunto 6.10 on my old PIII Toshiba Satellite Pro 4200. 
I installed before DSL3.0.1 on it and had to use framebuffer with the option vga=791, to get X.
I tried several boot options, including the vga=0x318 video=vesafb 
but X is always starting in 800x600 mode. 
Could anyone please point me some directions.
Thanks, Luis

---

### Post by funkyade on 2006-10-27
Look in your xorg.conf and make sure that in the "Screen" section you have a complete list of resolutions your laptop supports (max 1024x768 if I remember rightly)

```
#>sudo nano /etc/X11/xorg.conf
```

this should work, you could just change the existing res here to 1024 instead of 800...

you may need the correct driver for you gfx card - you will have to look that up, but post back if you are still struggling.

hth

---

### Post by luistrigueiros on 2006-10-27
> **funkyade said:**
> Look in your xorg.conf and make sure that in the "Screen" section you have a complete list of resolutions your laptop supports (max 1024x768 if I remember rightly)

```
#>sudo nano /etc/X11/xorg.conf
```

this should work, you could just change the existing res here to 1024 instead of 800...

you may need the correct driver for you gfx card - you will have to look that up, but post back if you are still struggling.

hth

Hi,
I haven´t installed xubunto on to the hardrive yet, I booted with the LiveCD and inserted the boot options using F2,F6.
Are you saying to boot with noX option and issue the previous command. 
Thanks Luis

---

### Post by funkyade on 2006-11-01
Sorry not to have posted back earlier.

If you are trying the Live CD, boot it as normal, open a terminal (APPLICATIONS->SYSTEM->TERMINAL) and then issue the command I gave earlier and change the entries in xorg.conf (use CTRL+X to save and exit), you can then restart your xserver using the CTRL+ALT+BACKSPACE key combination.

Alternatively, once xubuntu has booted and you are at the desktop. Go to APPLICATIONS->SETTINGS->DISPLAY SETTINGS and see if the resolution you want is in there.

hth

---

