---
title: "can't start gdm of fresh install"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by bb4r on 2007-03-05
Looks like I'm missing some important files, but I have no idea how to get them.

```
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/media:/tmp/.ICE-unix/4690
/bin/sh: /usr/bin/esd: not found

** (gnome-session:4690): WARNING **: Could not start esd: Failed to execute child process "/usr/bin/esd" (No such file or directory)


** (gnome-session:4690): WARNING **: Esound failed to start.

I/O warning : failed to load external entity "/home/steveo/.config/openbox/rc.xml"
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
I/O warning : failed to load external entity "/home/steveo/.config/openbox/debian-menu.xml"
I/O warning : failed to load external entity "/etc/xdg/openbox/debian-menu.xml"
(/usr/bin/openbox:4758): ObParser-WARNING **: unable to find a valid menu file 'debian-menu.xml'
I/O warning : failed to load external entity "/home/steveo/.config/openbox/menu.xml"
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

```

---

### Post by bb4r on 2007-03-06
Tried to remove gdm and reinstall, but that didn't seem change anything.  Any thoughts?

---

