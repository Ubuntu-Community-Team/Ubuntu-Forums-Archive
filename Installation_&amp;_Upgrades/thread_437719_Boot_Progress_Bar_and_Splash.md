---
title: "Boot Progress Bar and Splash"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by nlvivar on 2007-05-09
I have two laptops on both of which I have installed Feisty Xubuntu (on the older one) and Ubuntu (on the faster one) using the alternate cds.

I've finally gotten to the point where I'm running out of things to tweak or break and then fix...

One thing that has been bothering me is that neither laptops have the nice (X)Ubuntu slash and/or the progress bar and status updates. It is not that big of a deal, but sometimes I just like to know when my computer is going to finish booting or turning off, or if it has even hung.

Am I missing some packages since I used the Alternate disks to install?

Thanks.

---

### Post by nlvivar on 2007-05-09
Ok, I figured a few things out.

The splash and boot progress bar is called the usplash.

And now I have the usplash up and running on one of my computers. This one happens to be a widescreen.

I have a few concerns left:
1) the imaged is stretched. i assume it is because I have a widescreen laptop (1680x1050). Are there any usplashes made for widescreens?
2) it is not centered. the usplash comes slightly lower than middle of the screen and far to the right of the middle of the screen. I am not sure what is causing this.

I have edited both my usplash:

# Usplash configuration file
xres=1680
yres=1050

and  my grub menu.conf, where the only changed line is this:

# defoptions=quiet splash vga=794

Any help is appreciated.

---

### Post by SoloSalsa on 2007-06-09
Oh, now I know what it's called!  I miss the usplash from Dapper so much, but I never knew what it was called, and therefor, what to look for to enable it.

How did you do it?

---

