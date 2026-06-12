---
title: "Server 11.04 Installation Hangs"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by Cladd on 2011-06-11
Hey everyone,

I'm trying to install server 11.04 (64 bit).  I verified the disc is good through the boot menu, and I went to the installation.  After I choose my keyboard layout it scans the CD, then loads some things, and promptly does nothing.  All I've got is a purple screen, and I can switch over to other consoles.

Help?

---

### Post by Smuus on 2011-06-26
Hello,

I have exactly the same problem, however while I googled for solutions, the installation went on after about 10 minutes or so. But I only came to the "how do you want to name your server" and now I have the blank purple screen again. I guess I will wait another 10 to 20 minutes, but this really shoudn't be the solution.

As for the suggested solution for nVidia cards: I have two AMD cards in there, so this shouldn't be the problem. I tried it anyway with nomodeset but without any effect.

Another effect: When I press Ctrl+C while the purple blank screen it goes black, shows something about PC card detection and then goes back to blank purple screen.

My system:
Athlon II (Regor), 2x AMD HD6870 GPUs, 2GB Kingston ValueRAM, a fine Gigabyte Mainboard...
What I have is a working ubuntu server 10.04.2 LTS installation. What I want is a fresh ubuntu server 11.04 installation - no upgrade.

Anybody any clues?

Cheers, 
Smuus

---

### Post by trendle on 2011-07-23
Nobody got any help !?
Happens to me too.  Except I've got a N510 atom cpu.
I let it sit over night and still nothing changed.  That's just Cr**P.

Tried the switches, no_dmraid etc.  No help (shouldn't need to though).

I don't believe that I saw this with 10.04.  

So my conclusion is that somebody 'improved' things.  Well, thanks for that. You just wasted several days of my life (perhaps I should give up and get my life back.... hello Microsoft !).:confused:

Not a great selling point for turning average users onto Linux.

---

### Post by MAFoElffen on 2011-07-23
> **Cladd said:**
> Hey everyone,

I'm trying to install server 11.04 (64 bit).  I verified the disc is good through the boot menu, and I went to the installation.  After I choose my keyboard layout it scans the CD, then loads some things, and promptly does nothing.  All I've got is a purple screen, and I can switch over to other consoles.

Help?
@ Both posters, with priority on the who started this thread...

What is your graphics card?  

I know you are going to assume that The Ubuntu Server Version runs in tty text so does not have problems with graphics.  That was my incorrect assumption years ago.  Ubuntu Server runs in a VGA/VESA mode.  Some video cards do not go into this mode natively without a mode change.

Depending on your graphics card, you will need to set a "particular" kernel boot option that will enable it to go into that generic mode.

If you don't know the specifics of your video card, post the results of:
```

sudo lspic -v | grep VGA

```And to do that... Well, you are going to have to get into a terminal... Such as from from one of the LiveCD's... From a text console session.  I'll be back this afternoon if you need help with that or for mode options you might need.

This sticky might help you with all that:
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

---

### Post by MAFoElffen on 2011-07-23
> **trendle said:**
> 
Tried the switches, no_dmraid etc.  No help (shouldn't need to though).

I don't believe that I saw this with 10.04.  

Not a great selling point for turning average users onto Linux.
11.04 started with aubergine theming in Server.  Now the VGA theming can be done through a theming file, instead of through setterm...

These "kinds" of changes I started noticing in 9.04 alpha2.

EDIT-- Notice that I "didn't" say that this made things any easier, just different.

---

