---
title: "blueprints for discussion at UDS"
date: 2008-12-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-12-07
Hi all, 
 I was just checking the blueprints to be discussed at UDS this time around. 

The main themes seem to be :-

a. Mobility (Netbooks, Atom Processors you get the picture)
b. Power-management (should relate to mobility as well)
c. Fast boot-up 
d. Xorg 

One of the more interesting ones seems to be this one 

[https://blueprints.edge.launchpad.net/ubuntu/+spec/xorg-jaunty](https://blueprints.edge.launchpad.net/ubuntu/+spec/xorg-jaunty)

I'm sure this is what many would be interested as well. 

Another interesting one is this one 

[https://blueprints.edge.launchpad.net/ubuntu/+spec/volid-vs-blkid](https://blueprints.edge.launchpad.net/ubuntu/+spec/volid-vs-blkid)

I have never quite understood why we chose volid . 

blkid is needed for moving to ext4 . Also don't we use blkid in our boot infrastructure 

```

~$ blkid
/dev/sda1: UUID="49b2cc28-fa6d-4d0d-ae16-040861151df0" TYPE="ext3" SEC_TYPE="ext2" 
/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="fc24631b-c156-4beb-bf61-be84e24bc946" TYPE="ext3" 
/dev/sda3: UUID="7c003381-39d7-4126-8b9b-dbdbf3955eea" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="baa0d92f-3112-42ab-aaf7-b2e416dea782" TYPE="swap" 
/dev/sdb1: UUID="49b2cc28-fa6d-4d0d-ae16-040861151df0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="dcf827c4-c7cb-4d66-9cb9-7baf82a69f3c" TYPE="ext3" 
/dev/sdb6: UUID="d69559ab-c9f5-40fd-b048-8f0a98a2a977" TYPE="swap" 
/dev/sdb7: UUID="20168ab6-abce-4804-840f-51a2036c0a5e" SEC_TYPE="ext2" TYPE="ext3" 

```

Feel free to check out the whole list of the same [https://blueprints.edge.launchpad.net/sprints/uds-jaunty/](https://blueprints.edge.launchpad.net/sprints/uds-jaunty/)

---

### Post by Nullack on 2008-12-10
I like the blueprints on:

security improvements
improvements to cruft remover
better boot time

---

### Post by Eclipse. on 2008-12-10
Another one thats really got me excited is the distributed development with bzr, some of its already in place along with the reorganisation of the archive which I think has been well overdue.

---

### Post by Slug71 on 2008-12-10
> **ShirishAg75 said:**
> Hi all, 
 I was just checking the blueprints to be discussed at UDS this time around. 

The main themes seem to be :-

a. Mobility (Netbooks, Atom Processors you get the picture)
b. Power-management (should relate to mobility as well)
c. Fast boot-up 
d. Xorg 

One of the more interesting ones seems to be this one 

[https://blueprints.edge.launchpad.net/ubuntu/+spec/xorg-jaunty](https://blueprints.edge.launchpad.net/ubuntu/+spec/xorg-jaunty)

I'm sure this is what many would be interested as well. 

Another interesting one is this one 

[https://blueprints.edge.launchpad.net/ubuntu/+spec/volid-vs-blkid](https://blueprints.edge.launchpad.net/ubuntu/+spec/volid-vs-blkid)

I have never quite understood why we chose volid . 

blkid is needed for moving to ext4 . Also don't we use blkid in our boot infrastructure 

```

~$ blkid
/dev/sda1: UUID="49b2cc28-fa6d-4d0d-ae16-040861151df0" TYPE="ext3" SEC_TYPE="ext2" 
/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="fc24631b-c156-4beb-bf61-be84e24bc946" TYPE="ext3" 
/dev/sda3: UUID="7c003381-39d7-4126-8b9b-dbdbf3955eea" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="baa0d92f-3112-42ab-aaf7-b2e416dea782" TYPE="swap" 
/dev/sdb1: UUID="49b2cc28-fa6d-4d0d-ae16-040861151df0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="dcf827c4-c7cb-4d66-9cb9-7baf82a69f3c" TYPE="ext3" 
/dev/sdb6: UUID="d69559ab-c9f5-40fd-b048-8f0a98a2a977" TYPE="swap" 
/dev/sdb7: UUID="20168ab6-abce-4804-840f-51a2036c0a5e" SEC_TYPE="ext2" TYPE="ext3" 

```

Feel free to check out the whole list of the same [https://blueprints.edge.launchpad.net/sprints/uds-jaunty/](https://blueprints.edge.launchpad.net/sprints/uds-jaunty/)

I dont think we use blkid

---

### Post by cariboo on 2008-12-10
If you  are fully up to date check /boot/grub/menu.lst. On my system I'm using blkid instead of device labels to boot.

Jim

---

### Post by cariboo on 2008-12-10
If you  are fully up to date check /boot/grub/menu.lst. On my system I'm using blkid instead of device labels to boot.

```
title		Ubuntu jaunty (development branch), kernel 2.6.28-2-generic
uuid		c6afffda-4b72-454e-8bfb-29d122e3cc3e
kernel		/boot/vmlinuz-2.6.28-2-generic root=UUID=c6afffda-4b72-454e-8bfb-29d122e3cc3e ro quiet splash iommu=noaperture
initrd		/boot/initrd.img-2.6.28-2-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-2-generic (recovery mode)
uuid		c6afffda-4b72-454e-8bfb-29d122e3cc3e
kernel		/boot/vmlinuz-2.6.28-2-generic root=UUID=c6afffda-4b72-454e-8bfb-29d122e3cc3e ro  single "iommu=noaperture
initrd		/boot/initrd.img-2.6.28-2-generic
```

Jim

---

