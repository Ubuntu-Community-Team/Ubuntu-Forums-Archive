---
title: "Installation hangs at 98% (pcmcia &amp; acpi)"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by thonuz on 2005-08-11
I'm having some trouble getting Ubuntu with acpi working on my Sony Vaio fs-660/W.
First, If I do normal installation the system hangs at 98% (pcmcia)
So I tried "nopcmcia" at boot which also does not work.

Second. I installed with acpi=off at boot which gave me a nice 1280x800 working desktop without wireless of battery monitoring functions.
I removed anything "acpi" in grub boot.lst whic got my wireless working, but the battery monitor stays on not plugged in if I plug or un-plug it. Then some warnings about HAL start on any reboot. (who is Hal?) I then installed NVIDIA, which on boot gave me a blank screen. Nvidia works in recovery mode though, so i suppose my frequency needs tweaking. I've tried some other modline settings and can now get a white screen rather than the black one. 

Third. I tried the expert install because I need acpi. This allowed me to skip pc card services. on reboot after initial install it hangs at starting pcmcia services, even though I specifically answered no in the 2 times it asked me on install. 

My 2 questions are:
1. How can I install without pcmci, but with acpi. I need acpi as removing the off option later in grub does not work.

2. Why does Nvidia work in recovery. i get the logo and x. Does this mean I should use the x settings in recovery? maybe its really using vesa.

Thanks so much to anyone who can help.

---

### Post by thonuz on 2005-08-11
hw-detect/start_pcmcia=false works only to get it started, on reboot of second part of installation is freeze at that damn pcmcia again.

---

### Post by thonuz on 2005-08-14
Does anybody know how to install Ubuntu without pcmcia for good? ](*,) 


Thanks

---

### Post by AuthorityAction on 2005-09-04
I seem to be having the same trouble you had during install.  Hopefully we can work together and get the problem fixed.  I just downloaded Ubuntu today, so give me a couple days to mess around with it.

What are your specs?

Mine:

Intel Centrino "Sonoma" 1.73 GHz
nvidia GeForce Go 6600 1280x800
Intel Pro Wireless 2915

---

### Post by thonuz on 2005-09-05
I got pretty much the same specs.
 The ubuntu installer seems to be flawed here.
and install options are limited with ubuntu. Maybe they will fix it with the next release, maybe not.  Breezy is available linux 5.10 [ftp://cdimage.ubuntu.com/cdimage/releases/breezy/colony-4/breezy-install-i386.iso](ftp://cdimage.ubuntu.com/cdimage/releases/breezy/colony-4/breezy-install-i386.iso)
I have not had a chance to try it yet. 
If its debian you want try kanotix with nopcmcia. works on every laptop I've tried so far. Toshiba m45, Sony vaio, HP L2000, and a couple others. They should have a new release very soon. Maybe a few days with 2.6.13 kernel.
I tried Ubuntu because it was so popular, but have never got it to install in any of the above  laptops. 
Sorry, but I think ubuntu is over-rated (too and I won't try it again for a while. Hardware support is limited in my opinion..

---

### Post by i-tech on 2005-09-12
I have the same problem with my vaio(FS215s)!!! It freezes on 98% when Detecting hardeware to find Cd-Rom.
hw-detect/start_pcmcia=false didnt worked out.
Is there no way to fix this thing?.
Does debian works without problem? Maybe i should use Debian?

---

### Post by mindspin on 2005-09-12
Same trouble here on a Vaio VGN-FS285H

It's not mine, so I'm not too much depressed........

but help would be cool because it should run ubuntu sooner (not) later  ;-) 

mindspin

---

### Post by ninja_indiano on 2005-10-09
BUMP...same problem here

---

### Post by ninja_indiano on 2005-10-09
Ok done some reading.....

I&#180;m currently installing Ubunto and have not yet finished...

I but I did "linux acpi=off" in the place where you supose to hit enter when the CD boots.
and seems to be working...

PS: The instalation is not yet finished...Using a Vaio S460

---

