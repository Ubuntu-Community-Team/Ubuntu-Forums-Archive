---
title: "Is Dropbox supported on Ubuntu 24.04"
date: 2024-06-06
forum: Installation &amp; Upgrades
---

### Post by stevecoh1 on 2024-06-06
Recently upgraded to 24.04 and I find the dropbox icon doesn't work.  Nothing happens when I press it.  sudo apt upgrade dropbox fails, says it doesn't know dropbox.  Yet the underlying functionality of dropbox still seems to work.  I wanted to get in there to see why Dropbox was asking me to upgrade since all my allowed device slots were used.  This required the application.  Couldn't get it done on Ubuntu, had to use my IPhone.

---

### Post by ActionParsnip on 2024-06-07
The package is nautilus-dropbox

[https://packages.ubuntu.com/search?keywords=dropbox&searchon=names&suite=noble&section=all](https://packages.ubuntu.com/search?keywords=dropbox&searchon=names&suite=noble&section=all)

So try:
```

sudo apt --reinstall install nautius-dropbox

```

May help. You could also uninstall the package, remove the config file for the application, then reinstall it to get vanilla settings. You can then apply your account info again

---

### Post by dhlocker on 2024-08-04
I was pleasantly surprised to discover that ActionParsnip's solution worked perfectly (after fixing the "nautius" typo.)

I had previously uninstalled, reinstalled from the dropbox packages ([https://linux.dropboxstatic.com/packages/ubuntu/nautilus-dropbox_2024.04.17_all.deb](https://linux.dropboxstatic.com/packages/ubuntu/nautilus-dropbox_2024.04.17_all.deb)) with no joy, and killed and restarted with several different options to no effect. The first installation dropped down a menu that was invisible; the second and third tries would do nothing when the icon was clicked; the **sudo apt --reinstall nautilus-dropbox** brought me back to the menu I've grown to know.

---

### Post by rbk5287 on 2024-08-30
> **dhlocker said:**
> I was pleasantly surprised to discover that ActionParsnip's solution worked perfectly (after fixing the "nautius" typo.)

I had previously uninstalled, reinstalled from the dropbox packages ([https://linux.dropboxstatic.com/packages/ubuntu/nautilus-dropbox_2024.04.17_all.deb](https://linux.dropboxstatic.com/packages/ubuntu/nautilus-dropbox_2024.04.17_all.deb)) with no joy, and killed and restarted with several different options to no effect. The first installation dropped down a menu that was invisible; the second and third tries would do nothing when the icon was clicked; the **sudo apt --reinstall nautilus-dropbox** brought me back to the menu I've grown to know.

That didn't work for me.  Here's a possible clue that appeared when I started Dropbox from a terminal:

(dropbox:13419): LIBDBUSMENU-GLIB-WARNING **: 13:08:07.370: About to Show called on an item wihtout submenus.  We're ignoring it.

---

