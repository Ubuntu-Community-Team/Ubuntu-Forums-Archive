---
title: "Change permissions using ubuntu trial"
date: 2014-03-30
forum: Installation &amp; Upgrades
---

### Post by ElXhury on 2014-03-30
Hi,

yesterday I started the process to upgrade my ubuntu 12.04 to 14.04. The laptop crashed in the middle of the process and now it is brain dead. I am trying to recover my information before doing a fresh install of ubuntu 13.10 or 14.04.

To recover the information I am using a USB with a copy of ubuntu 13.10, and using the option "try ubuntu". Goog news is that when I do that I can see all my information in the disk. Bad news is that I can not copy it to a new pen drive because it is from a different user and the user in the "try ubuntu" mode does not have permissions to do that.

How can I solve this? all I need is a backup of my information before I do a fresh install of ununtu.

Thanks!

---

### Post by Bashing-om on 2014-03-30
ElXhury; Hi !

"sudo" (Super User DO) in terminal should permit you to copy off your files.
```

sudo cp /mnt/work/<path>/<File_name> /mnt/usb/<path>

```
The liveMedium does not require a password.

Else one can also launch the text editor with the administrative previleges:
```

gksudo gedit

```
open a new window from the menu and drag and drop files .

[INDENT]should workie great
[/INDENT]

---

