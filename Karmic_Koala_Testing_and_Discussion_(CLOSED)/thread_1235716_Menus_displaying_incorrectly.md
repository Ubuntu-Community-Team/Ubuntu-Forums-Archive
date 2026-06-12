---
title: "Menus displaying incorrectly"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-08-09
This has been like this for as long as I can remember. Here are 2 screenshots. The left one shows the menu when the combo box is first clicked. The right one shows the menu after scrolling to the the last item. As you can see, both menus are the same height, and there was enough room the first time it showed for all the items. So why does the first have the blank area before the first item? This can happen even if there are too many items to be shown in one go. I appreciate the scroll buttons on the menu, but there shouldn't be any blank areas. It looks sloppy, and unprofessional.

---

### Post by taavikko on 2009-08-09
Didn't manage to reproduce this. (shiki-dust theme)
Does it happen with a new user? or different theme?  (if something has just b0rked the nautilus conf files)

though this happens to me occasionally (very rarely) in different programs so there might be a glitch in gtk

---

### Post by phenest on 2009-08-09
This is a fresh install and updated, but I haven't done anything other than that. Not even changed any software. Everything default. Happens with other users. Happens with different themes.

This also happens in Jaunty, Intrepid, Hardy, Gutsy, Feisty. Did you try the same example as in my screenshot? I also get this in other apps, such as Gimp. It only seems to be a problem with combo boxes, as far as I can remember.

---

### Post by phenest on 2009-08-09
Additional: it only happens if the menu edge exceeds (or reaches?) the screen edge.

---

### Post by tekstr1der on 2009-08-09
Looks like this has been going on for ever with gnome/gtk:

[http://bugzilla.gnome.org/show_bug.cgi?id=129463](http://bugzilla.gnome.org/show_bug.cgi?id=129463)

---

### Post by taavikko on 2009-08-09
> **phenest said:**
> Additional: it only happens if the menu edge exceeds (or reaches?) the screen edge.

yay, got the undesired function.
Dragged the nautilus preference window near bottom edge, and clicked the "list view default" combo box, dropdown menu then had the first entry displayed like your screensh.


[quote=tekstr1der]Looks like this has been going on for ever with gnome/gtk:

[http://bugzilla.gnome.org/show_bug.cgi?id=129463](http://bugzilla.gnome.org/show_bug.cgi?id=129463)[/quote]
So it seems, though it seems to be marked fixed...

---

### Post by phenest on 2009-08-09
Interesting read. I understand the intent of the blank area, but aside from being ugly, the reason is invalid (see comment #21, 22, and 23 of the bug).

If I have understood this correctly, the reason is to have the current selection under the cursor when the menu appears. This provides another method to dismiss the menu, if the user does not want to make a change (other than clicking outside the menu). This leaves an ugly blank area on the menu with an insensitive arrow to show the user that other items are there.

There is no need for the current selection to be under the cursor when the menu appears provided the user has something else to click on to dismiss the menu if they have changed their mind (again, other than clicking outside the menu).

This is my proposal:
The drop arrow on the combo box that invokes the menu should be at the left hand side. When the menu appears, it will be to the right of the arrow, and leave the arrow uncovered so it can be clicked on again to dismiss the menu. This leaves the menu to be drawn fully without regard for where the current selection should be in relation to either the cursor or the combo box.

---

### Post by phenest on 2009-08-09
> **taavikko said:**
> So it seems, though it seems to be marked fixed...

Only because of the addition of the insensitive arrow, it would seem.

---

### Post by tekstr1der on 2009-08-09
Well, though the developers don't consider this as a bug anymore based on the slew of ignored dupes, I say we hit them with more reports. It's been a full month since last duplicate:). If the current behavior is considered the best solution for this issue, that's kind of sad. Different strokes, I guess, but I'd much rather see the large blank area filled with options. The best alternate solution is for app devs to avoid the gtk combobox completely.

---

