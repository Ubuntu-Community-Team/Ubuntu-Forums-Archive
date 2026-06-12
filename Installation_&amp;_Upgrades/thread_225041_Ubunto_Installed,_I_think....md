---
title: "Ubunto Installed, I think..."
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by WiredPig on 2006-07-28
I have installed, I believe, Ubunto Dapper on my Toshiba M45-S265.

I say I think because durring the install the screen went blank while installing modules (at about 65-75%) and I just hit enter when the HDD light stopped blinking until the system rebooted.

All was good after the reboot. I got the login screen and entered my user ID/Pwd. However, when I log in, I get a blank screen with the mouse pointer on it. I am pleased that the pointer does move and, after inactivity, the screen blanks.

*[edit] I am able to log in under the Fail Safe Terminal, but not Gnome or Fail Safe Gnome... So I was able to set the root password... but I cant figure out what I need to fix to get Gnome to load.*
Anyone have any advice?

Thaks,

Wired Pig

---

### Post by diepruis on 2006-07-29
Could you please post /etc/X11/xorg.conf?

---

### Post by WiredPig on 2006-07-29
> **diepruis said:**
> Could you please post /etc/X11/xorg.conf?

I'll give it a shot once I get home from work this evening.

Is there anything in particular that your looking for? I ask because I didnt configure the networking durring install and will be transcoding everything from the laptop via my PC.

Thanks,

WP

---

### Post by diepruis on 2006-07-30
I'm particularly interested in the "Section "Device"" part. Could you perhaps copy the file to a usb drive and post the entire thing?

---

