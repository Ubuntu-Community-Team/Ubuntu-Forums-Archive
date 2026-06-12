---
title: "Boot stops at Ubuntu + five dots"
date: 2013-01-09
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2013-01-09
What causes a boot to stop at Ubuntu 12.04 with the five dots?  If I then do Ctrl-Alt-F1, it takes me to a login.  I log in and then run sudo lightdm.  Thet brings me to the correct graphical login for Ubuntu, Ubuntu-2d.  After that login, system runs normally.

I got into this "mess" after I removed the Gnome desktop.

Is there a diagnostic tool that will point out the error in my ways?

John

---

### Post by oldfred on 2013-01-11
Have you looked into log files?

Try Log File Viewer and look at dmesg. Then look for errors, repeated tries at loading a driver, or long times between entries.

---

### Post by dannyboy79 on 2013-01-11
you could try to reconfigure lightdm with
```
sudo dpkg-reconfigure lightdm
```

also make sure that lightdm is within the file /etc/x11/default-display-manager

---

### Post by cigtoxdoc on 2013-01-11
Thank you for your help.  dmesg indicates "13.417424] nvidia: module license 'NVIDIA' taints kernel." even after new nVidia driver installed (NVIDIA UNIX x86 Kernel Module  173.14.36) using procedure specified by nVidia.  Once I do the alternate boot procedure as indicated in my question, video situtation is excellent.  I have also reconfigured lightdm.

John

---

### Post by dannyboy79 on 2013-01-14
> **cigtoxdoc said:**
> Thank you for your help.  dmesg indicates "13.417424] nvidia: module license 'NVIDIA' taints kernel." even after new nVidia driver installed (NVIDIA UNIX x86 Kernel Module  173.14.36) using procedure specified by nVidia.  Once I do the alternate boot procedure as indicated in my question, video situtation is excellent.  I have also reconfigured lightdm.

Johnso everything is fixed? please mark it solved using the thread tools in the upper right. thanks

---

