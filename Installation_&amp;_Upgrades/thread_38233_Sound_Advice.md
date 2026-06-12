---
title: "Sound Advice"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by crowMonk on 2005-05-30
I just installed Ubuntu.  And no sounds are working, not even system sounds.  There is some kind of sound support native on the ASUS board.  But I have installed a Turtle Beach, Santa Cruz sound card and would like to get that working.
How can I tell if Ubuntu is trying to connect to the right sound board?
Where can I find a driver for the Santa Cruz?
How and where do I install drivers in Ubuntu?

Thanks.

---

### Post by mingus on 2005-05-31
You need to verify that you have the driver module on your system, whether the kernel is recognizing the card, and whether it is loading the module.

But before that, if you have onboard audio and a separate PCI card, you want to if possible disable the onboard.  Having both available can create conflicts, even in Windows.  This can sometimes be done in the BIOS; check that out.

Get into a terminal and do "modinfo snd-cs46xx"; your card uses a Cirrus Logic controller.  That is the name of the ALSA driver for it.  It should be there already.

Next, do "lsmod | more".  Here you will see the driver modules the kernel has loaded.  Look for snd-cs46xx.  If it is there, you have a configuration problem with the mixer, etc., i.e., the sound is there but you can't get to it.  If you don't see it in lsmod, the driver didn't load.

If you don't see it in lsmod, do "dmesg | more" to look at the initial kernel load dialogue.  Make sure there aren't any errors in trying to load this module, such as an IRQ or DMA error.  This may happen if there is a conflict with the other sound device.  What to do now will depend on the error you see.  But if you don't see one, and again lsmod does not show it, then possibly the kernel may simply not know to load it.  (Similar to how plug-n-pray doesn't always detect the hw.)  So . . . 

reference:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Turtle+Beach&card=Santa+Cruz.&chip=CS4630&module=cs46xx](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Turtle+Beach&card=Santa+Cruz.&chip=CS4630&module=cs46xx)
there are other pointers out there that you can google, too.

The following worked in a similar scenario.  Really quite easy.

1.  Go to Synaptic and install modutils.
2.  Using sudo or root navigate to /etc/modutils/
3.  Open the file alsa-base in a text editor (I use nano in the terminal for this kind of stuff).
4.  Under # autoloader aliases, under the line "alias char-major-14 . . ." near the top add another line:
alias snd-card-0 snd-cs46xx
5.  If you need to specify driver loading options - and you'll have to google about for this, I don't know - that would go on the next line with the syntax:
options snd-cs46xx <parm>=<value>
(I would work this angle only if this procedure doesn't work.)
6.  Now in the terminal do "update-modules" - this will merge your newly added module into the already configured system modules for kernel loading
7.  Now in a text editor open the file /etc/modules.  This file instructs the kernel to load user-defined modules.  At the end add a line "snd-cs46xx" and save it.
8.  Reboot

After re-booting, again do an "lsmod | more" and hopefully you will see snd-cs46xx loaded (along with dependent modules).  If you do, go to System/Preferences/Multimedia Systems Selector and test if it is live.  Try both ALSA and ESD.  If you hear sound, go to Applications/Sound & Video/Volume Control and you should find a mixer.

From here on you are on your own for tweaking as it is specific to your card.

Hope this helps.

--mingus

---

