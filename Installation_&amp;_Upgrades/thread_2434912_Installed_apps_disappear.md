---
title: "Installed apps disappear"
date: 2020-01-13
forum: Installation &amp; Upgrades
---

### Post by lwalper on 2020-01-13
Where do the installed apps go? They just seem to install and then disappear without a trace. Is there somewhere to see a list of what has been installed. Is there some way to leave an icon on the desktop. It's a huge empty piece of real estate just begging for some action. I press the Super key and a few items pop up, but not usually what I'm looking for.

---

### Post by deadflowr on 2020-01-13
> Is there somewhere to see a list of what has been installed. 
super + A will show all desktop programs installed. (you may have to toggle a setting; it can be set to either frequently used or all.)
The setting should be at the bottom of the overview screen area.

dpkg --list will show all packages installed (but that includes a ton of library packages and other assortments of base packages)


> Is there some way to leave an icon on the desktop.
On 18.04 you should still be able to set the file manager to handle the desktop which will allow apps located in the Desktop folder to show on the desktop.
It's a simple dconf setting to enable it, or install gnome tweaks and set it there (same setting) just set it to show icons on desktop)
I dislike icons on my desktop, but from memory the first time you try to launch something it'll ask to mark it as trusted.

---

