---
title: "Upgraded to Maverick Meerkat, getting black screen"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by Jason Spaceman on 2010-11-10
I upgraded my laptop from Ubuntu 10.04 to 10.10 (Maverick Meerkat).  Upon rebooting after the upgrade I get a black screen.  No login window, nothing.  Just a black, empty void on my screen.

My laptop has a Nvidia graphics card, and reading around on the internet I heard that there is a problem with Meerkat and Nvidia cards, something to do with the driver or some such thing.

Is there a way to fix this?

I'm wondering if it's possible to boot Ubuntu into a command line interface instead of X Windows, log in, and change the driver settings in xorg.conf?  How would I go about booting into the command line?  Is there a sequence of keys to press at boot time?

---

### Post by sikander3786 on 2010-11-11
Try to edit the Grub entry. If you don't see the Grub menu by default, press and hold down the Shift key until Grub menu pops up.

Highlighting the 1st entry in Grub menu, press 'e' to edit it. Navigate to "quiet & splash", delete them and type "nomodeset" in their place. Press Ctrl + X to continue booting and see if it worked.

If it didn't, from the same Grub menu, select the 2nd option i.e, recovery mode, you'll be presented with a choice to reconfigure graphics. Reconfigure and reboot to see if it worked this time.

---

### Post by Jason Spaceman on 2010-11-11
Unfortunately I'm using LILO, not Grub.

---

