---
title: "Menu-&gt;Applications is lost due to update"
date: 2009-07-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-07-15
gnome-menus 2.27.4-0ubuntu1

Like the title says, anyone else seeing this?
Clicking the entry will only highlight it, but wont open.

gnome-menus.preinst states that its removing old conffiles.
So /etx/xdg/menus/gnome-applications is been removed...

```
gnome-menus (2.27.4-0ubuntu1) karmic; urgency=low

  * New upstream version:
    libmenu
    - Improve performance by using a cache to not compute the same thing
      again and again
    - Add API to access GenericName
    - Fix DefaultLayout attributes not being inherited
    - Do not always inherit parent DefaultLayout attributes
    - Sort inlined items unless inline_header is used
    Menu Editor
    - Add --help and --version arguments
    - Port to GtkBuilder
    Misc
    - Use shave to improve build log readability
  * debian/control.in:
    - don't require glade
  * debian/gnome-menus.install:
    - updated for the changes in the new version
  * debian/libgnome-menu2.shlibs:
    - new version update
  * debian/patches/12_merge_duplicates.patch,
    debian/patches/12_submenus_inherit.patch:
    - the change is in the new version
  * debian/patches/20_show-admin-tools-for-admin-group.patch:
    - new upstream version
```

---

### Post by Regenweald on 2009-07-15
I restarted the machine, try restarting the session. Fine now.

---

### Post by Toe on 2009-07-15
You don't even have to restart your session.
A simple "sudo killall gnome-panel" will suffice.

---

### Post by jfernyhough on 2009-07-15
I don't think you need to use sudo...

$ killall gnome-panel

would do.

---

### Post by wayne_cat on 2009-07-15
> **jfernyhough said:**
> I don't think you need to use sudo...

$ killall gnome-panel

would do.

right ...  the gnome-panel process belongs to your user

```
rschmitt@macbook:/$ ps -ef|grep gnome-panel |grep -v grep
rschmitt  4166  4102  0 Jul15 tty1     00:00:19 gnome-panel
rschmitt@macbook:/$ 
```

---

### Post by buzzmandt on 2009-07-15
It also works just to log off and back in again

---

### Post by taavikko on 2009-07-16
Hmm. didn't like this feature...
One has to restart session to reap the benefits of an update...
reminds me little too much of something else...

Problem solved, was just a tad too hazy to suspect a bug :)

---

### Post by durand on 2009-07-16
> **jfernyhough said:**
> I don't think you need to use sudo...

$ killall gnome-panel

would do.

Thanks!

---

