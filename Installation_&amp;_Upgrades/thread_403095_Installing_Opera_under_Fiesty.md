---
title: "Installing Opera under Fiesty"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by cthippo on 2007-04-06
I installed Fiesty on my desktop this morning and so far everything seems to be working, except Opera.  I downloaded the current version from Opera's website and it seems to install without problems, but when I clicked the icon it crashed and now when I try to run it nothing happens.  I did a full remove and re-install and still nothing.  I even tried launching the executable directly from the /usr/lib/opera/ folder.  Now what?

  System is:

Tyan K8WE
2 x Opteron 250
2 GB ECC reg
2 x Nvidia 7800 GT

here is the Terminal output when I try to do it manually...

```
cthippo@cthippo-desktop:/usr/lib/opera/9.10-20061214.6$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault (core dumped)

```

---

### Post by Colonel Kilkenny on 2007-04-06
There are lots of threads about this.
Newest libs caused Opera to segfault.
Get new Opera from [http://my.opera.com/desktopteam](http://my.opera.com/desktopteam)

---

### Post by lvanderree on 2007-04-07
There is a hot fix released at the opera weeklies blog:
[http://my.opera.com/desktopteam/blog/2007/04/07/hotfix-2](http://my.opera.com/desktopteam/blog/2007/04/07/hotfix-2)

Weeklies can be less stable then the normal builds, but in this case I think it is a better solution then downgrading you xlibs.
But actually, the weeklies have lots of improvements, like better flash support and the new speed dial window is also great!

---

### Post by Kateikyoushi on 2007-04-09
Never tried weeklies before but works fine, thanks for the tip and indeed speed dial is a bright idea.

---

