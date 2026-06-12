---
title: "No File Manager After Ubuntu 12.10 Upgrade (Nautilus Totally Removed??)"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2012-10-26
Hi. OK, that upgrade (from 12.04 64-bit) didn't go so smoothly, hehe. Besides not being able to log in after the next reboot - due to, of all things, not being able to mount an NTFS partition ([https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1059726?comments=all](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1059726?comments=all)) - I found my system was without a file manager. Yep, Nautilus had been uninstalled, and nothing put in its place.

I did notice before upgrading it was saying it was going to remove Nautilus, but it also said it was going to upgrade certain related packages (like Nautilus plugins), and figured it should be fine, as I doubted the upgrade would really leave my system without a file manager.

However, during the upgrade I noticed I couldn't open the Trash or any links in Places, simply asking what file manager I wanted to use (with only Thunar in the list of choices). I figured the newer Nautilus hadn't been unpacked and installed yet, and while I thought it was pretty sloppy that I couldn't use it while the upgrade did its thing, I figured all would be OK upon rebooting.

However, no Nautilus, so I had to do a **sudo apt-get install nautilus** to get my file manager back. Obviously, it was no biggie for me to do so, but it's still astounding that the upgrade thought this was a good idea (to leave the system without a way to access files), so I thought I better mention it. I dare say those with less experience wouldn't have other file managers like Thunar or Marlin installed, and many newbies would probably be unaware "File Manager" is actually a package called "nautilus" they can reinstall.

---

### Post by OzzyFrank on 2012-10-26
PS: When I installed Nautilus manually, it grabbed the old 3.4.2 version, which was basically the same as I had in 12.04 (only differences I could see were cosmetic, ie theming, and also "Safely Remove Drive" was no longer an option for USB devices). I just let the Update Manager install an update, and it upgraded Nautilus to 3.6.1 (I see they've now called it "Files"). I only noticed during that process that nothing is drawing the desktop, as I should have a bunch of launchers there, but it is blank (besides the wallpaper). Any idea how to get the desktop back? For now, if I really need the launchers, I can go to the actual folder, but that is less than ideal.

---

### Post by OzzyFrank on 2012-10-29
I still have nothing drawing the desktop...

---

### Post by OzzyFrank on 2012-10-29
OK, I figured I should look in **Dconf Editor**, and found that under **[COLOR="Red"]org > gnome > desktop > background[/COLOR]** the option **[COLOR="Red"]show-desktop-icons[/COLOR]** was disabled, and checking the box brought them back. I thought it had more to do with Ubuntu not knowing what was drawing the desktop (since the upgrade removed Nautilus), but it was even simpler. Now I just wouldn't mind getting my Trash icon back on the bottom panel...

---

