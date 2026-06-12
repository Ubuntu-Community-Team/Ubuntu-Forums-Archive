---
title: "How to leave instructive text note on desktop of new installation"
date: 2019-12-12
forum: Installation &amp; Upgrades
---

### Post by gmulak on 2019-12-12
Is it possible to make a bootable installation CD or USB Stick that leaves an instructional note on the desktop after installation?  If so, how would I do that?  

Thank you!

---

### Post by yetimon_64 on 2019-12-12
From man useradd...
```
       -k, --skel SKEL_DIR
           The skeleton directory, which contains files and directories to be
           copied in the user's home directory, when the home directory is
           created by useradd.

           This option is only valid if the -m (or --create-home) option is
           specified.

           If this option is not set, the skeleton directory is defined by the
           SKEL variable in /etc/default/useradd or, by default, /etc/skel.

           If possible, the ACLs and extended attributes are copied.


```
Going by my reading of the above code block from man useradd I'd suggest you try adding a directory called Desktop to the /etc/skel directory of your installation cd/usb stick. Put your instructional text file inside /etc/skel/Desktop on the installer file system. When you do a new install the users Desktop should then contain the text file. A new desktop is generally empty from an initial installation so this should be safe to do.

Any directories and files in /etc/skel are owned by root but when the new account is created get changed to that of the new user. I'd add the Desktop directory and the file to /etc/skel as owned by root with permissions set to that as required by the user.

Note: I haven't tested this myself but after a bit of searching the subject this is how I'd try to do what you are asking for.

Best of luck with this, hope it works for you. Regards, yeti.

---

### Post by sudodus on 2019-12-12
One way to do it is create an [Ubuntu OEM drive](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview) (an installed system, which can be installed into a USB drive).

---

### Post by gmulak on 2019-12-13
Wow!  Thank you for hte help!  I appreciate it.

---

