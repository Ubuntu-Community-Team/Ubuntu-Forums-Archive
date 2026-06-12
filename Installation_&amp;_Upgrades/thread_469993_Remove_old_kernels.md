---
title: "Remove old kernels"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by jbennet on 2007-06-10
My ubuntuserver has about 10 old kernels listed in grub. there taking up loads of space. I dont want to just remove the entries from grub, i want to actually remove all kernels aparat from the most recent one (it works fine). I would usually use synaptic for this but this server has no GUI.

How can i list all the installed kernel versions?

and if i list them can i just do apt-get remove?

---

### Post by jbennet on 2007-06-10
okay i did it by looking at the version numbers in grub but niow its kinda broken

it crashes at :

" * running local boot scripts /etc/rc.local "

it also says:

" *Unknown Stanza"

and i have issues with something called MDADM 

it boots ok in recovery mode just not normal mode

---

### Post by jbennet on 2007-06-10
Ok i managed to fix the boot scripts issue

apparently its a known problem that updating edgy to fesity   /etc/event.d/tty1 (you must manually edit tty1 through to tty6)

The last two lines are:

respawn
/sbin/getty 38400 tty1exec /sbin/getty 38400 tty1

but should be:

exec /sbin/getty 38400 tty1
respawn

After fixing each of the tty files, the machine booted fine, though you need to hit enter at the end

---

### Post by pt123 on 2007-06-10
to remove old images just use synaptic search for linux-image

and chose to completely remove the older versions

---

### Post by jbennet on 2007-06-10
as i said, i dont have a gui so no synaptic.

dont worry anyway, i got it fixed in the end

---

