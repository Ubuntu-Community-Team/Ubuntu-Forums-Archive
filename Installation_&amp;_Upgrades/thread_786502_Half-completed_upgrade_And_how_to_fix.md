---
title: "Half-completed upgrade? And how to fix?"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by Zalbor on 2008-05-08
I turned on my computer this morning and saw a lot of updates, most of them for gnome and kde packages. I started the download and installation, and then switched to another terminal. But when I came back the screen wasn't right and wasn't getting fixed, so I pressed ctrl+alt+backspace.
Then I remembered I had started an update, and that I don't know if it was completed when I restarted X. I checked for updates again and it said my system was up-to-date, then I checked for broken packages and there were none.
But then I noticed some strange things: The letters of icons on my desktop were bigger than before, and under each icon both on the desktop and other nautilus windows was the file's size. And in gnome-system-monitor, processes from all users (including root) appear as well as mine.
I did the same upgrade on another computer, and these things didn't happen here, so I figure they were caused by half-installed packages because I restarted X during the update. I guess reinstalling the packages will fix the problem, but I don't remember all of the ones that got upgraded.

Is there a way to find out which they were, and reinstall them? Something like a package installation log maybe? Or, another way to make sure everything's configured correctly?

---

### Post by Partyboi2 on 2008-05-08
Open up synaptic package manager and under file select history, you should see what updates were installed on which day.

---

### Post by Zalbor on 2008-05-08
Thank you, but apparently that only logs packages newly installed... Is there a way to see which ones were upgraded?

EDIT: The problem seems to have been solved. I installed some other packages, and synaptic configured the upgraded ones as well.

---

