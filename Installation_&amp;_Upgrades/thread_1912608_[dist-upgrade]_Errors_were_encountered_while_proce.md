---
title: "[dist-upgrade] Errors were encountered while processing:"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by RicardoE on 2012-01-20
Hello ubuntuers :)

so I ran dist-upgrade in a server instance, as you might now grub is blocked or something so I get the following error:

```
Errors were encountered while processing:
 linux-image-2.6.32-342-ec2
 linux-image-ec2
 kexec-tools
```

and some dependecy stuff, I have tried everything and I cant get passed this, I dont want to restart the server, as I will loose so much job done :(

The server instance is running version 10.04

your help is must appreciated.

---

### Post by zvacet on 2012-01-24
What

```
sudo dpkg --configure -a
```

say?

---

