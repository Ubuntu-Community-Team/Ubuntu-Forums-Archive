---
title: "gnome-panel: undefined symbol: gtk_widget_get_realized"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zakmakattak on 2010-04-27
Hi all,

Just updated from karmic to lucid release candidate, and everything went fine during the installation, but when I tried to boot, gnome-panel failed to load, and there are no desktop icons.  I can access terminal via ctrl-alt-t, and I tried:

```
gnome-panel
```

but it gave me the following error:

gnome-panel: symbol lookup error: gnome-panel: undefined symbol: gtk_widget_get_realized

Thanks in advance

---

### Post by dino99 on 2010-04-27
try to remove/purge plymouth, then reconfigure gnome-panel, and reinstall plymouth

---

### Post by zakmakattak on 2010-04-27
when I try to get rid of plymouth, I get:

> The following packages have unmet dependencies:
libwagon-java: Depends: libmaven-scm-java but it is not going to be installed
E: Broken packages

I checked, and I do have both packages in question, up to date.

---

### Post by dino99 on 2010-04-27
try: sudo dpkg --configure -a

---

### Post by zakmakattak on 2010-04-27
No dice, still get the same thing.

---

### Post by zakmakattak on 2010-04-27
*bump*

---

