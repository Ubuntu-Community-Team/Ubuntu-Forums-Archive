---
title: "New install of 24.04 now wireless trackball stops after 5 seconds"
date: 2024-08-20
forum: Installation &amp; Upgrades
---

### Post by markuswells on 2024-08-20
Hi Everyone,
I have been using this trackball (Wireless, not Bluetooth) since 14.04 and its been fine.
Now I do a fresh install, of 24.04 desktop, on a blank hard drive. Everything seems fine, but when I log in I can move the mouse for a few seconds then it stops.
I CAN plug in a wired USB mouse and its fine.

I have no idea how to even begin debugging this (dmesg or ?)
Any help would be greatly appreciated

Markus

---

### Post by him610 on 2024-08-20
First step when seeking help is to provide some information about your system and your mouse.
```
inxi -Fxxz && xinput

```
Please place results within code tags.

---

### Post by markuswells on 2024-08-20
Thank you for your help with this.

I did find comments about "--reinstall inputattach" and it seemed close to the issue I was having.

Cubby posted the fix here [https://superuser.com/questions/72112/mouse-clicks-suddenly-stopped-working-in-ubuntu/239150#239150]("https://superuser.com/questions/72112/mouse-clicks-suddenly-stopped-working-in-ubuntu/239150#239150")

It did not fix the issue right away, but after I left the system off over night it did resolve everything.
NO other changes were made. Be patient.

Markus

---

