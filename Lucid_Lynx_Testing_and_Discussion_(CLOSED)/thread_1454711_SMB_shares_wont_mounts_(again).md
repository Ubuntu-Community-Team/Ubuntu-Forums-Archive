---
title: "SMB shares wont mounts (again)"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gregh on 2010-04-15
After last nights upgrade samba shares will no longer mount. Fails with a DBUS error.
This problem was fixes about a few days ago but last nights updates have reverted to the same problem.

Anyone else? or any information I can provide to help?

---

### Post by SleepWalkerX on 2010-04-15
Do you manually mount them from the command line or are you talking about when you access a samba share through nautilus it won't automount the share?

---

### Post by gregh on 2010-04-15
Sorry, I should have provided more information.

It is either browsing via nautilus or using the nautilus "connect to server" feature.
I get the error:

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

-G

---

### Post by timosha on 2010-04-15
Same here.

---

### Post by scaine on 2010-04-15
My samba shares mounted using autofs are still working.  In fact, so is nautilus if I just issue "smb://myserver/mydata" in the location bar.

My shares are completely open.  Do you use username/password to connect?

Probably worth noting what the server is too.  In my case, I'm running Samba on an Ubuntu 9.10 server.

---

### Post by timosha on 2010-04-15
> **scaine said:**
> My samba shares mounted using autofs are still working.  In fact, so is nautilus if I just issue "smb://myserver/mydata" in the location bar.



Nope !
Error: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Please select another viewer and try again.

I use a username and password to connect, but I don't get there.

---

