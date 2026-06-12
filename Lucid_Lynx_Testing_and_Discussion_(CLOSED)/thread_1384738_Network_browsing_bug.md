---
title: "Network browsing bug??"
date: 2010-01-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by chuckyp on 2010-01-18
Wondering if someone can confirm. I'm trying to browse my home windows network with lucid. After recent updates it prompts for a user/password just to browse the workgroup.  The workgroup doesn't have a password. I can however connect directly to window shares with the places > connect to server.

This is really weird behavior. Nothing has changed with my network so don't start offering suggestions. Its a problem with just this machine after recent updates.

---

### Post by sparker256 on 2010-01-18
> **chuckyp said:**
> Wondering if someone can confirm. I'm trying to browse my home windows network with lucid. After recent updates it prompts for a user/password just to browse the workgroup.  The workgroup doesn't have a password. I can however connect directly to window shares with the places > connect to server.

This is really weird behavior. Nothing has changed with my network so don't start offering suggestions. Its a problem with just this machine after recent updates.

See if this bug matches what you are seeing. If so add yourself as affected.

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/502607](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/502607)

Bill

---

### Post by cariboo on 2010-01-18
As a work around, as I mentioned in the [original]("http://ubuntuforums.org/showthread.php?t=1341141&highlight=Samba+problem") thread use:

```
smb://<servername>/<sharename>
```

and enter your password.

---

