---
title: "Lost my ubuntu"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by gilch on 2011-07-14
I am not sure where to post this.
Yesterday, everything was fine, I did the update that was proposed, and everything was fine after that as well.
This morning it would not boot; when I tried to wake up the system, it gave me a bunch of errors, the last ones being as follows:

"mount error: could not resolve address for servername: No address associated with hostname
mountall: mount /media/shares [1402] terminated with status 1"

I am writing this in Win 7 since I lost ubuntu.
I am using ubuntu 11.04.

Tell me where I should post if this is not the right place.... thanks.

---

### Post by Mark Phelps on 2011-07-15
You HAD something mounted to /media/shares -- something that no longer mounts properly.

Was this a folder on your local network, on another PC?

Was this an NTFS partition on your PC (possibly, Win7)?

The short-term fix would be to remove the offending mount line from /etc/fstab.  That should then allow you to finish booting into Ubuntu.

Since you can't actually boot into Ubuntu, you would need boot from an Ubuntu CD, open Nautilus in root mode (using a terminal, enter "gksudo nautilus"), find the /etc/fstab file, remove the offending line, save the file -- and reboot.

---

### Post by gilch on 2011-07-16
Thanks.
I got back onto ubuntu by using `previous version`.
I looked for etc/fstab, but I can't find it. I looked under file system, and under etc, but it was not there. I don't know how else to find it.

Gilles

---

