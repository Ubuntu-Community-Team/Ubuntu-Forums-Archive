---
title: "update linux kernel on the server"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by remsy on 2006-07-18
Hi. I have ubuntu dapper drake desktop and server versions installed. I noticed that the desktop version updated the linux image through the automatic update tool, to 6.15.25 I believe. 

How can I also update the server's linux kernel from the command line? is there an automatic update tool or something equivalent?

Thanks,

Remsy

---

### Post by joft on 2006-07-19
Hi,

what about using
```

sudo apt-get update
sudo apt-get upgrade

```
?

Though, I don't know if there is a really "automatic update tool" for the console, in the way it's done in the desktop version.

---

