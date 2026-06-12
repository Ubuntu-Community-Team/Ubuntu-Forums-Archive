---
title: "Where to place downloaded fonts"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2010-02-03
Ubuntu 9.10

I just downloaded the MS core fonts form the ubuntu eye candy page.

Where/how do I place these font folders so I can use them in Open Office and other applications such as Evolution?

Thanks in advance. Bob.

---

### Post by dnairb on 2010-02-03
IIRC:

-Create a new folder in your home directory called .fonts

DON'T forget the leading period

-Copy the fonts to the folder you created above. Ensure you mark View > Show hidden files (or press ctrl-h) in Nautilus to see the .fonts folder

-Then in terminal, run the following:

sudo fc-cache -f -v

---

### Post by bob brazie on 2010-02-03
Worked like acharm. Thanks!

If I wanteded to un-do that command in the future and not use these fonts what would the terminal command be?

---

### Post by dnairb on 2010-02-03
To uninstall, remove the fonts from the .fonts folder (or rename it in case you want to  re-install in future) and then run the same terminal command.

---

### Post by bob brazie on 2010-02-03
Thank you so much for your time and help.

Bob.

---

