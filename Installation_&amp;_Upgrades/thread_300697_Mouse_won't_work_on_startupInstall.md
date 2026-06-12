---
title: "Mouse won't work on startup/Install"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by andrew.b.reed on 2006-11-16
Hi,

I have booted my PC with the desktop CD, and have been presented with the Ubuntu desktop. Only one problem - my mouse isn't working. It's a MS Basic Optical Mouse 1.0A. I have it plugged into a USB port, but I have also tried to startup with the PS/2 adapter and obviously plugged into the ps/2 port. Still didn't work. The mouse works fine in Suse 10.1...

Any ideas?

Andrew

---

### Post by woedend on 2006-11-16
what is your mouse driver in /etc/X11/xorg.conf
if it's ImPS/2, try using ExplorerPS/2
actually, can you at all post your xorg.conf file?
do you have Suse's xorg.conf also by chance?

---

### Post by andrew.b.reed on 2006-11-16
Hi, my mouse driver will be as it is off the CD - presumably. I haven't actually installed - just loaded the LiveCD part. I would post my Suse config except it's at home right now, and I'm at work... I'll be sure to take a note of it, but will then go about destroying the Suse setup by tabbing about the Ubuntu desktop to start the install. I'll just try my luck that eventually the mouse will be configured right - shame it doesn't work straight off the CD for me.

---

### Post by andrew.b.reed on 2006-11-19
Hi, InputDevice for the mouse is indeed using ExplorerPS/2, as was the Suse installation. I carried on and installed ubuntu via much frustration with the keyboard. No surprises really that it didn't happen to change the outcome at all. Interestingly, I navigated my way to the Ubuntu device database. My sound doesn't seem to work either with the test that it ran. Such a shame. Perhaps my motherboard is a tad too old or something?

---

### Post by andrew.b.reed on 2006-11-29
Got it working - specified "noapic" as a boot option.

---

