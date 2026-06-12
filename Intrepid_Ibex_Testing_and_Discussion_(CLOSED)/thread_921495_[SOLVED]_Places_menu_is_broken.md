---
title: "[SOLVED] Places menu is broken"
date: 2008-09-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Wise Ferret on 2008-09-16
After upgrading from Hardy, I get the following error trying to access my home folder from places menu:

Could not open location 'file:///home/username'
No application is registered as handling this file.

THe folder is of course there and is accessible through nautilus. This happens when trying to access the Desktop folder from nautilus as well.

I have tried running:
sudo update-desktop-database
sudo update-mime-database /usr/share/mime 
killall nautilus

But this did not work.

Looking in gconf->desktop->gnome->url-handlers, I see that there is indeed no directory for the "file" protocol. I would like to add this myself, but I didn't figure out a way to add a directory to gconf (I canot do this in gconf-editor, and did not find a way to do it with gconftool-2 either). So my question are:

1. Is there a way to conveniently fix this?
2. If not, how can I get my hands dirty and edit the gconf directory tree manually?

---

### Post by taavikko on 2008-09-16
```
sudo apt-get --reinstall install nautilus
```

---

### Post by Wise Ferret on 2008-09-16
> **taavikko said:**
> ```
sudo apt-get --reinstall install nautilus
```

Done that, and it did not help.

I ended up editing manually /etc/gconf/gconf.xml.defaults/%gconf.tree.xml and making it look like this:

<gconf>
<dir name="schemas">
  <dir name="apps">
  </dir>
</dir>
<dir name="apps">
</dir>
<dir name="desktop">
  <dir name="gnome">
    <dir name="url-handlers">
      <dir name="file">
      </dir>
    </dir>
  </dir>
</dir>
</gconf>

After saving this and restarting gnome I finally had gconf->desktop->gnome->url-handlers->file directory available in gconf-editor. Then I could add the needed keys and feel them with proper data (just copied the 3 keys from ->trash directory - they are is the same as the trash bin is also handeled by nautilus). Now everything works.

---

