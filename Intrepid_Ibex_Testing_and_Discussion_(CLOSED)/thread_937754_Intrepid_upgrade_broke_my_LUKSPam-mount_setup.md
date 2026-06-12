---
title: "Intrepid upgrade broke my LUKS/Pam-mount setup"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by fritz276 on 2008-10-04
Hi,

I used 8.04 and have an encrypted /home partition with LUKS. I basicly followed a tutorial on ubuntuusers (its German, sorry) and it worked perfect. The important lines (to have /home mounted automatically when a login, since LUKS password and users password are the same) where

<volume fstype="crypt" path="/dev/sd<Partition>" mountpoint="/home" options="fsck" />

in /etc/security/pam_mount.conf.xml

and

@include common-pammount

in /etc/pam.d/common-session

After the update to 8.10, I couldnt login (neither as root, which has its home directory at /root, nor as user). After booting from a CD and removing the @inclde common-pammount from /etc/pam.d/common-session I could login again at the console (with root and user), but not with GDM as user (nothing happens). I have to manually mount my crypted /home to be abled to login in GDM as user. 

Can someone please help? I dont know what changed in the new PAM packages, and I dont want to manually mount my crypted home every time.

Thanks

---

### Post by overdrank on 2008-10-04
Moved Intrepid Ibex Testing and Discussion :)

---

