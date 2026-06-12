---
title: "Update Manager issues"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by dobrowski on 2008-08-16
I am trying to run update manager and it fails telling me to run 

 dpkg --configure -a
dpkg: requested operation requires superuser privilege

I figured out from the forums that I need to type sudo in front.  That resulted in me getting this error. 

 parse error, in file `/var/lib/dpkg/updates/0039' near line 1:
 field name `,' must be followed by colon


I tried using the synaptic package manager to get rid of this file since i cannot delete or edit it directly, and that also did not work.  Does anyone have any advice?  Is it really important that I have the update manager working?

Thanks,
David

---

### Post by Diabolis on 2008-08-16
Post the content of the file:
```
cat /var/lib/dpkg/updates/0039
```

It is only missing a colon.

Or just remove it:
```
sudo rm /var/lib/dpkg/updates/0039
```

---

### Post by dobrowski on 2008-08-16
Thank you. 

Here is what it says. 

> , libgtk2-perl (>= 1.00), libgnome2-canvas-perl (>= 1.00), libgnome2-vfs-perl (>= 1.00)
Size: 329136
Description: Perl interface to the GNOME libraries
 libgnome2-perl allows allows to write programs with a GNOME user
 interface in Perl.
 .
 GNOME is a project to build a complete, user-friendly desktop based
 entirely on free software.
 .
 Find out more about GNOME at [http://www.gnome.org](http://www.gnome.org).
 .
 The perl bindings follow the C API very closely, and the C reference
 documentation should be considered the canonical source:
 [http://developer.gnome.org/doc/API/2.0/libgnome/index.html](http://developer.gnome.org/doc/API/2.0/libgnome/index.html)
 .
 This module is part of gtk2-perl.
 .
 To discuss gtk2-perl, ask questions and flamedavid@dell-laptop:~$ 



---

### Post by Diabolis on 2008-08-16
Actually it will be harder to edit the file because it is a binary. According to this [thread]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/35534") it will be easier to remove it.

---

