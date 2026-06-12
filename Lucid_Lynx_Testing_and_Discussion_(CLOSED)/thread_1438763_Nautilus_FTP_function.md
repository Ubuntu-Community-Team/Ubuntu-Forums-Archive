---
title: "Nautilus FTP function"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jandante on 2010-03-25
I can't connect to a FTP Server anymore in Lucid Lynx (latest updates installed).

When I start a new connection I never get the screen for the password. And when I start a stored connection (bookmark) nautilus crashes...

Anyone who has this problem or shoud I do a reinstall?

Got an error some time later when trying to make a new connection:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by KB1JWQ on 2010-03-25
Hmm, does this apply to all FTP servers, or just one?

Can you still hit it through the ftp CLI cilent?

---

### Post by KB1JWQ on 2010-03-25
Update: Just tested it on my Lucid box here-- connected to an FTP server with no issues.

---

### Post by Framli on 2010-03-25
> And when I start a stored connection (bookmark) nautilus crashes...
I get this too at times. It seems to happen when Nautilus tries to get the password from the keyring.

[https://bugs.launchpad.net/ubuntu/lucid/+source/gvfs/+bug/538764](https://bugs.launchpad.net/ubuntu/lucid/+source/gvfs/+bug/538764)

---

### Post by jandante on 2010-03-25
> **KB1JWQ said:**
> Hmm, does this apply to all FTP servers, or just one?

Can you still hit it through the ftp CLI cilent?

I can through Filezilla but I don't know how to use the Command line client,

i will so a reinstall and will come back on this!

After a new install everything (even my usb network dongle (WUSB100)) worked perfect.

---

