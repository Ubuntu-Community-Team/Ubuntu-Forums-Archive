---
title: "gnome-power-manager applet disappeared"
date: 2009-06-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-06-27
What happened to gnome-power-manager applet? I don't have it in my panel!

If I start it from the console (after killing the existing process), I get these errors

```
(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Couldn't enumerate devices: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Couldn't enumerate devices: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Couldn't enumerate devices: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Couldn't enumerate devices: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Couldn't enumerate devices: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Couldn't enumerate devices: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Message did not receive a reply (timeout by message bus)
```

---

### Post by Vanishing on 2009-06-27
> **yelo3 said:**
> What happened to gnome-power-manager applet? I don't have it in my panel!

If I start it from the console (after killing the existing process), I get these errors

```
(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Couldn't enumerate devices: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Couldn't enumerate devices: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Couldn't enumerate devices: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Couldn't enumerate devices: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Couldn't enumerate devices: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Couldn't enumerate devices: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Message did not receive a reply (timeout by message bus)

(gnome-power-manager:11921): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Message did not receive a reply (timeout by message bus)
```

lastest upgrade broke some other things as well..
as in for your problem, you can either
-try to downgrade:
> devicekit-power
libdevkit-power-gobject1
gnome-power-manager

or
-wait for update..

---

