---
title: "Restoring old evolution files"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by loren41 on 2010-07-02
In an attempt to restore my ubuntu 9.04 desktop to its original settings, I entered the following in Terminal:
rm - rf .gconf. gconfd .gnome .gnome2 .terminacity

and then reset.

The new desktop is cleaner, but now Evolution Setup Assistant wants me to reinstall.  I don't think I have an archive file, so should I use the Assistant to install?  Will I lose my mail, calendar and tasks if I do?

What if I just install version 9.1?  Will it install using my old evolution files?

---

### Post by MechaMechanism on 2010-07-02
Make a backup of the .evolution directory.  Just right click the .evolution folder and select copy and paste wherever you want.  This should create a backup.  Now go ahead and do the setup wizard and see what happens.  No luck?  Then report back here.

---

### Post by loren41 on 2010-07-02
When I right click .evolution, a window displays with three choices - add to bookmarks
        - Show hidden files
        - Show size column

---

### Post by loren41 on 2010-07-02
Sorry, I was in search mode rather than the browser.:redface:

---

### Post by alterpinguin on 2010-07-02
if you cannot backup your
$home/.evolution
directory
then "mv" (move)
it to another !save place.
---
maybe rename it to:
my_old_evolution
-
then do a new install of evolution for your user.

After this, it creates a new .evolution directory
rename this to: new_clean_evolution
and rename your old... or better do copy (so you still save the original one)
cp -Rv my_old_evolution .evolution
-
that are commandlines you have to enter in a terminal, when you are in your home-directory ....(maybe lookup man-page for cp    man cp)

---

### Post by loren41 on 2010-07-02
Thanks Mecha for the quick response.  It didn't click with me when I read that Evolution files are readable, therefore, subject to the usual file commands.

---

