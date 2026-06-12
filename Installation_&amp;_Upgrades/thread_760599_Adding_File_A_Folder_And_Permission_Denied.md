---
title: "Adding File A Folder And Permission Denied"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by ALPER on 2008-04-20
I have installed Stardict and i wanted to add dictionary to /usr/share. But &#305; couldn't. "Permission denied" shown in console.

---

### Post by vanadium on 2008-04-20
This question belongs to the "Absolute beginners" forum. You need administrator rights to copy files into /usr/share.

---

### Post by ALPER on 2008-04-20
I also has root password.

---

### Post by vanadium on 2008-04-20
You can execute a command with root permissions when you preceed it with "sudo", e.g.

sudo cp -i myfile /usr/share

You can also launch a file explorer (nautilus) with root permissions:

gksudo nautilus

Close this instance of nautlilus as soon as you are done, because you could break your system when you make a mistake.

---

### Post by ALPER on 2008-04-21
thank you for your help,vanadium 

nautilus helps me. Perfectly!

---

