---
title: "Definitive answer for ATI - blank screen boot problem?"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by atarileaf on 2006-12-12
Has anyone found a one size fits all solution to the problem of booting the Live CD where you end up with a blank screen? It seems to affect those of us with ATI cards.

Here's the strange thing in my situation. I tried the following solution that someone else posted in another thread:

Hit F6 at the main menu and at the end type: break=bottom
Then, when a prompt comes up type:
mv /root/etc/X11/xorg.conf /root/etc/X11/xorg.conf.disabled
Then, hit Enter and type: exit
and it should boot up fine.

The thing is, the first time I did this, it DID work. Now I've tried again and done the exact same thing when I get to the prompt and type that line in, then exit, I get nothing. The cursor just sits there and blinks at me. It won't accept any commands. I'm at my wits end and can not get this thing to work. 

I can't figure out the alternate CD either. It seems much more complicated and I'm an absolute Linux virgin. I know nothing.

So, has anyone figured out how the heck someone like me can boot this Live CD?

Here's my specs again:

Asus K8V-X motherboard
Athlon 64 2800+ (1.8Ghz)
512 ram
80 gig drive
ATI All in wonder 9800 Radeon Pro

Thanks.

---

### Post by wpshooter on 2006-12-12
First of all did you check the integrity of your Ubuntu Cd by running the verification function found at the initial Ubuntu boot screen menu ?

Have you tried install using the video safe mode ?

---

### Post by atarileaf on 2006-12-12
Hi. Yes, I've done both. CD is fine. Safe graphics mode doesn't help. Same problem.

---

### Post by wpshooter on 2006-12-12
Then your only alternative is to install from the ALTERNATE CD instead of the DESKTOP (live CD) and then fix any video problems after you have the O/S installed.

Good luck.

---

### Post by Knilch2000 on 2007-01-01
I had / have the same problem with live CD. Even after installation the problem continues.

I had to adjust xorg.conf and add options to the "Device" section for the ati driver. I don't know which one of them did the trick, sorry, but I think it was either "AGPSize" or "GARTSize", or disabling "AGPfastwrite".

Try to boot to prompt, adjust xorg.conf and then startx

```

Section "Device"
        Identifier      "ATI R350 Radeon 9800 Pro"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option "AGPMode" "8"
        Option "AGPSize" "64"
        # Option "AGPFastWrite" "on"
        Option "AccelMethod" "XAA"
        Option "ColorTiling" "on"
        Option "DynamicClocks" "on"
        Option "RenderAccel" "true"
        Option "TripleBuffer" "true"
        Option "DRI" "true"
        Option "EnablePageFlip" "true"
        Option "EnableDepthMoves" "true"
        Option "XAANoOffscreenPixmaps"
        Option "BusType" "PCI" #!!! for direct rendering to work
#       Option "GARTSize" "128"

```

hope this helps..

---

