---
title: "Task Manager changes size all the time"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by Jummel on 2011-05-29
Hi,

After upgrading from 10.10 to 11.04 all of a sudden, the task manager or task bar, keeps changing length. The individual window "buttons" themselves keep changing size - flashing even, and the space between them also changes. It is driving me nuts! The little system tray(?) icons no longer appear in the system tray, but all stacked on top of each other in the top left corner.

Help!

---

### Post by Zorael on 2011-05-30
I have no idea what might cause this, but you could try to recreate plasma's settings to its defaults. Perhaps the plasma version upgrade between 10.10 and 11.04 include changes to how it handles settings? I only know these issues are largely idiopathic.

Open Dolphin and navigate to **~/.kde/share/config/**. You may have to enable hidden file visibility for the **.kde** directory to become visible - you can change this in View -> Show Hidden Files (or use the keyboard shortcut Alt+.). There, rename your **plasma-desktoprc** and **plasma-desktop-appletsrc** files to something else, or move them somewhere else entirely. Finally either log out and back in, or restart plasma by other means.

One terminal command that does all that, in one line for easy copy/pasting;
```
cd ~/.kde/share/config; mv plasma-desktoprc plasma-desktop-appletsrc ~/; kquitapp plasma-desktop; sleep 5; plasma-desktop &>/dev/null
```
The command is safe. Afterwards those files should have been moved to your home directory, and your plasma settings should have been reverted to their defaults. Feel free to remove those files if everything checks out.

---

