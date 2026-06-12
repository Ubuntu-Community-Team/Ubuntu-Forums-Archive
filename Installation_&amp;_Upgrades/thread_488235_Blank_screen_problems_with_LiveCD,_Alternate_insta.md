---
title: "Blank screen problems with LiveCD, Alternate install"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by NickS on 2007-06-29
Hi: I have read through all the other posts on people having blank screen problems with their Ubuntu installs, and none of them have helped.

When I tried the LiveCD (normal) install mode, it showed the splash screen, and then went blank (unresponsive to keystrokes, etc).

When I tried the LiveCD (safe video) mode, same thing.

I've been trying the Alternate CD, and it gets up to the actual install part ('preparing' and 'unpacking' various things, about 3% completion on the stage after it asks you about HTTP proxy), before it goes blank. The CD continues to spin for about 20-30 minutes afterward, and then everything goes quiet. The system does not respond to keystrokes.

(And yes I verified both LiveCD and Alternate CD)

I have a Gateway M275 Laptop:
Pentium M 1.7Ghz, 504MB ram, 50+GB of HD space. Graphics: Intel 82852/82855 GM/GME (onboard).

Please help!

---

### Post by cddot on 2007-06-30
Don't know if it would help in your case, but I got past my blank screen problems by removing the following kernel boot options "quiet splash", and adding "vga=791 noapic" (all no quotes).

---

### Post by NickS on 2007-06-30
Your advice allows me to run the normal LiveCD installer - thanks.

However, Linux still wouldn't run - after the GRUB menu, the screen went blank, as usual.

After poking around for a while in 'safe mode' (the second ubuntu option from the GRUB menu), I realized that the problem was due to my Intel graphics chipset. All I had to do to fix the problem was (from the command line in safe mode - $ is the prompt):

$ nano /etc/X11/xorg.conf

and scroll down until you find the part that says:

Section "Device"

Add the option: Option "DisplayInfo" "FALSE", so it will look something like:

Section "Device"
      Identifier "Intel ..."
      Driver "i810"
      BusID "..."
      ...
      Option "DisplayInfo" "FALSE" 
EndSection

Note: the ellipses ('...') indicate that your xorg.conf likely has different values than mine for these settings - just keep whatever you currently have.

Hit control-X, then 'y' then Enter. Then type

$ shutdown -r now

Hopefully this will help anyone who has been suffering similar blank screens with their onboard Intel graphics.

-Nick

This problem is due to a 'video BIOS' problem with certain intel chipsets, whatever on earth that means.

---

### Post by ibgeorgeb on 2008-07-07
> **NickS said:**
> All I had to do to fix the problem was (from the _command line_ in safe mode - $ is the prompt):

$ nano /etc/X11/xorg.conf


I'm still having problems with the M275. I'm at the second line GRUB menu, "Start Ubuntu in safe..." Now, how do I get to the **command line**? I see the Boot Options line. Thank you. ibGb

---

