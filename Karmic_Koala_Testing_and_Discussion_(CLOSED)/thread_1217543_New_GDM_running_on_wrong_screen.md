---
title: "New GDM running on wrong screen"
date: 2009-07-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mempf on 2009-07-19
I am running Karmic fully up to date and I have two monitors.

My primary monitor is on the right set up as 1280x1024. The other monitor is left of that and running at 1360x768.

I am using NVIDIA's twinview for multiple displays.

The problem is that the new GDM now loads up on my 1360x768 monitor which is often turned off or being used for other things.

Before GDM would appear only on the primary display leaving the other black until login.

Does anyone know of a current fix or of a bug report on this subject?

Thanks

---

### Post by Toe on 2009-07-19
This is probably the bug report you are looking for: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/396894](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/396894)

You could try moving the mouse to the active monitor quickly as soon as it appears when GDM is starting.
In my case mouse position affects the placement of the login window.

---

### Post by wayne_cat on 2009-07-19
Until gdm 2.22 there was an option to change the primary gdm screen.

From the gdm 2.20 documentation:

[http://library.gnome.org/admin/gdm/2.20/configuration.html.de](http://library.gnome.org/admin/gdm/2.20/configuration.html.de)


```
[greeter]
XineramScreen=0
```gdm 2.22 was a complete rewrite ... and they have dropped this option. gdm is a cripple now ...

---

### Post by mempf on 2009-07-19
> **Toe said:**
> This is probably the bug report you are looking for: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/396894](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/396894)

You could try moving the mouse to the active monitor quickly as soon as it appears when GDM is starting.
In my case mouse position affects the placement of the login window.

Yeah that's exactly the issue I'm having. The mouse effects where it goes. Now how do we get the mouse to start on the primary screen?

---

### Post by ktp on 2009-07-19
Do you have "video output 1" connect to your primary monitory?  I have noticed that if it is not then GDM would start on the monitor which was connected the video output 1.

---

