---
title: "Error: no versions of ndiswrapper found!"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by foolish one on 2007-10-12
what does that mean? I downloaded 2 different ndiswrappers and atttempted to manually install them, following the instructions on the INSTALL file. but every time there would be a command that the terminal doesn't recognize. And then the rest of the installtion process wouldn't work. 

then I trashed those and dowloaded a different version, for this one it installed straight from the GUI all I did was click on it. Though when I try to use it, it doesn' work and when I try to use it in the terminal it displays:

$ ndiswrapper -i mrv8335.inf 
Error: no versions of ndiswrapper found!

---

### Post by lixoo81 on 2007-10-13
I hit the same problem today. The solution is to install the ndiswrapper-utils package, as well as ndiswrapper-common.

```
sudo apt-get install ndiswrapper-utils-1.9
```

Hope that helps.

---

