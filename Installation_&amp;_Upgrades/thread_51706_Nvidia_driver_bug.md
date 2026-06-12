---
title: "Nvidia driver bug?"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by wgscott on 2005-07-25
I am using the ubuntu nvidia packages.  Only the admin user can use graphics display unless the permissions are reset using a command such as

```
sudo chmod -R 666 /dev/nvidia* 
```

The worst part is it seems the permissions get corrupted upon reboot, so I had to stick this in one of the init.d scripts to get the change to stick.  

Is this a known problem, bug, feature, peculiarity of my system, or what?

---

