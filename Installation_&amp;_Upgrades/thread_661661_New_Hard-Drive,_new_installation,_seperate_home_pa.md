---
title: "New Hard-Drive, new installation, seperate home partition has not defaulted"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by Shinbu-Otaku on 2008-01-08
Hi,

I have just got a new hard drive, and have got my /partition seperate from the / drive. I reinstalled 7.10 last night, and the new install is not picking up that the seperate partition should be used for home. It has created a home folder on the new hard drive, and it is empty (other than the default folders).

Is there any way of getting it to stop using the new home folder, and using the one from my other hard drive instead without re-installing it? I have set this up before and never had a problem, so i dont get what happened this time.

Thanks

---

### Post by Pumalite on 2008-01-08
During the installation, you have to go Manual and pick the partitions one by one.

---

### Post by Shinbu-Otaku on 2008-01-08
damn, i had a funny feeling i would need to re-install, thanks though.

---

### Post by vanadium on 2008-01-08
My feeling is that you probably can just pick up the old home folder by pointing to that old home in /etc/fstab, especially if you are the sole user on the system. You probably will be able to use your old user directory right away. Indeed, your user id will probably be the same in your new installation as it was in your old. You can tell whether your current system still considers your old home directory as belonging to you from the command "ls -l /home". If that lists your user name, then the UID's match. Otherwise, a number will be displayed rather than your user name.

If the old home is still "yours", just add a line to mount your old home under /home in /etc/fstab and reboot.

If the old home is not yours, then I am less sure. You could chown the old /home and its contents, but that is not 100% sure. If some files would for one or another reason need to have a different owner, things could be broken. A more safe approach would be to recreate your user account, but with the UID of your old home, but this requires the command line and you would need to manually add yourself to the necessary groups, etc.

In fact, it might be simpler: man usermod learns me that you may change the UID of your account. thus, you could login to another account (with root privileges), change the UID of your account to correspond with the UID of your old home, and change the mount point of /home in /etc/fstab. After rebooting, you would after login in be known under the new UID, and because of the change in /etc/fstab, your old home would be picked up.

---

