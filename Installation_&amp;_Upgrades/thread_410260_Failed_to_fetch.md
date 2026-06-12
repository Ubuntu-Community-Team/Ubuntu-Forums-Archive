---
title: "Failed to fetch ???"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by dcahill on 2007-04-15
Can someone tell me why Feisty's update manager is sending the following messages? 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hotkey-setup/hotkey-setup_0.1-17ubuntu8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hotkey-setup/hotkey-setup_0.1-17ubuntu8_i386.deb)
  404 Not Found [IP: 91.189.89.8 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb)
  404 Not Found [IP: 91.189.89.8 80]

Thanks.

---

### Post by bapoumba on 2007-04-15
Hi,
try to run:
```
sudo aptitude update
sudo aptitude upgrade
```

---

