---
title: "Can't install .deb packages.  &quot;Bad file descriptor&quot;"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mike_IronFist on 2009-10-02
I'm trying to install stuff like Skype, the latest Virtualbox, etc. No matter what .deb file I open, the install fails and the terminal section of the installer window opens and it reads:
```
dpkg: unable to read filedescriptor flags for <package status and package descriptor>: Bad file descriptor
```

How can I fix this?

**EDIT:** This bug has already been found and will be fixed in the next major milestone release or update for Karmic. Until then, users can fix this issue by using the command line to install .deb packages. For example:

```
dpkg -i packagename.deb
```

In this example, you would replace packagename with the name of the .deb file you're installing, obviously.

---

### Post by Funnnny on 2009-10-02
Yep, the only way to install deb file (for now )is using dkpg -i <filename>

---

### Post by chriskin on 2009-10-02
> **Mike_IronFist said:**
> I'm trying to install stuff like Skype, the latest Virtualbox, etc. No matter what .deb file I open, the install fails and the terminal section of the installer window opens and it reads:
```
dpkg: unable to read filedescriptor flags for <package status and package descriptor>: Bad file descriptor
```

How can I fix this?

**EDIT:** This bug has already been found and will be fixed in the next major milestone release or update for Karmic. Until then, users can fix this issue by using the command line to install .deb packages. For example:

```
dpkg -i packagename.deb
```

In this example, you would replace packagename with the name of the .deb file you're installing, obviously.

thanks for the solution on this one :)

---

