---
title: "backup home dir to another partition"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by playersgc on 2006-08-26
I'd like to backup my home directory to a different partition just in case I mess up the current one.  There's already other files on the target partition, and it's formatted vfat.  I'd rather not compress it, so I could get to the files easily if I wanted to, but if compressing is really the best or only way, I'll do it.

I tried booting from a LiveCD, and running:
> sudo cp -r /mnt/hda2/home /mnt/hda4/home

and it copied a few things, but then it started spitting out a bunch of errors, like 
> cp: cannot create regular file `/mnt/hda4/home/mylaptop/.openoffice....' : Operation not permitted

etc.

Is there an easy way to do this?  (I thought cp was the easy way.)
Thanks!

---

### Post by confused57 on 2006-08-26
Maybe this will work for you:

[http://psychocats.net/ubuntu/separatehome.html](http://psychocats.net/ubuntu/separatehome.html)

---

### Post by zorkerz on 2007-03-10
> Maybe this will work for you:

[http://psychocats.net/ubuntu/separatehome.html](http://psychocats.net/ubuntu/separatehome.html)[]("http://psychocats.net/ubuntu/separatehome.html")
 		
That helped me.  its this command i needed to allow me to copy all the contents of home over i believe. ```
find . -depth -print0 | sudo cpio --null --sparse -pvd /backupdir
```

---

