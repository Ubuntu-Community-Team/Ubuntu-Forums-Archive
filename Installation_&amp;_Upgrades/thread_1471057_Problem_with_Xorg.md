---
title: "Problem with Xorg"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Naracuin on 2010-05-03
I've installed Ubuntu 10.04 yesterday on my Computer without any problems. Everything seemed to work just fine. 

However, then I tried to install World of Warcraft using Wine. I had no problems installing, but I couldn't start it afterwards, so I tried to configure my graphics card (Radeon HD 4850) and got an error message:

```
$ aticonfig --initial
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-2
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

```I tried sudo aticonfig --initial then and it seemed to work. But if I try to start WoW, I still get this error message:

```
$ wine .wine/drive_c/Program*/World*/Wow.exe -opengl
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  164
  Current serial number in output stream:  164

```Any ideas how I could solve this problem?

---

