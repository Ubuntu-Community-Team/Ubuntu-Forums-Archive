---
title: "installation of ubuntu 64bit server fails - cannot install base system"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by nicolasdiogo on 2010-09-08
Hi folks,

i have installed a ubuntu a few times using different versions and hardware.

but this is a first for me.

while installing ubuntu server on a machine that used to run ubuntu hardy (just tried CentOS), i get error as below>

```

!! install the base system
cannot install base system
the installer cannot figure out how to install the base system. no installable CD-Rom was found and no valid mirror was configured.

```

*however* i have test the CD on this machine and it passed

i also burned 3 other CDs and all fail.

i am installing on LVM-root but it was working fine on Hardy before

while the installer is running - on a second ternminal if i try
```

ls -l /cdrom/*

```

i get errors such as:
```

ls: /cdrom/ubuntu/doc:    Input/output error
..

```


any idea on what i can do?

many thanks,

Nicolas

---

### Post by nicolasdiogo on 2010-09-08
just a quick update on my problem.

i tried to
```

umount /cdrom
mount /dev/cdrom /cdrom

```

and it seems to have fixed the problem.

as for what the problem was *NO* idea.

hope this helps someone.
or at least myself if i ever find this problem again.

tchau

---

### Post by kr0nt4b on 2010-09-17
unmounting and mounting the cdrom did the trick for me as well. Only i couldnt mount it in the same way as nicolasdiogo. I needed to do this:
```
umount /cdrom
mount /dev/disk/disk-by-id/<cdrom name>
```

---

