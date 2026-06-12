---
title: "Software updater will not work"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by Chris62 on 2013-01-29
Hi,

I have a desktop and a laptop, both dual boot Windows 7 and Ubuntu 12.10. The Ubuntu installation on both machines is identical in that Software Updater has been run at the same time on both machines. The last time that I ran it, there was an update of the kernel which resulted in the desktop having 3.5.0-22-generic but the laptop still has 3.5.0-18-generic.How can I update the laptop kernel, or should I not bother? I tried doing it with Synaptic but the laptop would not boot properly afterwards  so I have removed the one that I installed using Synaptic.

---

### Post by ibjsb4 on 2013-01-29
If its not broke, don't fix it :)

Or you can do a dist-upgrade to a new kernel.
```

sudo apt-get update && sudo apt-get dist-upgrade
```

Number three

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by Chris62 on 2013-01-29
Many thanks for that. It didn't change anything but as it isn't broke, I won't try fixing it anymore

---

### Post by raja.genupula on 2013-01-29
If you broke anything 

```
sudo apt-get install -f
```  will help to fix.

to get complete updates 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```hope that helps.

else you can use update-manager also.

always the server does the matter.

---

### Post by Chris62 on 2013-01-30
Hi raja.genupula,

Thanks for your message. Although I had intended to leave the system as it is, I tried your suggestions but the kernel was not upgraded. It did, however, find an earlier kernel which has now been removed.

I am still at a loss to know why my desktop has kernel 3.5.0-22-generic and the laptop has 3.5.0-18-generic. The only difference between the two is that in the desktop, Ubuntu has a hard disc to itself and in the laptop Ubuntu and Windows 7 share the same hard disc; the two computers have different processors

---

