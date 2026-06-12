---
title: "problem with installing packages during installation by preseed"
date: 2015-10-21
forum: Installation &amp; Upgrades
---

### Post by ali abry on 2015-10-21
Hi every body
i'm trying to install some package during ubuntu server 12.04 installation using preseed, i tested these two pereseed:

     Code:
```
      d-i preseed/late_command string in-target dpkg -i /cdrom/extra/*.deb
```

```
d-i preseed/late_command               string \
    for deb in /cdrom/extra/*.deb; do cp $deb /target/tmp; \
    chroot /target dpkg -i /tmp/$(basename $deb); done
``` 
but both of theme give error that says it couldnt execute theme  :
     Code:
```
      exit 0
```

---

