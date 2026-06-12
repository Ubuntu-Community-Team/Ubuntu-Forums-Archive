---
title: "Can't install Matlab from ISO"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by sleepfuriously on 2013-09-09
Hello,

I have a Matlab R2013a disk image that I mounted using Furius ISO Mount (mount point: /home/andrew/Matlab801_MacUnix_iso). I ran the command

```
sudo /home/andrew/Matlab801_MacUnix_iso/install -v
```

but I get "command not found." I also tried the method listed here <https://help.ubuntu.com/community/RootSudo> for dragging the install file into the terminal.

```
gksudo "gnome-open %u"
```

This started the installation process successfully, but when I tried to create a destination folder for Matlab I got the message "Unable to create destination folder /usr/local/MATLAB/R2013a". I thought this would have been fixed by running as sudo, but apparently not?

Thanks in advance.

---

### Post by 2011uet on 2014-04-03
Solution is very simple open terminal and drag install_linux on it every thing will be done automatically:P

---

