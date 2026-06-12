---
title: "natty upgrade LVM: Grub &quot;no such disk&quot;"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by growse on 2011-05-05
I've had this problem on a couple of Ubuntu server upgrades and am keen to get to the bottom of it.

basically, with an Ubuntu 10.10 server installtion where LVM has been used, running through the do-release-upgrade process works perfectly until the reboot stage. Then grub complains with "no such disk" and dumps me out to the grub shell.

From here, I can see (from ls) the following:

```

(hostname-swap_1) (hostname-root) (hd0) (hd0,5) (hd0,1) (fd0)

```

I can enumerate the filesystem on (hd0,1) which seems to contain the /boot filesystem and the filesystem on (hostname-root) seems to contain the / filesystem.

If I execute:
```

linux=(hd0,1)/vmlinuz-image-2.6.38-8-server root=(hostname-root)
initrd=(hd0,1)/initrd.img-2.6.38-8-server
boot

```

It boots, but into busybox saying that the target filesystem doesn't have requested /sbin/init.

Obviously, grub's made a mess somewhere. Any hints as to how I can sort this out?

---

### Post by jeenux on 2011-05-18
Just did an upgrade to natty and got the same problem. Try this:
 
do a "ls (hostname-root)" and note the UUID, then:
 
linux /vmlinuz-2.6.38-8-server root=UUID=5ce0cc37-8fcf-4bf0-bae6-c486a1142bab
initrd /initrd.img-2.6.38-8-server
boot
 
 
on a server on vmware I had to use the PAE kernel instead:
 
linux /vmlinuz-2.6.38-8-generic-pae root=UUID=5ce0cc37-8fcf-4bf0-bae6-c486a1142bab
initrd /initrd.img-2.6.38-8-generic-pae
boot
 
 
Now trying to figure out how to make this permanent...

---

