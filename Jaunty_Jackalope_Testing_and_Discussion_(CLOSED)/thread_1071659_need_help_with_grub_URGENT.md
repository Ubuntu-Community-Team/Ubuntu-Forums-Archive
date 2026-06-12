---
title: "need help with grub URGENT"
date: 2009-02-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jman6495 on 2009-02-16
Hi

I Have Just re-installed ubuntu 9.04 and On My New Install somthing has gone wrong...
i tryed to install gfxboot and it crashed my grub (now i know why so don't worry about that)but i need to remove grub (as in sudo apt-get remove grub)
and then reinstall grub . i realy don't want to reinstall ubuntu again and i saw a tutorial on how to access a system from the live cd and get a terminal up (so i can reinstall grub)but i can't find it.
anyone know how to do it?


ps.
i don't mean :
find /boot/grub/stage1
root (hd0,0)
setup (hd0)

Please help this is realy urgent

   jman6495:(

---

### Post by Phlee on 2009-02-16
What happends if you try and boot a live version from cdrom and run some system level commmands.  Can you reinstall it that way?

---

### Post by jman6495 on 2009-02-16
> **Phlee said:**
> What happends if you try and boot a live version from cdrom and run some system level commmands.  Can you reinstall it that way?

sorry i don't understand ,
i need to access my currently installed ubuntu (on my hard disk) with a terminal.

---

### Post by Phlee on 2009-02-16
right, you can use the desktop install cd to boot "Live" version that is stricly run from cd.  There you can mount your paritions and debug etc.

---

### Post by bodhi.zazen on 2009-02-16
Boot the live CD

Mount your ubuntu root system to say /media/ubuntu

Then

sudo chroot /media/ubuntu
sudo apt-get install grub

If you need further assistance, you might wish to check out supergrub ;)

---

### Post by cariboo on 2009-02-16
If you boot from the Jaunty LiveCD then once at the desktop open a terminal mount your Ubuntu partion to /mnt:

```
sudo mount /dev/sda1 /mnt
```

substitute your partition for /dev/sda1, then chroot the mounted partition:

```
sudo chroot /mnt
```

you should now be able to reinstall grub:

```
sudo apt-get reinstall grub
```

edit: bodhi.zazen beat me to it.

Jim

---

### Post by jman6495 on 2009-02-16
thats it!
thanks
:-)

jman6495

---

