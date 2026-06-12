---
title: "vmware player install problem"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by Odisej on 2006-11-10
Hi all,

I've seen some similar posts already but i could not find a solution to my problem. Every time i install vmware player the install process is somehow corrupt. This is what happens:

- i install vmware player from repositories and i get an error that the installation was not completely ok. Player works, though, and network is connected. 

- but after that every time I try to install something on Ubuntu I have to configure network connections for vmware player again. It is some kind of installation/configuration loop which never stops. I am also unable to uninstall vmware player after that. The same error is reported each time.

I am puzzled that only a few people have experienced this problem. So I am giving you info on my hardware:

- Acer laptop
- Intel 910 chipset
- Celeron M processor
- GMA 910/915 graphics 
- Atheros chipset wireless (configured ok by Ubuntu)

i also have a problem if I try to install vmware player from .tar  file. The installation is ok but the player does not start. i select its icon, it looks like it is just about to start and bring it up but nothing happens. The same with vmware server.

Any ideas? 

Regards,

Odisej

---

### Post by Giggity on 2006-11-10
VMWare products have been incompatible with all updated Ubuntu releases for several months now.  You have to be using a kernel 2.6.15 or earlier, or else VMWare won't work on your system.  There appears to be no intention to solve this problem.  Different people experience different manifestations of this problem... I for one simply cannot get the bridged networking module to compile, which causes this little "not_configured" flag to pop up in one of VMWare's system directories, making VMWare fail to start up until I delete it.

In the meantime, you can try this every time you have the trouble:

```
sudo rm /etc/vmware/not_configured
```

It's worked for me... then as long as I change the settings to use NAT networking instead of bridged networking I have no trouble getting things to at least run passably.

Let me know how this works for you.

---

### Post by mrfuzzemz on 2006-11-11
> In the meantime, you can try this every time you have the trouble:

Code:

sudo rm /etc/vmware/not_configured

It's worked for me... then as long as I change the settings to use NAT networking instead of bridged networking I have no trouble getting things to at least run passably.

Let me know how this works for you.

Different person, but I wanted to let you know that removing that file did it for me!  Thanks Giggity!

---

