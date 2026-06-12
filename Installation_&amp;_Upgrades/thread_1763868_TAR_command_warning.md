---
title: "TAR command warning"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by oweri on 2011-05-20
May I know what is wrong in the following TAR command?
It works, but generate a warning...

> tar -cpzvf  /etc/a000/backup.tar.gz  /etc/r000
tar: Removing leading `/' from member names

---

### Post by Telengard C64 on 2011-05-21
> **oweri said:**
> May I know what is wrong in the following TAR command?
It works, but generate a warning...

> tar -cpzvf  /etc/a000/backup.tar.gz  /etc/r000
tar: Removing leading `/' from member names

I don't see anything wrong with the command. That warning is just that, a *warning*. The **/** prefix is not recorded in your archive, I think to avoid possible trouble later.

That's okay, because you should change the working directory prior to extracting anyway. If you really, *really* want your archived files extracted in the root folder, then **cd /** before you **tar -xzvf**.

HTH

---

### Post by matt_symes on 2011-05-21
Hi

> **oweri said:**
> May I know what is wrong in the following TAR command?
It works, but generate a warning...

> tar -cpzvf  /etc/a000/backup.tar.gz  /etc/r000
tar: Removing leading `/' from member names

This is no issue at all. It is removing the / to create a relative path in the archive and not an absolute path. That way when you unpack the archive it will appear under your current working directory and not under the root directory /.

This is generally what you want and it is also safer as you are less lightly to overwrite important files.

If you want to get rid of the warning you can use the -C flag to change to the root directory.

tar -cpvf /etc/a000/backup.tar.gz  -C / /etc/r000

IIRC, That should get rid of it.

Kind regards

---

