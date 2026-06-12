---
title: "Default VS Server installation"
date: 2006-04-24
forum: Installation &amp; Upgrades
---

### Post by _Chris_ on 2006-04-24
I'm going to install Ubuntu 5.10 to support VMware virtualization software (which requires a server OS).  I'm wondering if the standard installation includes all of the Server components, or all but the Server components.  Additionally, does anyone know if the Server installation includes a GUI?  Thanks in advance!
Chris

---

### Post by aysiu on 2006-04-24
Server does not include a GUI, but you can easily add a GUI by installing server and then type ```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---

### Post by _Chris_ on 2006-04-24
Thanks for the info.  I'm still wondering if the standard installation includes server components.

---

### Post by Sef on 2006-04-24
From what I understand, the only difference between a server install and a standard install is that the standard install has a window manager, while the server has a command line to start with.

---

### Post by _Chris_ on 2006-04-24
OK, thanks for your help!  I think I'll just get on with the installation.  No guts no glory, right?
Chris

---

