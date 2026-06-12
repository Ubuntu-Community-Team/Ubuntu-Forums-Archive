---
title: "Upgrade from cd image or update manager"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Corvair on 2009-12-30
Could someone please clear this up for me.

I want to upgrade from 9.04 to 9.10

With an Image cd do I have to do a clean install or can I simply upgrade without loosing all my files? 

Or do I have to use upgrade manager in order to conserve all my personal stuff?

Thank you in advance,

Corvair

---

### Post by dstew on 2009-12-30
You can't upgrade using a Live CD, but you can using an [Alternate Install CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"). If you burn an Alternate Install CD, put it in, navigate to its root directory (usually /media/cdrom) and run the upgrade script```
./cdromupgrade
```Running```
./cdromupgrade --help
```will give some details on the process. See the [Upgrading Ubuntu community document]("https://help.ubuntu.com/community/Upgrades"). On that document are also instructions for upgrading from a downloaded Alternate Install .iso without burning it to disk. Good luck, and best wishes.

---

### Post by Corvair on 2009-12-30
Thank you for your reply.

---

