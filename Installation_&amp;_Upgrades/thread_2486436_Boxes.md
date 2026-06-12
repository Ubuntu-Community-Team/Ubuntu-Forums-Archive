---
title: "Boxes"
date: 2023-04-30
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2023-04-30
I removed snap from Ubuntu 23.04.  Install gnome software instead and flatpak.  Now when I try to install Boxes it only offers the flathub version.  I need to know how to install non flathub version of Boxes.  Can anybody help me.

Henry

---

### Post by #&amp;thj^% on 2023-04-30
Try to ween yourself from GUI's
Try this:
```
sudo apt install boxes
```
example:
```
apt policy boxes
boxes:
  Installed: 2.2.0-2
  Candidate: 2.2.0-2
  Version table:
 *** 2.2.0-2 500
        500 https://mirrors.ustc.edu.cn/ubuntu mantic/universe amd64 Packages
        100 /var/lib/dpkg/status


```

---

### Post by Hewjr100 on 2023-04-30
Actually I do use the CLI alot, I just was under the assumption that with software app or terminal it would defer to install the Flatpak version.  Similar to firefox with snap.  Anyway all done and thanks.

Henry

---

### Post by deadflowr on 2023-04-30
In Software, underneath the Install button just click on the box that says flathub to toggle it to the deb version.

---

