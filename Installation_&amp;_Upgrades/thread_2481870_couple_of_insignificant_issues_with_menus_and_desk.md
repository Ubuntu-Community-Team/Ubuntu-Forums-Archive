---
title: "couple of insignificant issues with menus and desktop icons after upgrading to 22.04"
date: 2022-12-11
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2022-12-11
After running do-release-upgrade from 18.04 to 20.04 and then to 22.04, I've noticed a couple of small issues with my menus and desktop icons. 

First, the desktop icons are permanently set to "auto arrange" and all three options there are greyed out. 

Also, I am unable to create or edit menu items using alacarte. When I click the [OK] button, it gives this error:

```
(alacarte:24174): Gtk-CRITICAL **: 18:52:01.059: gtk_accel_label_set_accel_closure: assertion 'gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(alacarte:24174): Gtk-CRITICAL **: 18:52:01.059: gtk_accel_label_set_accel_closure: assertion 'gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Traceback (most recent call last):
  File "/usr/share/alacarte/Alacarte/ItemEditor.py", line 186, in on_response
    self.save()
  File "/usr/share/alacarte/Alacarte/ItemEditor.py", line 176, in save
    util.fillKeyFile(self.keyfile, self.get_keyfile_edits())
  File "/usr/share/alacarte/Alacarte/ItemEditor.py", line 234, in get_keyfile_edits
    Icon=get_icon_string(self, self.builder.get_object('icon-image')),
  File "/usr/share/alacarte/Alacarte/ItemEditor.py", line 58, in get_icon_string
    filename = editor.icon_file
AttributeError: 'LauncherEditor' object has no attribute 'icon_file'
```

Same for the icons on the top panel. I am unable to edit those, either, but... I can delete those and add a new one using the [Panel Properties] dialog under the [Applets] tab. 

I don't know what else you might need but...

```
 $ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 22.04.1 LTS
Release: 22.04
Codename: jammy
```

```
 $ apt-cache policy alacarte
alacarte:
  Installed: 3.44.1-1
  Candidate: 3.44.1-1
  Version table:
 *** 3.44.1-1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe i386 Packages
        100 /var/lib/dpkg/status
```

```
 $ apt-cache policy gnome-flashback
gnome-flashback:
  Installed: 3.44.0-1ubuntu2
  Candidate: 3.44.0-1ubuntu2
  Version table:
 *** 3.44.0-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     3.44.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
```

Oh... and I use nemo as the filemanager, if that matters any:

```
 $ apt-cache policy nemo
nemo:
  Installed: 5.2.4-1
  Candidate: 5.2.4-1
  Version table:
 *** 5.2.4-1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
```


Any thoughts?

---

### Post by rebeltaz on 2022-12-18
bump... ?

---

### Post by rag2 on 2022-12-18
As noted at [https://ubuntuforums.org/showthread.php?t=2479979&p=14123578#post14123578](https://ubuntuforums.org/showthread.php?t=2479979&p=14123578#post14123578), others have had a similar problem when using GNOME Flashback. My solution was to use **menulibre** instead.

---

### Post by rebeltaz on 2022-12-18
> **rag2 said:**
> As noted at [https://ubuntuforums.org/showthread.php?t=2479979&p=14123578#post14123578](https://ubuntuforums.org/showthread.php?t=2479979&p=14123578#post14123578), others have had a similar problem when using GNOME Flashback. My solution was to use **menulibre** instead.

Ah. Thank you so much. I will give that a shot. I appreciate it and Merry Christmas!

---

### Post by ActionParsnip on 2022-12-21
[https://bugs.mageia.org/show_bug.cgi?id=12153](https://bugs.mageia.org/show_bug.cgi?id=12153)

---

