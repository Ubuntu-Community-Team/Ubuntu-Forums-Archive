---
title: "Mounting a drive to computer"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by xeocub on 2007-08-24
I just reinstalled feisty, and everything is going wonderful. As usual, I was asked where to mount which drive and everything is fine. Now I added another driver, and I am unable to mount it as the others have been (IE in Computer:/// and on the desktop) 

Mounting the drive is not a problem for my /media/blah folder, and the drive works fine. 
The question is, how do I mount the way Ubuntu mounts the drives so that it will show up in all my menus, the Computer:/// folder etc?

Thanks!

---

### Post by jimrz on 2007-08-24
> **xeocub said:**
> I just reinstalled feisty, and everything is going wonderful. As usual, I was asked where to mount which drive and everything is fine. Now I added another driver, and I am unable to mount it as the others have been (IE in Computer:/// and on the desktop) 

Mounting the drive is not a problem for my /media/blah folder, and the drive works fine. 
The question is, how do I mount the way Ubuntu mounts the drives so that it will show up in all my menus, the Computer:/// folder etc?

Thanks!

you need to add it to /etc/fstab. it will then auto mount whenever you boot up

---

### Post by xeocub on 2007-08-24
I know that.. but that's not what I'm talking about. 

If you add it to fstab, it will mount at every boot, but it still won't mount the way the feisty installation does. It will never be in Computer:///, nor the menus and such.

Anyone know how to do that?

---

