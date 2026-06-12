---
title: "how to install a .deb as a non-root user?"
date: 2020-05-21
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2020-05-21
i have a .*deb* that i want to install privately for one user (non-root, no sudo) so that it ends up in that user's home directory, with that user's ownership.  how is this to be done?

---

### Post by Perfect Storm on 2020-05-21
I would unpack it and take out the app itself and leave the rest.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=285949&stc=1&d=1590038727[/IMG]

---

### Post by Skaperen on 2020-05-21
how can i do that with commands?

---

### Post by Perfect Storm on 2020-05-21
extracting? 
```
ar -xv ****.deb
```

---

### Post by Skaperen on 2020-05-21
i learned something new and interesting today.  now my mind will go crazy over ways to analyze debs.  i wonder if i can even create them with ar.

---

