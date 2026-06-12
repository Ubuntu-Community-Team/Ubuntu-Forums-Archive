---
title: "Lost Gimp on upgrade"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by worxguy on 2010-01-28
I recently upgraded to koala, but gimp no longer functioned after upgrade; i.e. open file popup dialogue freezes, crop tool is non-functional, preferences dialogue was absolutely a blank box. Tried un-install/re-install thru both the new software center and synaptic. Same broken result every time. Tried a direct download from gimp.org but ran into a lot of dependency stuff I know nothing about; I'm an end user, not a coder. So, how do I get a functioning install of gimp?
thanks,
worxguy

---

### Post by llawwehttam on 2010-01-28
Try opening terminal and typing:

```
sudo apt-get purge gimp ; sudo apt-get install gimp
```

---

### Post by worxguy on 2010-01-28
Thanks for your quick response. But, I ended up with the same broken installation after running those commands.

---

### Post by worxguy on 2010-01-28
Got a new clue:
The darned thing runs great if invoked with this command:
gksudo gimp

This does, however, generate a couple of warnings:

(file-uri:15160): GLib-WARNING **: g_set_prgname() called multiple times
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

(file-jpeg:15345): GLib-WARNING **: g_set_prgname() called multiple times

And, of course, I'm clueless on that.

thanks,
worxguy

---

