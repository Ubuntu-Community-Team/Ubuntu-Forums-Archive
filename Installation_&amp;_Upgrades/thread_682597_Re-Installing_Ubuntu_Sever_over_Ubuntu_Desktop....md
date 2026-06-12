---
title: "Re-Installing Ubuntu Sever over Ubuntu Desktop..."
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by mwob on 2008-01-30
Hi all,

We installed Ubuntu Desktop 32bit a while back on out Poweredge 2650 Dell Server, and are using it for a VM server, so we have a lot of VM images we want to keep hold of. We recently upgraded the machine to 7Gb of memory, but Ubuntu is only reporting 3.7 Gb, presumably because of the 32bit issue.

So, we think that what we need to do is install the server version, because that has support for the upper memory built into the kernel.

My question is, can I re-install Ubuntu Server over what we have at the moment, and tell it to leave the files I currently have in /var/lib/vmware alone? Or will it delete all these files?

Thanks!

---

### Post by jonallport on 2008-01-30
You should be able to use tasksel to migrate to the server edition.

Personally I would backup/copy the vmware images, do a clean server install and replace the vmware.  In my experience vmware images are very portable in this way.

---

### Post by perfecttao on 2008-01-30
I'm inclined to agree with jonallport - VMWare images are extremely portable - thats one of the major benefits of virtualisation, and you can't beat a clean install to avoid any residual headaches as a result of leftover files......

---

