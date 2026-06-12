---
title: "Fstab + ntfs 3-g"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2010-03-20
can't auto mount ntfs partiton

```
UUID=Removed For Security Purposes   /media/Media    ntfs3-g    rw,suid,dev,exec,auto,user,async,dmask=002,fmask=002,uid=1000,gid=1000    0    0
```

---

### Post by drs305 on 2010-03-20
> **tad1073 said:**
> can't auto mount ntfs partiton

```
UUID=Removed For Security Purposes   /media/Media    [COLOR="Red"]**ntfs3-g**[/COLOR]    rw,suid,dev,exec,auto,user,async,dmask=002,fmask=002,uid=1000,gid=1000    0    0
```

Try "ntfs-3g" or even "ntfs" which will also work.

---

### Post by tad1073 on 2010-03-20
typo on my part...guess i should have know there was a problem when the drive did mount up after I save the config file.

thank you, 
4 eyes are better than 2

---

### Post by tad1073 on 2010-03-20
here is a comprehensive breakdown of fmask, dmask and umask binary

[http://en.wikipedia.org/wiki/Fmask](http://en.wikipedia.org/wiki/Fmask)

---

