---
title: "Still cannot disable menu icons"
date: 2009-12-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Robin Nixon on 2009-12-16
I noted that Ubuntu 9.10 removed the ability of the *System > Preferences > Appearance > Interface > Show icons in menus* check box to disable most icons. If you try it the feature will only disable a few icons in the System menu (and not its submenus), the Trash and a handful of others. By far the majority of icons cannot be removed, making the option useless.

I issued a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/465259](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/465259)

But it's still marked as *Undecided*.

If anyone else here wants this bug fixed could you please follow the above link and click *This bug affects me too*? Hopefully it will then get fixed in time for Lucid's release.

---

### Post by cszikszoy on 2009-12-16
This isn't really a bug.  Regardless of whether or not the setting to show icons in menus is set to true or false, GTK app developers are able to override it and specify that icons be shown.

---

### Post by Robin Nixon on 2009-12-16
I'm not talking about in programs but in the Applications, Places and System menus themselves.

The help page for this option states:[INDENT]**Show icons in menus**
[/INDENT][INDENT][INDENT] Select this option to display an icon beside items in application menus and the panel menu. Not all menu items have an icon.
[/INDENT][/INDENT]But even with the option unselected almost all icons still display.

---

### Post by cszikszoy on 2009-12-16
Right... but the applications / places / system menu is still a program!  And if you're seeing icons still it's very possible that they are purposely overriding that setting and displaying the icons regardless.

---

