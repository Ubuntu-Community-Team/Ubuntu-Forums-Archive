---
title: "Known issue - Missing Deleted Items Folder"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by bobnutfield on 2008-05-19
Hello Everyone..

I know this is an issue with others who have upgraded to Hardy, but, as far as I know, it has not been corrected yet.  I know that the location of .Trash has been moved to ~/.local/share/.Trash to comply with new standards, but this is not an issue on my laptop (which was a beta-to-final install, but is on my desktop which was an upgrade.

The Deleted Items icon cannot be restored and the only way to delete items in that folder is with cd to that directory and use the rm command on each file.

Has anyone found a work around until this is fixed?

Thanks

Bob

---

### Post by fakeollie on 2008-06-01
Bob, my advice to you is to run Configuration Editor (alt+F2, gconf-editor, enter) and browse it to / -> apps -> nautilus -> desktop. On the right side you'll see the desktop configurations, make sure you check [x] trash_icon_visible. Then and you'll have a visible Trash icon on your desktop, which you can then use to browse deleted items or right-click and choose Empty Trash. 

Anyway, I also recently lost the ability to see (or add) the trash icon on the panel after a daily upgrade (I use the "proposed" repositories) for either nautilus or gnome-panel. I'd love if someone would chime in with a fix or suggestion in that regard.

---

### Post by cliff01 on 2008-06-02
I too lost the trash icon AND the mixer/volume control. It won't let me add either back on to my desktop. I wish I could "back out" of 8.04 till it's less buggy.

---

### Post by noynac on 2008-06-03
Deleted posting, which did not address issue.

---

### Post by fakeollie on 2008-06-03
I believe, noynac, that Bob --like me and cliff01-- can't add a trash icon to the panel. It happens. Either gnome-panel or nautilus is borked somehow and doesn't allow us to add a trash to the panel. If we go to a panel, right click, choose add, find the trash and add it... Nothing happens. Nothing is added to the panel.

I suggested to Bob how he could turn on the desktop gconf to show a trash icon on the desktop so he wouldn't have to resort to more exoteric browsing/scripting just to empty the trash. I mean... that's the whole point of having an icon (and the related filesystem abstraction) of a Trash area. I can't speak for the others, but myself, I'm not looking for any type of workaround. I'm looking for a way to make it work like it's supposed to (the trash/deleted items applet should be easily added and then work on a panel).

This is very cosmetic, but it's oh so incredibly annoying.

EDIT: this is also being discussed here [http://ubuntuforums.org/showthread.php?p=5103538](http://ubuntuforums.org/showthread.php?p=5103538)

---

