---
title: "Windows and terminal messed up"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by Godspeed! mux on 2008-02-19
Hello all,

I have just installed Ubuntu on a desktop PC and everything seemed to go well. But, once logged in I noticed that windows do not have any decoration. There is no close button, they can not be resized or moved, and I can only close them by going to file->close.

I then tried to go into terminal but it appears as a white box and nothing else.

I have seen posts by people with similar problems in regards to beryl but I did not install beryl.

I am not all too experienced with Ubuntu and am not sure what to do. Any thoughts? :confused:

Thanks,
-Tim

---

### Post by Godspeed! mux on 2008-02-19
Fixed it!

I restarted, at GRUB went into recovery mode (text) and then wrote the following:

sudo nvidia-xonfig --add-argb-glx-visuals

This fixed the windows and the terminal.

Hope this helps someone.

-Tim

---

