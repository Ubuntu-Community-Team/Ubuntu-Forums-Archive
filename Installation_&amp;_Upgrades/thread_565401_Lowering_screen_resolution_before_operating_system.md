---
title: "Lowering screen resolution before operating system loads"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by jonjon1123 on 2007-10-02
I just installed Ubuntu server and got to the part of the Gnome desktop installation where you have to select screen resolutions.  I picked 1600 x 1200 because that is what my monitor supports.  I booted up the machine and now my monitor says it is not at the optimum resolution so it doesn't display anything, just that message.  I am assuming this is because my graphics card can't support that resolution (I am installing on a very old machine).  Is there are way I can lower or change the resolutions that I specified during installation without going through the process of completely reinstalling Ubuntu server and Gnome desktop again (it takes so long to do that)? 

Thanks,

-Jon-

---

### Post by renzokuken on 2007-10-02
get to a terminal screen (Ctrl+Alt+F1) then run

```
sudo dpkg-reconfigure xserver-xorg
```

just select lower resolutions at the appropriate point in the wizard

---

