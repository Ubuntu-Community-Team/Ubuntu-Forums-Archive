---
title: "Display refresh 60Hz after install"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Anteaus on 2007-05-06
Feisty 7.04 worked fine for me from the CD, but after installing to HD the display is limited to 1024x768 max, and stuck on 60Hz refresh. I could live with 1024, but with 60Hz on a CRT I would end-up with a headache.

In fact I'm trying to solve the problem using a remote desktop, to avoid having to stare at the flicker. 

I looked at the  config file in /etc/X11, and the max horzontal rate for the generic monitor was 56kHz, which would explain the trouble.  However, changing it to the monitor's actual max makes no difference at all, not even after a restart.

Any ideas why it's stuck on 60Hz when it worked correctly from the live CD?  

Display is ATI Rage 3D Pro, not exactly the latest but a very well-known card so should be recognised. 

BTW I'm a reasonably experienced Debian user, but first-time install with Ubuntu.  

Might also be worth mentioning that the installer bombs-out at the bootloader section if you set grub to install to anywhere other than the MBR. In my case (hd0,1). This seems to be a bug.

---

### Post by Anteaus on 2007-05-07
OK, so a complete reinstall fixed the display issue. Still none the wiser why it happened but at least it's fixed.

---

