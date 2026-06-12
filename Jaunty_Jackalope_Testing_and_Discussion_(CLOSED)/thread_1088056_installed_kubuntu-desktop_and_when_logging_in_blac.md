---
title: "installed kubuntu-desktop and when logging in black screen"
date: 2009-03-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2009-03-05
i have been wanting to try kde 4.2 so i installed the kubuntu-desktop and when i tried to login to it i am just getting a black screen with a mouse cursor that is it.

does anyone have any ideas 

thanks

---

### Post by ajgreeny on 2009-03-05
Does your gnome desktop work OK, or do you mean this is a new install of kubuntu without ubuntu and its gnome desktop underneath?

---

### Post by caryb on 2009-03-05
I have seen this with Intel & Nvidia graphics cards, change your /etc/Xll/xorg.conf to say vesa & reboot.

> Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"   **-----> change this to vesa with the "" inplace**
    VendorName     "NVIDIA Corporation"
EndSection


Cary

---

