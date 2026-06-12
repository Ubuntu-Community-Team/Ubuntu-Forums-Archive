---
title: "Kubuntu nepomuksearch dies"
date: 2009-09-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by forcecore on 2009-09-05
i have not used search on Kubuntu earlier alphas and even with 9.04 release but now i try to search files every time nepomukservice just dies with message on status bar, has anyone problems with searching on Kubuntu A5 or previous alphas?

---

### Post by jithin1987 on 2009-09-05
What does system settings -> desktop search says (In advanced section).
Check .xsession-errors for any clue.

---

### Post by forcecore on 2009-09-05
nothing it is in default settings to search from user but why the heck i need some service, it should work like Gnome or windows search that it just searches trough files.

---

### Post by jithin1987 on 2009-09-05
You have to check if strigi Desktop File Indexer  is enabled in system settings -> Desktop Search. If not enable it and it will work.

---

### Post by forcecore on 2009-09-05
same story i enabled it but looks like KDE search is very poorly designed, search must be robust not sensitive to everything and basic search should work without services.

---

### Post by jithin1987 on 2009-09-05
I am not sure I got what you meant by services. If you have enabled strigi desktop file indexer and in the advanced settings you can configure which folders to index.

It pretty much worked for me. Even if you have enabled it in basic settings, look for the status message displayed under the check box. If there is some problem with the desktop search it should be displayed there.

---

### Post by Gavin77 on 2009-09-05
If you open Dolphin and then use Control-F a normal Find Files/Folders dialog will open.

---

### Post by forcecore on 2009-09-06
> **Gavin77 said:**
> If you open Dolphin and then use Control-F a normal Find Files/Folders dialog will open.

Thanks a lot it works very well like it should, i removed that useless search toolbar and disabled that punk thing.

---

