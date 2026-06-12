---
title: "can't autoremove"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by toecutter on 2007-03-27
Every time I add or remove something I get a terminal message saying I should remove various packages: libgdk-pixbuf2 libgnomeprint15 libgnomeprint-bin libxml1 libgnomeprint-data

When I try 'apt-get autoremove' everything is going fine until I get this error message:

> E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

any ideas how to solve this, please?

Thanks for any help :)

---

### Post by zvacet on 2007-03-28
```
sudo apt-get autoremove
```

---

### Post by toecutter on 2007-03-28
Very strange...this time it worked (?) what'd you do, remote into my machine? :P

...and here I was questioning your reply! :) cheers.

---

