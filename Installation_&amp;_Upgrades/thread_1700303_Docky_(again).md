---
title: "Docky (again)"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by TimmyK. on 2011-03-04
Please see [this thread]("http://ubuntuforums.org/showthread.php?t=1698202"). In short, my problem is is that the docks are behind the windows, and so when I move my mouse over the icons and they enlarge, the tops are cut off. Worse, one of my docks on autohide isn't visible unless I have all windows minimized. I can't seem to find any setting on Docky or elsewhere for whether it is in the front or the back.

---

### Post by rvchari on 2011-03-04
> **TimmyK. said:**
> Please see [this thread]("http://ubuntuforums.org/showthread.php?t=1698202"). In short, my problem is is that the docks are behind the windows, and so when I move my mouse over the icons and they enlarge, the tops are cut off. Worse, one of my docks on autohide isn't visible unless I have all windows minimized. I can't seem to find any setting on Docky or elsewhere for whether it is in the front or the back.

the pic shows u r using cairo dock. i had bad experiences with cairo dock that will mis behave as and when it feels !!! i used to remove the .files (dot files) in my home directory (all related to cairo dock) and re run. my problem used to get solved !

but now i am happy with AWN... i had bid adieu to cairo since the time i started using AWN

---

### Post by TimmyK. on 2011-03-04
I don't understand about the Cairo Dock. Please remember I am new. Can you please give me detailed instructions on how to fix this, and explain what each item is? I have no idea what a dot file or a home directory is.

Does AWN give more advanced features and settings? I don't want it if it's less customizable as Docky.

---

### Post by rvchari on 2011-03-05
> **TimmyK. said:**
> I don't understand about the Cairo Dock. Please remember I am new. Can you please give me detailed instructions on how to fix this, and explain what each item is? I have no idea what a dot file or a home directory is.

Does AWN give more advanced features and settings? I don't want it if it's less customizable as Docky.

for cairo docks...
open nautilus window, it will show your home directory
right click and activate show hidden files. (hidden files have a prefix (dot)).
check for .cache and .config folders. it might contain cairo. simply delete that folder with shift button pressed. log out and log in. your cairo dock should show up like before. if not then check .gconf or other folders. delete everything that shows up as cairo (only in ur hidden directories)

still if problem is  not solved, then follow this link for AWN

[http://http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html]("http://http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html")

---

### Post by rvchari on 2011-03-05
i am sure you will like the feel and behaviour of AWN. once you get used to it, uninstall cairo-dock. cairo gets buggy at times and we tend to loose interest over a period of time with frequent bugs !!!

---

### Post by TimmyK. on 2011-03-05
I'm afraid I don't know what the nautilus window or home directory is, and I don't know what to right-click.

---

### Post by rvchari on 2011-03-05
> **TimmyK. said:**
> I'm afraid I don't know what the nautilus window or home directory is, and I don't know what to right-click.

nautilus is the default file manager for ubuntu desktop. if ur desktop has icons, clik on the home icon on ur desktop. it will open in nautilus.
in the window, right click and make it show hidden files. hope u got my point....

---

### Post by TimmyK. on 2011-03-17
I found the problem. For some reason it only does this when VMware Player is opened.

---

