---
title: "Doing an install over VNC"
date: 2023-06-27
forum: Installation &amp; Upgrades
---

### Post by steven43 on 2023-06-27
Is it possible to do an Ubuntu install over VNC?

Typically with other distributions I have used, this is accomplished by appending the grub entry for installing and adding [FONT=courier new]inst.vnc[/FONT] but that does not appear to be working with Ubuntu.

---

### Post by MAFoElffen on 2023-06-28
Sort of...

RedHat and it's derivatives use the Anaconda Installer which accepts the "inst.vnc" startup option to install via VNC. Ubiquity, Subiquity and Calamares are the installer types used by Ubuntu and it's flavors, which do not do that.

But it still can be done, just like if you were going to install via ssh... With that you interrupt it, install and configure openssh-server, find your IP, then connect to it remotely.

For VNC: What you have to do it be at the target machine when it starts, if Desktop Edition, use "Try", install and configure the VNC Server, then connect to it remotely via VNC. Connected to it remotely, you would then kick off the installer.

Slightly different process if you are doing the Server Edition, but same basic process. You would have to interupt the process to install both a desktop and VNC Server in the Live Image Environment for a remote VNC client to connect to.

So yes, it is possible, but not from a simple startup command.

---

