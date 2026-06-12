---
title: "Aoache Folder Permissions"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by daystar on 2005-04-16
Hi,

I just installed apache on my ubuntu box but I cant write to the document root as its permissions are set to allow only root to write to it. Obviously having to store my files in my home dir while I edit them, then copy them to the document root through sudo is a hassle compared to just editting them directly out of the document root. But the only way I can do this is to chmod the document root to 777 to give myself access, which can't be good security as anyone can edit it.

How does everyone deal with their document roots, am I missing something obvious?

Thanks guys.

---

### Post by hagman on 2005-04-16
Hi,

You can change the ownership of your document root to root:<your_user_group> and access to 0770. So changes can only made by your group members, not by anyone else.

Cheers,

Helge

---

### Post by mesocool on 2005-04-16
Can you be more specific? For example a line of command.. :razz:

---

