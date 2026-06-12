---
title: "Boot xenial client with pxe from chroot dir"
date: 2016-05-26
forum: Installation &amp; Upgrades
---

### Post by nick313 on 2016-05-26
Hi,
I've build a xenial image with debootstrap in a chroot environment and I tryed to boot from them with pxe. I found this problem only  in xenial, if i tried with trusty it's works.
this is my /etc/fstab
```
# nfsv4
/home /exports/home none bind 0 0
/images /nfs4exports/images none auto,bind,x-systemd.automount,x-systemd 0 0
```

and this is my /etc/exports
```

/nfs4exports             *(ro,fsid=0,sync,insecure,no_subtree_check,no_root_squash,crossmnt)
/nfs4exports/images      *(ro,async,nohide,insecure,no_subtree_check,no_root_squash,no_acl)
/nfs4exports/states      *(rw,sync,nohide,insecure,no_subtree_check,no_root_squash,no_acl)
/exports       *(rw,fsid=0,insecure,no_subtree_check,async)
/exports/home *(rw,nohide,insecure,no_subtree_check,async)
```

after pxe boot the client obtain an ip address from dhcp  but show me these error:

> Mount remote root
Begin: Mount remote root ... mount: 192.168.3.253:/images/xenial-test failed, reason given by server: Permission denied
mount: mounting 192.168.3.253:/images/xenial-test on ro failed: Bad file description
Cannot mount nfs root, reboot


The server is an ubuntu trusty with latest update


Any idea?
thanks

---

