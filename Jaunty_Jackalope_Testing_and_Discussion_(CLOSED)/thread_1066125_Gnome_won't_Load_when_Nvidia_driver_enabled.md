---
title: "Gnome won't Load when Nvidia driver enabled??"
date: 2009-02-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by damispyderbyte on 2009-02-10
Hey i'm confused, 
ok I went sudo apt-get install nvidia-glx-180 and installed the nvidia drivers there. Then I dropped to terminal, disabled gnome display thing (sorry can't think of whats it called). I then had nvidia auto configure my x.org file. (nvidia-xconfig). I restarted gnome display thing and it loaded the logon screen fine. I logged in and it showed my background, but no menu bars and the only command I that would work is ctrl-alt-F1. I Then reversed the changes and started the gnome display manager again. I logged on and it worked, but no 3D accel. So its almost like the gnome panels wont load?
This is a weird problem, anyone have any ideas? Thanks!!

Sys specs: Core 2 Duo T7500 2.2
           Nvidia M8600GT
           Asus G1S-A1
           Ubuntu Jaunty Alpha 4
Thx again!!

---

### Post by minisori on 2009-02-10
What version of xserver-xorg-core do you have? You should install the latest one: version 1.5....-0ubuntu5.

---

### Post by damispyderbyte on 2009-02-10
k, its 1.6 and for some reason now it worked, its weird all i did is restarted at again...
ubuntu u work in some mysterious ways. 
Thanks, and how do i mark this thread as solved??

---

### Post by minisori on 2009-02-10
1,6 ? Oo

Just edit the first post and put a [solved] at the beginning of the title :)

---

### Post by Triggerhapp on 2009-02-10
Probably the kernel modules, which I think are created on boot when you boot into a kernel that doesnt already have them... May be mistaken,

---

