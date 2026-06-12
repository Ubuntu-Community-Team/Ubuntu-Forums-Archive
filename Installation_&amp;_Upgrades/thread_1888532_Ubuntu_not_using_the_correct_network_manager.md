---
title: "Ubuntu not using the correct network manager"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by pbarclay on 2011-11-29
Hi

I have upgrades to Ubuntu 11.10 from 10.04, I have a 32-bit version install and an HP Pavilian Entertainment Laptop.

When I installed 10.04 I had to update my network manager as the default one caused the wireless network to drop out randomly, the new network manager works great and this post is a testament that it is still working.

However Ubuntu 11.10 seems to think that I have no wireless network and as such Ubuntu Software Centre will not let me install anything as it just says "No network connection" and the install button is disabled. This is the same for all system widgets that need to connect to the internet. Basically it seems that Ubuntu is relying on the Default network manager to tell it about the network status despite it not being used.

Does anyone know where the config is to let Ubuntu use the functioning manager?

Thanks
Paul

---

### Post by raja.genupula on 2011-11-29
hi man ....

```
sudo apt-get update 
```

i need this output.

please post that here,

---

