---
title: "How do I install an Nvidia Driver?"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by SoberWarlock on 2008-02-04
I just installed an Nvidia driver for my 8800GTS, but I can't get it to work. I open up the file called 

"NVIDIA-Linux-x86-169.09-pkg1.run" and I can't open it with terminal and I have no clue what to do. Need help. :confused:

---

### Post by justsomedude on 2008-02-04
What are the reasons you don't want to use the restricted drivers manager?

I could give instructions, but keep in mind you'd have to reinstall the driver every time there is a kernel update, so again, why don't you use the restricted drivers manager?

---

### Post by SoberWarlock on 2008-02-04
> **justsomedude said:**
> What are the reasons you don't want to use the restricted drivers manager?

I could give instructions, but keep in mind you'd have to reinstall the driver every time there is a kernel update, so again, why don't you use the restricted drivers manager?

Oh Ok I just enabled it and I had to restart my computer so now it feels more smooth, but is this the right driver? How can I tell that the restricted drivers manager did it's job? what can I type in terminal to find out?

---

### Post by justsomedude on 2008-02-04
> **SoberWarlock said:**
> Oh Ok I just enabled it and I had to restart my computer so now it feels more smooth, but is this the right driver? How can I tell that the restricted drivers manager did it's job? what can I type in terminal to find out?

If you open the restricted drivers manager again, it should now say "NVIDIA accelerated graphics driver In use".

You could also open a terminal and type

```
gedit /etc/X11/xorg.conf
```

Scroll down to *Section "Device"*. It sould say *Driver         "nvidia"* there. If it says *Driver         "nv"* or *Driver         "vesa"*, the driver is not in use.

Have fun, now you can enable flashy desktop effects and the like...

---

