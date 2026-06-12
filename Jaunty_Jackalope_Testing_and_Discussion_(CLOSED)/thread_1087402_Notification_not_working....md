---
title: "Notification not working..."
date: 2009-03-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2009-03-05
I seem to have an issue with the new notification tool.  It won't display the volume or brightness keys along with who knows what.  Not a black box, nothing.  Also, I don't seem to have the pop-up applet available this time around...

---

### Post by Kazade on 2009-03-05
I have a similar problem... I *did* have the new notifications for volume and brightness, but now they have returned to the old-style notifications, yet I still get the new-notifications from pidgin and network-manager

---

### Post by mariner09 on 2009-03-05
Right, NM, crashes, they all appear.  I don't even get the old-style pop-ups for brightness and volume.

---

### Post by dalonso on 2009-03-05
For the moment, in order the new notification system work you need to be using the standard ubuntu icon set. Could it be because of this that it is not working for you?

---

### Post by mariner09 on 2009-03-07
Apparently that was it.  I thought it was working with the breathe icon set prior to Alpha 5, but I could be mistaken...

---

### Post by Darkshade on 2009-03-07
You can always use
```
sudo cp /usr/share/icons/Human/scalable/status/notification-* /PATH-TO-YOUR-ICONSET/scalable/status/
```
and then
```
killall -15 notify-osd
```
in order to see the notification with an iconset different than human.

Or even better, use
```
sudo cp /usr/share/icons/Human/scalable/status/notification-* /usr/share/icons/gnome/scalable/status/
```
instead of the first one, in order to make the notifications appear even if you decide to change your theme (saves you the trouble of copying them again to your new theme).

---

### Post by KhaaL on 2009-03-09
> **Darkshade said:**
> You can always use
```
sudo cp /usr/share/icons/Human/scalable/status/notification-* /PATH-TO-YOUR-ICONSET/scalable/status/
```
and then
```
killall -15 notify-osd
```
in order to see the notification with an iconset different than human.

Or even better, use
```
sudo cp /usr/share/icons/Human/scalable/status/notification-* /usr/share/icons/gnome/scalable/status/
```
instead of the first one, in order to make the notifications appear even if you decide to change your theme (saves you the trouble of copying them again to your new theme).

Thanks, that fixed it for me. I saw that this was [reported as a bug]("https://bugs.launchpad.net/notify-osd/+bug/331383") too

---

### Post by chrisccoulson on 2009-03-09
The correct fix is to rename /usr/share/nofity_osd to /usr/share/notify-osd. See [https://bugs.edge.launchpad.net/ubuntu/+source/notify-osd/+bug/338837]("https://bugs.edge.launchpad.net/ubuntu/+source/notify-osd/+bug/338837")

---

### Post by mariner09 on 2009-03-10
There was no nofity_osd folder on my system.  It was correct with notify_osd...

---

