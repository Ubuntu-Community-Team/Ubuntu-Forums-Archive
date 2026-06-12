---
title: "I'm sure there must be a good reason for this but..."
date: 2009-05-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-05-12
why can't I browse all local and remote discs (Computer icon in tool-bar) from "gksu Nautilus" or as root?
Cheers, Mike

---

### Post by cariboo on 2009-05-12
I have the same behaviour, plus I can't use sftp as a normal user. Nautilus just disappears, even though there is a folder on the desktop, double clicking the folder makes it go away.

---

### Post by taavikko on 2009-05-12
I've got sftp mounted remote disc, trying to access it from
Places ends up in... nothing.

Did the nautilus upgrade modify
```
ls -l /usr/share/applications/nautilus*
-rw-r--r-- 1 root root 422 2009-05-11 22:54 /usr/share/applications/nautilus-autorun-software.desktop
-rw-r--r-- 1 root root 476 2009-05-11 22:54 /usr/share/applications/nautilus-browser.desktop
-rw-r--r-- 1 root root 459 2009-05-11 22:54 /usr/share/applications/nautilus-computer.desktop
-rw-r--r-- 1 root root 454 2009-05-11 22:54 /usr/share/applications/nautilus.desktop
-rw-r--r-- 1 root root 496 2009-05-11 22:54 /usr/share/applications/nautilus-file-management-properties.desktop
-rw-r--r-- 1 root root 474 2009-05-11 22:54 /usr/share/applications/nautilus-folder-handler.desktop
-rw-r--r-- 1 root root 371 2009-05-11 22:54 /usr/share/applications/nautilus-home.desktop
```

Icon in desktop access sftp-mount normally.

---

### Post by taavikko on 2009-05-12
Whops, spoken bit early, after last reboot.
```
[  185.329994] nautilus[4027]: segfault at 32 ip 00007f15d013a884 sp 00007fffdb528670 error 4 in libglib-2.0.so.0.2100.0[7f15d00e1000+c6000]
[  195.875760] nautilus[4278]: segfault at 0 ip 00007f4ec0eb7630 sp 00007fffcc290ed8 error 4 in libglib-2.0.so.0.2100.0[7f4ec0e4c000+c6000]

```

And mounts don't open.

Also, keyboard-layout went haywire
probably due to latest udev upgrade...

---

### Post by davideotape on 2009-05-12
My comuter icon doesn't like being opened now. It just doesn't do anything. Everything else seems to be working fine though. Is there a bugreport for this?

---

### Post by taavikko on 2009-05-12
> **davideotape said:**
> Is there a bugreport for this?

[https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/375253](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/375253)

---

### Post by mdurham on 2009-05-12
The replies above have nothing to do with my original post. Unfortunately the bug occurred at the same time that I posted my question, hence the confusion. Please see my original post, it has nothing to do with the current bug, it happens when Nautilus is running 'normally' without bugs.
Thanks, Mike

---

