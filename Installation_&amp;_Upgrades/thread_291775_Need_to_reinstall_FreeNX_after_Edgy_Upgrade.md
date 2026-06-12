---
title: "Need to reinstall FreeNX after Edgy Upgrade"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by acegolfer on 2006-11-02
It took about 5 hours to upgrade from Dapper to Edgy. Slow downloading speed even with T1 connection. I managed to get everything back in order. Here's what I did.

1. I had to reinstall FreeNX using Dapper repository.
2. Removed apache2 and reinstalled apache2. Couldn't upgrade without removing first.
3. Some dynamic links were gone in /var/www directory. 
4. I saw some bug reporting tool error messages but they seem to be gone after rebooting.

So far, so good. I was anxious at the beginning but after all, I'm a happy camper.

---

### Post by garretwp on 2006-11-05
Does your freenx work with the dapper repository on edgy?

- Garrett

---

### Post by acegolfer on 2006-11-08
> **garretwp said:**
> Does your freenx work with the dapper repository on edgy?

- Garrett

Yes, FreeNX for Dapper works for Edgy.

---

### Post by imagine on 2006-11-08
Just get the !M server and client from [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)
You need to install the deb packages of NX Client Desktop Edition, NX Node and NX Forever Free Edition in this order.

It isn't fully opensource and only supports two user accounts, but for a home computer this is enough. Usually there is only one person who wants to remotely connect to the PC anyway.


Be aware that after the installation the server uses the default !M-keys as long as you don't create your own.

---

