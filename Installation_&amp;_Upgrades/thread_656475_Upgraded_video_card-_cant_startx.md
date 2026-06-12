---
title: "Upgraded video card- cant startx"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by tamaker on 2008-01-02
I am determined to migrate from windows vista to Ubuntu as my primary machine and have used linux some (mostly the ubunty flavor and mostly in GUI, not too much command line, but some)... 

I have a gateway desktop that I dual boot vista and ubunto on ... I upgraded my video card to an ATI Radeon HD 2400 card and nowwhen I try to boot into ubuntu, I get command line only... X fails to start.

I just spent a few hours looking into it and after running lspci Im specifying PCI Bus 3:0:0 for my video card but it says no (display?) devices are found.

To verify that the PCI bus should be 3:0:0 I booted vista and used the device manager to see the BUS ID.

The card DOES allow for dual boot (i have one primary monitor and a 50" HDTV that I've only used once after upgrading my TV -- it was connected via DVI > HDMI connector but is now disconnected and Im using the VGA port on the card for my primary monitor.

my monitor and old card worked fine and I was really having fun getting up to speed with ubunty and had WINE running for the few windows-only apps I needed to run...

please help.

---

### Post by snakeeyes on 2008-01-02
give us information about ur old vga card, was that an ATI as well?

Try using the vesa driver to get xserver started. To reconfigure it:

sudo dpkg-reconfigure xserver-xorg

---

### Post by tamaker on 2008-01-02
> **snakeeyes said:**
> give us information about ur old vga card, was that an ATI as well?

Try using the vesa driver to get xserver started. To reconfigure it:

sudo dpkg-reconfigure xserver-xorg
I did run sudo dpkg-reconfigure xserver-xorg after looking up some other tips online, that seemed to rebuild / backup the config file used during startup... 

Still doesnt solve my issue though.

THe old video card was an ATI HD All In Wonder card.

---

### Post by tamaker on 2008-01-02
Ok - I researched VESA and figured out how to get that setup and in place ... and I was then able to start x, go to the ATI site, find the driver and install it. 

Im now struggling with:

1.) how to add higher resolutions as options (right now its 1024x767 - but Im wanting to run 1600x1200

2.) when my bootloader (gurbI think) loads I have all these entries for various ubuntu loads ??? I want to whittle it down to just the ubuntu and then the ms vista load options - what file is that located in so I can edit the file and specify which is defaulted if no u ser choice is made?

---

### Post by snakeeyes on 2008-01-03
you can add ur desired resolution manually in ur xorg file:

sudo nano /etc/X11/xorg.conf

You could also again reconfigure xserver and choose ur resolutions u require manually, also while configuring xserver u will need to configure ur monitor so then choose the medium option and choose ur resolution of choice.

---

