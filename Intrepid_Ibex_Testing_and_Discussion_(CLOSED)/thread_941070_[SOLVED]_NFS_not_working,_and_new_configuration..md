---
title: "[SOLVED] NFS not working, and new configuration."
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by perlluver on 2008-10-07
```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)

/media/disk 192.168.2.1/24(rw,no_root_squash,async)
```

This is what I have in exports, now it will not mount on the other computers in the house, but this is what I have used since Gutsy.  And the new config is confusing, particularly gss/krb51, what does that mean?

---

### Post by perlluver on 2008-10-09
I hate bumping, but I thought I might need one, anyone have any info?

---

### Post by FuturePilot on 2008-10-09
How are you mounting the share on other computers? Is the share in fstab? Try mounting the share manually like
```
sudo mount 192.168.x.x:/files /media/share
```
(Change that IP to the server's IP and path to the shared directory and the last part is where you want to mount it on the local machine)

Does that give errors?

---

### Post by perlluver on 2008-10-09
> **FuturePilot said:**
> How are you mounting the share on other computers? Is the share in fstab? Try mounting the share manually like
```
sudo mount 192.168.x.x:/files /media/share
```
(Change that IP to the server's IP and path to the shared directory and the last part is where you want to mount it on the local machine)

Does that give errors?

Thanks FuturePilot, and yes indeed it does throw up an error of: ```
mount.nfs internal error
``` before that it was giving connection errors.

---

### Post by perlluver on 2008-10-10
Did a fresh install of Intrepid and it started working again today, no idea why it wasn't working, but it is now.

---

