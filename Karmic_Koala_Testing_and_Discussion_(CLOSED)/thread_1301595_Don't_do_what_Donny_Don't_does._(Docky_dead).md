---
title: "Don't do what Donny Don't does. (Docky dead)"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dro0g on 2009-10-26
As of this morning's updates I'm no longer able to launch gnome-do. If I try to run it, a process called 'cli' which seems to be part mono grabs 100% CPU and gnome-do never launches. (as an aside, naming a Microsoft related programing language after a disease seems about right)

gnome-do --debug doesn't return anything.

Anyone else seeing problems with gnome-do/docky?

---

### Post by Lieter on 2009-10-26
Nope, do works for me

Running latest updates 
gnome-do: Version: 0.8.2+dfsg-1
mono-runtime:Version: 2.4.2.3+dfsg-2

---

### Post by nutmac on 2009-10-26
Mine stopped working also, with the following error (similar to [bug 460808](https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/460808)):

$ gnome-do
Stack overflow in unmanaged: IP: 0x7f7d03a400ac, fault addr: 0x7ffff349dff8
Stack overflow in unmanaged: IP: 0x498ea4, fault addr: 0x7ffff349be50
Stack overflow in unmanaged: IP: 0x545e33, fault addr: 0x7ffff349cdf8
Stack overflow in unmanaged: IP: 0x498ea4, fault addr: 0x7ffff349b680
Stack overflow in unmanaged: IP: 0x545e33, fault addr: 0x7ffff349be38
Stack overflow in unmanaged: IP: 0x545e33, fault addr: 0x7ffff349ae78
Stack overflow in unmanaged: IP: 0x545e33, fault addr: 0x7ffff3499eb8
Stack overflow in unmanaged: IP: 0x586da4, fault addr: 0x7ffff3498b30
Stack overflow in unmanaged: IP: 0x586da4, fault addr: 0x7ffff3497d90
Stack overflow in unmanaged: IP: 0x586da4, fault addr: 0x7ffff3496ff0
Stack overflow: IP: 0x586da4, fault addr: 0x7ffff3495b80
At Unmanaged

---

