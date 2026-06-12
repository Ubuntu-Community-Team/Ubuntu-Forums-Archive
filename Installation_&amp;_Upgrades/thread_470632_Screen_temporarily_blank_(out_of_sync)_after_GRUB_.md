---
title: "Screen temporarily blank (out of sync?) after GRUB starts"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by maxino on 2007-06-11
Hi,
I just installed 7.04 and found a glitch I never had before.
The hardware is an old IBM "NetVista" PIV 2GHz with Intel graphics onboard (chipset 82845).
Never had a problem with the previous distro I used to run.

As soon as GRUB starts the screen goes blank for a few seconds but comes back to life at Ubuntu login so I can start the desktop and everything is fine. After shutdown, the screen goes blank again till the computer switches off. It's clear that although the computer is fully usable, I cannot see anything of the services being started or stopped.

I tried to put the line "vga=normal" or "vga=ask" in the GRUB conf file but no matter what video mode I try to force, the screen always goes blank after 1 or 2 seconds.

My screen (Samsung 19''), during the blank phase, detects a 720x400@85Hz video mode which apparently it doesn't like. When the Ubuntu login appears the screen detects 1280x1024@60Hz and as I said runs happily with it.

Can someone kindly suggest how to solve this issue? Many thanks

---

### Post by frodon on 2007-06-11
You should try other resolution for your GRUB : 
vga = 785 for standard vga
vga = 788 for 800x600
vga = 791 for 1024x768 *
vga = 794 for 1280x1024

Put it here in your menu.list :
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791
```

---

### Post by maxino on 2007-06-11
Hi frodon,

For some weird reason, the only resolution that seems to work  is the 800x600 (vga = 788).
Now I can see what happens after the kernel loads. Problem solved.

Thanks :)

Max

---

### Post by bobsp on 2007-06-13
My Dell 2350 is doing this too with Feisty.  I've tried all the values you've suggested (and 792 as suggested in this thread [http://ubuntuforums.org/showthread.php?t=471041&highlight=splash]("http://ubuntuforums.org/showthread.php?t=471041&highlight=splash")), but none makes any difference.

I resorted to removing the "quiet splash" from the kernel list entry, so at least I could see the computer doing something during boot.

Anyone got any other ideas?

---

### Post by maxino on 2007-06-14
Hi bobsp,

This is what works for me. 
I added vga mode 788 in the default options section of /etc/boot/menu.lst:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=788

and removed any other video mode reference elsewhere.
It works but oddly the resolution is not 800x600.  I can see the startup of the all the services in big blocky letters, and I am happy enough with that.

Good luck

Max

---

