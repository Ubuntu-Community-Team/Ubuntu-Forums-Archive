---
title: "Online upgrade problem"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by uli on 2007-02-27
I have tried to upgrade from Ubuntu 6.06 to Ubuntu 6.10. online.

Everything seemed to run smoothly until an update script was looking for:

[http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl)

That mirror does not exist!

However, there are two mirrors that appear to have the data required:

[http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) and
[http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl)

How do I change the (automatic) request with the wrong URL to input the correct URL?

Any help is appreciated.
uli

---

### Post by Kateikyoushi on 2007-02-27
You need to edit your sources.list. Copy the following line to the terminal.

```
sudo nano /etc/apt/sources.list
```

Then change the url and ctrl+X to exit and Y to save.

---

### Post by uli on 2007-03-01
Thanks, Kateikyoushi, your advice worked.
uli

---

