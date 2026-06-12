---
title: "[resolved] I want run livecd on net,how can ido it? helps."
date: 2004-12-31
forum: Installation &amp; Upgrades
---

### Post by qazwer on 2004-12-31
how run ubuntu livecd on net?dhcpd tftpd nfs?

---

### Post by qazwer on 2004-12-31
[QUOTE=qazwer]how run ubuntu livecd on net?dhcpd tftpd nfs?[/QUOTE]
 I have already modify /tftpboot/pxelinux.cfg :

DEFAULT vmlinuz
APPEND nfsdir=192.168.1.1:/ubuntu  lang=us ramdisk_size=100000 init=/etc/init vga=791 initrd=miniroot.gz
BOOT_IMAGE=morphix
TIMEOUT 300

error:can't find base module!

---

### Post by qazwer on 2005-01-02
up

---

### Post by wallijonn on 2005-01-02
What was the fix?

---

### Post by alpha on 2005-01-02
[QUOTE=wallijonn]What was the fix?[/QUOTE]
 This is disappointing, I see this on many forums, a member posts a problem then solves it themselves and instead of posting how they solved the problem, as it may benefit those who are in a similar situation, they just disappear.

---

### Post by qazwer on 2005-01-03
[QUOTE=alpha]This is disappointing, I see this on many forums, a member posts a problem then solves it themselves and instead of posting how they solved the problem, as it may benefit those who are in a similar situation, they just disappear.[/QUOTE]
 disappoint.

---

### Post by alpha on 2005-01-04
[QUOTE=qazwer]disappoint.[/QUOTE]
 
 Didn't you like my reply?

---

### Post by qazwer on 2005-01-04
[QUOTE=alpha]Didn't you like my reply?[/QUOTE]
 hehe , I try resolve it now,If I can ,share it.
I now insert netcard device modules ,use depmod and ldd,but failed,it can't find my netcard 8139.depressed.

---

