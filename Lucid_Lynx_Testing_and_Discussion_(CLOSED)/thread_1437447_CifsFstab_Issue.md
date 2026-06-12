---
title: "Cifs/Fstab Issue"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hybridr6 on 2010-03-23
I posted this topic in the general support too, but realized it would probably be better suited for this sub forum.

Ok so when using "sudo mount -a" everything works fine and dandy. Just booting up normally though, the shares are mounted with nothing in them. I'm guessing there is some option needed? Please Help!

Here's the line from my fstab.


```
//10.10.10.2/ash  /home/ash/Documents  cifs  username=ftp,password=,noperm,uid=1000,iocharset=utf8  0  0
```

---

### Post by hybridr6 on 2010-03-24
Ugh having the same problem mounting NFS shares aswell. Adding a share to /etc/fstab and then issue'n mount -a works, but then booting the system normally the shares are again mounted and missing their content. What am I missing here?

---

### Post by stafio on 2010-04-25
I'm having the same problem. This is slightly worrisome with the final release less than a week away.

---

### Post by stafio on 2010-04-25
I tried a few things and got it working for myself. It was just a matter of changing my line in fstab from ```
//Compy/SharedMusic /multimedia/music cifs
``` to ```
//Compy/SharedMusic /multimedia/music cifs guest
```
In my case, I am allowing and mounting the share as a guest user. The first fstab line worked in Karmic, but it looks like the addition of "guest" is necessary in Lucid.

---

### Post by hybridr6 on 2010-04-25
> **stafio said:**
> I tried a few things and got it working for myself. It was just a matter of changing my line in fstab from ```
//Compy/SharedMusic /multimedia/music cifs
``` to ```
//Compy/SharedMusic /multimedia/music cifs guest
```
In my case, I am allowing and mounting the share as a guest user. The first fstab line worked in Karmic, but it looks like the addition of "guest" is necessary in Lucid.

Thanks for the info, will try it out when I get a chance.

---

