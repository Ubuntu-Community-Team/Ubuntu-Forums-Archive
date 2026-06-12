---
title: "[SOLVED] Synaptic Error"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by maluka on 2007-10-04
what does this mean and how do i fix it?


> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



---

### Post by forestpixie on 2007-10-04
open a terminal

```
sudo dpkg --configure -a
```

never worried too much about what it means other than the obvious :lol:

---

### Post by maluka on 2007-10-04
Lol :d

---

### Post by maluka on 2007-10-04
after doing that i get a new error though

> E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by bapoumba on 2007-10-04
[http://ubuntuforums.org/showpost.php?p=3473785&postcount=2]("http://ubuntuforums.org/showpost.php?p=3473785&postcount=2") May be?

---

### Post by forestpixie on 2007-10-04
as did I and a whole bunch of others I've seen - don't know about you but I didn't finish the install and it got stopped :(

eventually after much mucking about bapoumba came to my rescue with this, I've since found out it's not something to use unless you really need to 

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

try this first though to see if it works

```
sudo apt-get --purge remove virtualbox
```

Edit - hi bapoumba - I remembered :), busy checking I'd got it right while you were posting

---

### Post by maluka on 2007-10-04
AWESOME!!! that fixed it. no more virtualbox for me. what was i thinking!  note to self *do notmess with the virtualbox  :lolflag:

---

### Post by forestpixie on 2007-10-04
after my abortive attempt with virtualbox I had a go with the vmware stuff - managed to get that working with a copy of my existing windows until I got rid completely.

Glad you're sorted too :)

---

