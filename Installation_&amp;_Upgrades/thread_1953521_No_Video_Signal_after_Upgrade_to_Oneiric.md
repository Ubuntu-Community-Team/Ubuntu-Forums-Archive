---
title: "No Video Signal after Upgrade to Oneiric"
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by r_avital on 2012-04-06
Hi all, 
Here's the situation (all Ubuntu versions mentioned below are 64bit):


[LIST=1]
[*]AMD64 system running Lucid 10.04 LTS just fine.
[*]Performed upgrade to 10.10 via update-manager - booted just fine.
[*]Performed upgrade to 11.0 - booted to blank screen with NO VIDEO SIGNAL.  Message on monitor was "No signal."  My video setup is simple vga.
[*]Gave up on upgrade, downloaded 11.10 to bootable USB stick, booted up, 11.10 installed flawlessly.
[*]Reboot - Again, no video signal.
[*]Left it alone, and after what seemed like 2 or 3 minutes, video signal is back, I can log in, install proprietary nVidia video driver, everything is fine.
[/LIST]
Every reboot (soft or hard) results in the same behavior: "No signal" message on screen for a few seconds, then video signal is back, I can log in.


For grins, I rebooted several times holding down left Shift key, monitor displayed "GRUB starting" for a second or two, then blank - "No signal" message, then signal returns and I get regular login screen.


Which means I can't boot into GRUB, but the issue I'm concentrating on is the screen temporarily going dead with no signal.


Installed a new SATA dvd drive - "No signal" on reboot, but this time it stayed there indefinitely (I gave up and re-installed Lucid).


Is there a change in Oneiric that causes this behavior?


TIA

---

### Post by r_avital on 2012-04-13
Bump :)

---

### Post by efflandt on 2012-04-14
Try using **nomodeset** kernel boot parameter.  I still have 10.10 on another and never had to use any boot parameters with that, but for 11.10 I have to use **nomodeset** or I got the no video signal, even at a time when 10.10 and 11.10 (both 64-bit) were using the same exact nvidia driver version.

I think it is because it is now using both nouveau and nvidia, which cooperate fine as modules, but not so fine directly from the kernel (kernel mode setting).

But without being able to access the grub menu I am not sure how you can get the nomodeset parameter entered to boot properly do edit /etc/default/grub and run sudo update-grub unless you can boot from install CD or iso on USB and do a chroot (per Ubuntu grub2 wiki).  This is the line you want to modify in /etc/default/grub:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

---

### Post by r_avital on 2012-04-30
efflandt, thanks for the suggestion, I'll give that a try!

---

