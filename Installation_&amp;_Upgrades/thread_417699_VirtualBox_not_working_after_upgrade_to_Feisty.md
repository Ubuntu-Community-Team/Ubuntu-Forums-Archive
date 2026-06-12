---
title: "VirtualBox not working after upgrade to Feisty"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by ansky on 2007-04-21
I just upgraded from Edgy to Feisty and now I can start up VirtualBox which was working great under Edgy.  I am now getting this error:

[INDENT]/dev/vboxdrv not writable for some reason. If you recently added the current
user to the vboxusers group then you have to logout and re-login to take the
change effect.[/INDENT]

The file /dev/vboxdrv does not exist.  Anything I can do short of reinstalling VirtualBox?

---

### Post by raja on 2007-04-21
Try ```
sudo /etc/init.d/vboxdrv setup
``` That should run the setup again.

---

### Post by ansky on 2007-04-21
Thanks but that seems to be missing too:

[INDENT]sudo: /etc/init.d/vboxdrv: command not found[/INDENT]

---

### Post by raja on 2007-04-21
If you cant do that I am afraid re-installing may the only thing to do.

---

### Post by serid on 2007-04-22
Hi,

I had the same problem - the vboxdrv module is gone. I needed to reinstall VirtualBox
(then it asks you whether you want to make a new vboxdrv modul for your kernel)
Just in case, rename your old .virtualbox folder to .virtualbox_old and then copy the content
to the new one. Additions were also gone so you will need to install them again.

Cheers,

Adrian

---

