---
title: "Grub 2 wont find OS on another drive"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Michaelg14 on 2009-10-23
I have two hard drives one (sda) has 9.10 on it with a copy of Windows xp.  I am in the process of moving xp to another drive so I installed it on sdb.  I have not had any luck with grub finding the second copy of Windows on sdb.  Os-prober will not find it and update-grub doesn't either.  I edited grub.cfg (I know that's a no-no) to point to the os on sdb and it works fine so I know it is possible I just don't know how to make grub find it on its own.

---

### Post by ranch hand on 2009-10-23
Read this and some of the links.  There is a way to have a menu you can edit.

[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

---

### Post by SACHINVD on 2009-10-23
u need to modify menu.lst file

---

### Post by ranch hand on 2009-10-23
> **SACHINVD said:**
> u need to modify menu.lst file
You really should read the link given above before giving that advice.  Grub2 does not use a /boot/grub/menu.lst.

---

### Post by Michaelg14 on 2009-10-23
Thanks for that good info.  I used the custom script and everything is now working.

---

### Post by ranch hand on 2009-10-23
> **Michaelg14 said:**
> Thanks for that good info.  I used the custom script and everything is now working.
We will be getting kernel updates.  Edit this entry for your 9.10 and put it on your custom menu and never need to edit it again;
```

 echo "Adding KinkyA1 on sda16" >&2
cat << EOF
menuentry "KinkyA1 on sda16" {
        set root=(hd0,16)
        linux /vmlinuz root=/dev/sda16 so quiet splash
        initrd /initrd.img
}
EOF

```
KinkyA1 indicates that this is a clean install of Kinky Kitty (9.10) and from alpha1.  Yes I am nuts and have too many Kinky installs.

---

### Post by philinux on 2009-10-23
Originally Posted by SACHINVD  u need to modify menu.lst file


> **ranch hand said:**
> You really should read the link given above before giving that advice.  Grub2 does not use a /boot/grub/menu.lst.

Here we go what did we say last night. :P

---

### Post by ranch hand on 2009-10-23
Yup.

---

### Post by VMC on 2009-10-23
> **ranch hand said:**
> Read this and some of the links.  There is a way to have a menu you can edit.

[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

Or you can point them in the direction of your signature :)

---

### Post by ranch hand on 2009-10-23
> **VMC said:**
> Or you can point them in the direction of your signature :)
I changed right after that post.

---

