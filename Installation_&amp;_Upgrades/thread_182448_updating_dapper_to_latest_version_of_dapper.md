---
title: "updating dapper to latest version of dapper"
date: 2006-05-26
forum: Installation &amp; Upgrades
---

### Post by horseradish on 2006-05-26
hi,

I upgraded to dapper a month ago. Do I automatically get updated to the newest version or do I have to use a command ? (and if so, what command ?)

Also, is it normal to have a lot of updates every day ? I seem to have daily updates of considerable size.

thanks.

---

### Post by Sef on 2006-05-26
> Do I automatically get updated to the newest version or do I have to use a command ?

When Dapper is released as stable on 1 June, there will be a button for you to click to update your system to Dapper.

---

### Post by horseradish on 2006-05-26
thank you very much. 

Just to clarify, I already have dapper, but Im not sure if I have the latest version ? does it automatically get updated to the latest version ?

In the meantime, is it normal to have quite large daily updates ? I have KDE installed as well.

---

### Post by Sef on 2006-05-26
If you have Dapper installed and have been installing the updates, you have the latest version.

> is it normal to have quite large daily updates ? 

Once Dapper is stable, the updates should slow up.

---

### Post by horseradish on 2006-05-26
thank you very much :)

---

### Post by louisgag on 2006-05-26
I run 

sudo apt-get update 

followed by

sudo apt-get dist-upgrade

but some packages (like arts and gdk-im) don't upgrade because I have to remove those manually, which I am doing right now to see what happens...

---

### Post by louisgag on 2006-05-26
ok, so after doing this:

libarts1c2 sera désinstallé
libpng10-0 sera désinstallé
libsmpeg0c2 sera désinstallé
libwxgtk2.4 sera désinstallé
arts (version 1.4.3-0ubuntu1) sera mis à niveau vers la version 1.5.2-0ubuntu1
gdk-imlib1 (version 1.9.14-16.2ubuntu4) sera mis à niveau vers la version 1.9.14-29ubuntu1
libopenal0 (version 0.2004090900-1.1build1) sera mis à niveau vers la version 0.2005080600-2.1build2
libarts1c2a (version 1.5.2-0ubuntu1) sera installé
libsmpeg0 (version 0.4.5+cvs20030824-1.7) sera installé


running dist-upgrade now tells me everything is updated (before it told me 3 packages had not been updated).

---

### Post by Sef on 2006-05-26
If you're in Dapper there is no need to run dist-upgrade.  Sometimes packages are held back and installed later.  This is seen with kernels a lot.

---

