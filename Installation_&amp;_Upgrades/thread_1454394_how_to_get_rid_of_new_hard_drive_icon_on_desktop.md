---
title: "how to get rid of new hard drive icon on desktop"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by Teber on 2010-04-14
i'm using karmic. today i mounted a new hard disk, 1 Tb, as per the instructions i found in the wiki. first of all i wish to express my gratitude to all who contributed there. the instructions were most helpful and everything went fine. my new drive can be accessed for both read and write and automounts like the good drive it is.

however, there is this this icon for the new drive on my desktop. is there a way to get rid of it? i can access the drive perfectly well through the places menu. i like my desktop clean...

many thanks in advance.

---

### Post by ajgreeny on 2010-04-14
You must have mounted it in /media, I imagine, as all disks mounted in media will show on the desktop by default.

There are two ways around this, either change the mount point of the disk from /media to /mnt, or if you don't even want usb disks to show on the desktop, you can change the setting in *gconf-editor ->apps ->nautilus ->desktop* by removing the selection in **volumes_visible**.

---

### Post by nickbooker on 2010-04-14
> **Teber said:**
> i'm using karmic.

[...]

however, there is this this icon for the new drive on my desktop. is there a way to get rid of it? i can access the drive perfectly well through the places menu. i like my desktop clean...

many thanks in advance.

You can disable displaying of mounted drives on the desktop, but the configuration option isn't available in the Preferences tools, so...

Press Alt+F2, and type "gconf-editor" into the Run dialogue box that appears.

This will bring up a program called "Configuration Editor", which you can use to tweak the GNOME settings database manually.

Navigate in the tree on the left to /apps/nautilus/desktop - make sure the desktop entry is highlighted.

Remove the tick from the "volumes_visible" entry in the right-hand pane, and the icons should disappear almost immediately.

You can then close the Configuration Editor.

I hope this helps.

Nick

---

### Post by nickbooker on 2010-04-14
Oops unintentionally duplicated ajgreeny's answer - didn't refresh for 10 mins, sorry.

---

### Post by Teber on 2010-04-14
wow! this forum is a truly amazing place! (which i already knew, of course)

thanks the two of you! the nautilus thingy did the job!

---

