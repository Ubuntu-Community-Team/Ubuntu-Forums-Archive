---
title: "problem in unraring a file"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2010-10-27
```
unrar x vol3.rar 
```gives

```

vol3.rar is not RAR archive
No files to extract

```
what should I check?

---

### Post by AndyCee on 2010-10-28
Try running:

```
file vol3.rar
```

that will tell you what the file actually is from the file header/magic number. If it says "data", the file is likely either corrupt or incomplete.

---

### Post by karthick87 on 2010-10-28
Your rar file may be corrupted.

---

### Post by Mark Phelps on 2010-10-28
I believe that you can also get that error message if the RAR is password-protected and you fail to supply the password when you try to expand it.

---

