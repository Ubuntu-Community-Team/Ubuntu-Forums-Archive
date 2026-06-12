---
title: "Add/Remove Applications not dowloading after a previous cancelled download"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by vivtho on 2008-05-14
Hi,

Last night I was away from my regular broadband connection and had used dial-up to connect to the net.  I set some software for download, but cancelled it while it was downloading because of the large download size (about 45MB).  Today, when I got back to my high-speed connection and tried to download the same software again, the Add/Remove Applications window just does not move ahead after the confirmation screen ("Apply the following changed?").  It stays stuck there and there is no network activity.  The window also cannot be closed and I have to restart to make it go away.

I'm a newcomer to Linux and am running Ubuntu 8.04.

Any help would be really appreciated.

Thanks,
V. Thomas

---

### Post by vivtho on 2008-05-14
UPDATE:

It's working now.  I'm not sure what exactly fixed it, but I tried the following command after looking up some man pages.
```
sudo apt-get clean
```

Would this be the reason why it started working again?

---

### Post by mxg01 on 2008-05-14
Yes, 'apt-get clean' clears up any working files used by apt and any partially downloaded packages. So you've just gone back to the state before you started the aborted download.

---

### Post by vivtho on 2008-05-14
> **mxg01 said:**
> Yes, 'apt-get clean' clears up any working files used by apt and any partially downloaded packages. So you've just gone back to the state before you started the aborted download.
Thanks! That's something new to learn today.

---

