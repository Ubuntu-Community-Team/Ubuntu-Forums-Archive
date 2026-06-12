---
title: "Fresh install of 11.10 - forgot my home directory is encrypted..."
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by RussellEngland on 2011-12-03
I originally upgraded from 11.04 to 11.10 but it all went a bit wrong.

I've got 3 partitions
[LIST]
[*]ubuntu root /dev/sda6
[*]swap /dev/sda7
[*]data /dev/sda5 - which I had mounted as home (not sure how though)
[/LIST]

So I copied /etc /var /usr/local to the data partition. Then deleted the ubuntu and swap partitions. Recreated them and made a fresh install.

All went well until I tried to access the data partition. Then realised it was encrypted...

If I browse to
/media/e0eb9b14-c2f3-48f3-95a3-554d44f70e1e/russ

The contents are
Access-Your-Private-Data.desktop 
README.txt

I'm still a linux amateur. At the very least it would be great to get access to the data. :)

Any ideas?

Thanks, Russ

---

### Post by RussellEngland on 2011-12-06
Yey!! Got access by running

```
sudo ecryptfs-recover-private
```

---

### Post by Megaptera on 2011-12-06
Thanks for sharing the answer & glad you got it sorted.

---

### Post by unclejac on 2012-03-11
Thanks Russ, your thread helped me retrieve my data after HDD decided to go. 

time for a new old hdd and a fresh install 

unclejac

---

