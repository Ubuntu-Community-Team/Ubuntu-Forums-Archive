---
title: "VirtualBox 3 with Alpha 3 for 3D desktop effects?"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2009-07-24
I'm running alpha 3 in vbox 3.0.2 and was able to get the additions (Xorg mouse and video) installed for better mouse integration and higher screen resolution.

But does anyone know how to get compiz desktop effects to work?

I've tried putting SKIP_CHECKS=yes to the ~/.config/compiz/compiz-manager file but get a white screen upon attempting to enable normal effects.

---

### Post by aamukahvi on 2009-07-24
> **vishalrao said:**
> I'm running alpha 3 in vbox 3.0.2 and was able to get the additions (Xorg mouse and video) installed for better mouse integration and higher screen resolution.

But does anyone know how to get compiz desktop effects to work?

I've tried putting SKIP_CHECKS=yes to the ~/.config/compiz/compiz-manager file but get a white screen upon attempting to enable normal effects.
I didn't need to do anything, it just works. Try upping your video memory in host settings and enable 3D acceleration?

---

### Post by vishalrao on 2009-07-24
yup, did those already, im running vbox on arch linux with nvidia, are you on vbox/windows?

---

### Post by aamukahvi on 2009-07-24
> **vishalrao said:**
> yup, did those already, im running vbox on arch linux with nvidia, are you on vbox/windows?
Nope, host is Jaunty64 and guest is Karmic32. I don't think the host distro matters, though. As long as your host has 3D acceleration, it should work in the guest too.

---

