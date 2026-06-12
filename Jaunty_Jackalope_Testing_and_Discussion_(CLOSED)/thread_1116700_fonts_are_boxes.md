---
title: "fonts are boxes"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by paxmark1 on 2009-04-05
Running 9.04  Intel G45 video on board 4 GB ram intel dual core box.

I have been running 9.04 for maybe 10 days now, no real problems

I had given up on KDE and Kubuntu with the big changeover previous; did Debian, with KDE 3 but I am now liking Gnome and have kept Gnome and Ubuntu.  I realized was not acessing my windows fonts via ntfs-3g on the windows partition I had acess to previous.  No slick import function found.  so I added the mttscorefonts via aptitude.  There had been a lot of updates recentlly.  

Starting back up (went to windows to work on taxes) and xorg borked with a box with rectangles repeatedly on both kernels and recovery mode also.

Finally got I somehow on the previous kernel and recovery mode, but still very touch for Gnome X and terminal and all panels have just rectangles for text and text inputted into terminal comes off as text.

However alt-f2 got me opera and so I write.

Any help appreciated.  I did aptitude update and upgrade in shell prior to getting X up finally.  There were no upgrades.

If this should be in the X subcategory instead of installation and updates, please move.

peace,
mark

---

### Post by bapoumba on 2009-04-05
Moved to Jaunty.

I'm not running jaunty, so I cannot test. Make sure the language-pack-xx (xx fitting your localization) package is installed.

---

### Post by paxmark1 on 2009-04-06
So, how would I check this out on the CLI.  Elinks doesn't work so well because my forward slash is now a different character even on root recovery shell.  

I downloaded the  beta cd, so that is another option

peace mark

---

### Post by bapoumba on 2009-04-06
That would be:
```
apt-cache show language-pack-en
```
To see if English language package is installed.

Other packages may be needed, I have these:
```
bapoumba@SonyBlue:~$ apt-cache search language-pack-en
language-support-en - metapackage for English language support
language-support-translations-en - Additional translations metapackage for English
sword-language-pack-en - Sword modules for the English language
language-pack-en - translation updates for language English
language-pack-en-base - translations for language English
language-support-writing-en - Writing aids metapackage for English
```

---

