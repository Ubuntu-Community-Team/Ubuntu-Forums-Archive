---
title: "i/o error while booting livecd"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by deczo on 2011-11-03
Hi there,
I've got huge problem after upgrading from 10.04 to 11.10:
(32bit)

the system does not start at all now, it freezes with this screen:

```
fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
/dev/sda1: clean, 435591/732960 files, 1546925/2929408 blocks
/dev/sda6: clean, 81410/1831424 files, 5975098/7323904 blocks
storage: clean, 81400/4210704 files, 6308902/16809984 blocks
 * Starting network connection manager         [OK]
 * Starting CUPS printing spooler/server       [OK]

```

Also when I try to boot liveCD (i86 DVD version) from my portable hd (usb) which worked before like a charm, now it loads welcome screen and after choosing to run ubuntu it breaks with 'i/o error please reboot'

I tried and got the same error while booting from cd (i86 desktop version).


Here's what I did:
boot the hd version, then install the system, chosen UPGRADE existing 10.04 to 11.10 and after reboot the problem occured.


Any help would be appreciated.

---

### Post by deczo on 2011-11-04
Anyone? There is nothing I can do with the problem and literally can't use the pc, any clues?

---

### Post by awam66 on 2011-11-04
You cannot upgrade directly from 10.04 to 11.10, you have to go through from 10.04 to 10.10 then to 11.04 then to 11.10. If you did not do this then a clean install is probably the only option.

---

### Post by christophevr on 2011-11-04
Hello.

i/o error while booting live cd , happens to me as well if I burn the cd to fast. When I make an ubuntu live cd I always use the slowest possible speed then it works.

---

### Post by deczo on 2011-11-04
@awam66 
you cannot do in upgrade manager, thats true.
But you can do it with livecd/usb.

@christophevr
I will try that, downloading the image atm.

---

