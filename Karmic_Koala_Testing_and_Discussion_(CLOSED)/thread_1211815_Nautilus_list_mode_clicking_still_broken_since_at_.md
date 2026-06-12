---
title: "Nautilus list mode clicking still broken since at least Jaunty"
date: 2009-07-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-07-13
Is it just me or does Nautilus hate people clicking on folders in list mode?

Whenever I single-click one folder and then want to single-click another folder, Nautilus goes crazy and starts expanding the folders in while still in list mode.

Anyone else experiencing this?

---

### Post by taavikko on 2009-07-13
One guestion to make it clearer...

You click on the folder (the name) and it opens the folder
then click on other folder (the name) and it opens the folder
Not using tabbed viewing?

Or your mixing the clicking on the expander and the folder (name)?

As for now, as far as I understand, the default behaviout in the list mode is to open the folder when clicking on the name.
expander is used when viewing the contents of the particular folder in the list mode.

---

### Post by airtonix on 2009-07-13
Make sure you are not clicking on the 'expander arrow' which is the toggle for opening/closing the folder list contents inline. You can't see my mouse cursor here, but i'm hovering over the arrow next the folder named "Public" in the right hand pane.

Clicking on those arrows will toggle the folder contents visibility.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=120962&stc=1&d=1247500500[/IMG]


If that isn't your issue, then make sure that (within the nautilus configuration interface) you do not have it set to "Single click to open items"
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=120963&stc=1&d=1247500500[/IMG]

---

### Post by ktp on 2009-07-13
> **Starks said:**
> Is it just me or does Nautilus hate people clicking on folders in list mode?

Whenever I single-click one folder and then want to single-click another folder, Nautilus goes crazy and starts expanding the folders in while still in list mode.

Anyone else experiencing this?

I have seen similar stuff with archive manager.  I can't find what exactly causes the issue but when it happens thing just don't work right.  It seems like something to do with list viewer and selection.  When it happens, I have noticed that the "row selection" is not completed selected...only first cell will be selected.  The only way to get it fixed is to restart the application.

---

