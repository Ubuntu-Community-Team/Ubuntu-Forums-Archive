---
title: "problem with tar"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by gtown50112 on 2008-01-13
i noticed that i couldn't install any updates, which let me to check tar.  unfortunately when i type *tar -v* i get 
$ tar -v
bash: tar: command not found

any thoughts on how to proceed? thanks!

---

### Post by gander on 2008-01-13
Good Evening...What exactly are you trying to do with tar.  "tar' is used to
extract files from an archive or as it's better known a "tarball".  Is that what you
want to do?....gander

---

### Post by jaakan on 2008-01-13
is tar still in /bin?

---

### Post by Partyboi2 on 2008-01-13
huh?
If you are not getting updates make sure that you have the first 2 ticked under "Software Sources" (System>Admin>Software Sources)
under the "Update Tab"

---

### Post by gtown50112 on 2008-01-13
Thanks for the replies.  I know that tar is used to unpack tarballs.  The problem that I am having is that in order to install the software updates that I download I need to be able to untar them.  Unfortunately I can't use tar for some reason.  The latest versions of tar on the gnu mirrors seem to be in tarballs... which is frustrating.

I am getting updates... they just fail on install.

---

### Post by Partyboi2 on 2008-01-13
is tar installed?
```
 tar --version
```

---

