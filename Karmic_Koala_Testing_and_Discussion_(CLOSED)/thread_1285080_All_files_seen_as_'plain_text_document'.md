---
title: "All files seen as 'plain text document'"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ubername on 2009-10-07
Since last updates all my files are recognised as plain text documents (odt, jpg, mpg, pdf etc.) If I select to 'open with' eg odt with OpenOffice, then all other files open with that too (which makes sense in a way)

Amy Clues?

TIA

---

### Post by VMC on 2009-10-07
[http://ubuntuforums.org/showthread.php?t=1284510](http://ubuntuforums.org/showthread.php?t=1284510)

---

### Post by cor2y on 2009-10-07
use this to fix it
```
update-mime-database.real -V ~/.local/share/mime/
```

---

### Post by howefield on 2009-10-07
Then reboot, or type in terminal

```
nautilus -q
```


From the same thread as noted above. Worked a treat for me.

---

### Post by ubername on 2009-10-07
Sorry, should have searched before posting. Thanks for replies.

---

### Post by emarkay on 2009-10-07
Suggest close thread and mark as "Solved".

---

