---
title: "upgrade to 12.10 broke compiz, unity won't start (nvidia)"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by kelt65 on 2012-10-22
For some reason, compiz refuses to start in 12.10. I have tried nvidia-current and nvidia-experimental-304 to no avail.

compiz claims the following:
[INDENT]```

compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Fatal: No composite extension
compiz (core) - Error: Plugin initScreen failed: composite
compiz (core) - Error: Failed to start plugin: composite
compiz (core) - Info: Unloading plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Error: Plugin 'composite' not loaded.

compiz (core) - Error: Plugin init failed: opengl
compiz (core) - Error: Failed to start plugin: opengl
compiz (core) - Info: Unloading plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'composite' not loaded.

compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Fatal: No composite extension
compiz (core) - Fatal: No composite extension
gnome-session[14127]: WARNING: Child process 14236 was already dead.
gnome-session[14127]: WARNING: Application 'compiz.desktop' killed by signal 11
gnome-session[14127]: WARNING: App 'compiz.desktop' respawning too quickly
gnome-session[14127]: CRITICAL: We failed, but the fail whale is dead. Sorry....
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
** Message: applet now removed from the notification area
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Fatal: No composite extension
compiz (core) - Error: Plugin initScreen failed: composite
compiz (core) - Error: Failed to start plugin: composite
compiz (core) - Info: Unloading plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).



```[/INDENT]

AFAIK the nvidia driver is functioning perfectly and providing 3D and direct rendering, according to nvidia-settings -> OpenGL/GLX information. There are no errors in the Xorg.0.log.

Then I find this in ```
/etc/X11/xorg.conf
```
```

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

How on earth did that get there? I changed to "Enable" and everything is fine now.

---

### Post by dwaltz on 2012-10-27
same problem here, with an Intel integrated HD 2000.
Your solution worked, thanks

---

