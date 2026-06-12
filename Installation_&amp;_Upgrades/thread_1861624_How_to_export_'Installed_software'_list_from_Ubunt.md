---
title: "How to export 'Installed software' list from Ubuntu Soft. Center?"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by wi0 on 2011-10-15
Ubuntu software center (11.04 version) displays a clean list of installed software. I'd like to save that list. I've found ways to export lists of installed packages, but that's not what I want. The center list only includes actual programs like, say, Audacity which is what I want instead of the full listing of packages installed to resolve dependencies and what not.

The only thing I can think of right now is making screenshots, but that's not very efficient. Is there another way?

---

### Post by MAFoElffen on 2011-10-15
> **wi0 said:**
> Ubuntu software center (11.04 version) displays a clean list of installed software. I'd like to save that list. I've found ways to export lists of installed packages, but that's not what I want. The center list only includes actual programs like, say, Audacity which is what I want instead of the full listing of packages installed to resolve dependencies and what not.

The only thing I can think of right now is making screenshots, but that's not very efficient. Is there another way?
```

dpkg --get-selections > installed-software

```And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,

```

dpkg --set-selections < installed-software

```Followed by

```

dselect

```

---

### Post by wi0 on 2011-10-16
Thank you, but this is the exporting a list of installed packages I was referring to. It includes a lot more than the software center list.

---

