---
title: "No more bookmark for Firefox 9.0.1 in 11.10"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by SteMMo on 2012-02-04
Hi all,
since i upgrated to 11.10 (adn also to 11.04) i have problems handling bookmarks.
The bookmark list is empty, the library window is empty and if i try to add a link, i don't have any result.
Any idea?
Is there any log for firefox?

Thanks

---

### Post by ajgreeny on 2012-02-04
> **SteMMo said:**
> Hi all,
since i upgrated to 11.10 (adn also to 11.04) i have problems handling bookmarks.
The bookmark list is empty, the library window is empty and if i try to add a link, i don't have any result.
Any idea?
Is there any log for firefox?

Thanks
Try a new profile.  Rename the **~/.mozilla/firefox/#x#x##x#.default** folder in your home as a backup, and start FF again.  You can then try to restore your bookmarks from the **~/.mozilla/firefox/#x#x#xx#.defaultbackup/bookmarkbackups** folder and see if they really are gone.

The files in the bookmarksbackups folder are plain text which you can read with gedit to see if there is anything there.

---

### Post by SteMMo on 2012-02-04
Thanks,
i almost solved running firefox in safe-mode; in this way i restore the bookmark default list.
Now i'm not abel to restore my old bookmards cause i do not find the import command :(.
In the Library window i have no buttons!

---

### Post by ajgreeny on 2012-02-04
What, no "Import and Backup" showing in the top bar of library window?

---

### Post by SteMMo on 2012-02-06
No, i only see the orange arrows and the Search box, no buttons in the middle !?!?!?!?
How this is possible ????

---

### Post by ajgreeny on 2012-02-06
> **SteMMo said:**
> No, i only see the orange arrows and the Search box, no buttons in the middle !?!?!?!?
How this is possible ????
No idea.  Sorry!

---

### Post by lovinglinux on 2012-02-07
I have seen a similar problem on another thread, but I can't remember the solution.

If you are able to run it with safe mode, then is an extension messing things up. Try to disable the Global Menu extension and the Ubuntu Firefox Modifications extension to see if there is any change.

---

### Post by SteMMo on 2012-02-08
Yes!
Running in safe-mode i'm able to access to Import/Export menu.
From here i imported an old json bookmarks file and now i have my old links.
Once returned to standard mode, the button disappairs.
In the meantime the system updates to 10.0 but nothing change (in standard mode) :(

---

### Post by lovinglinux on 2012-02-09
> **SteMMo said:**
> Yes!
Running in safe-mode i'm able to access to Import/Export menu.
From here i imported an old json bookmarks file and now i have my old links.
Once returned to standard mode, the button disappairs.
In the meantime the system updates to 10.0 but nothing change (in standard mode) :(

So, it is an extension or theme. Are you using a custom theme?

---

### Post by SteMMo on 2012-02-10
If you mean a theme for firefox, no, the predefined one.

If disabled every extension until I found that the only one that make the button appair is Global Menu Bar Integration 2.0.2.
When it is disabled i see the buttons 'Organize', 'View' and 'Import and save' (i guess that are the names in English).

---

### Post by lovinglinux on 2012-02-11
> **SteMMo said:**
> If you mean a theme for firefox, no, the predefined one.

If disabled every extension until I found that the only one that make the button appair is Global Menu Bar Integration 2.0.2.
When it is disabled i see the buttons 'Organize', 'View' and 'Import and save' (i guess that are the names in English).

So, that is the culprit, isn't it?

---

### Post by SteMMo on 2012-02-11
Yes, i think. Now i'm running without that one.

Other problem is when i ask to add a new bookmark: the first window is ok but when I try to enlarge it to select a different folder, the window does not resize and then i see only a part of the window. :confused:

---

### Post by lovinglinux on 2012-02-13
> **SteMMo said:**
> Yes, i think. Now i'm running without that one.

Other problem is when i ask to add a new bookmark: the first window is ok but when I try to enlarge it to select a different folder, the window does not resize and then i see only a part of the window. :confused:

The bookmark manager window? You could try to add by simply clicking the star in the address bar and customize the location there. You can also drag the tab to the bookmarks sidebar.

I rarely use the Bookmark Manager. Only when I need to export/import.

---

