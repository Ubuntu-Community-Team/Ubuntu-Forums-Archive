---
title: "Removal of Latest Kernel"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by jda8818 on 2010-07-23
Hello All, I've been running 10.04 for about two months now; but I  have zero linux experience prior to that.

After a recent upgrade to kernel 2.6.32-23 (UpdateManager suggestion):

```
jadcock@HTPC:~$ uname -a
Linux HTPC 2.6.32-23-generic-pae #37-Ubuntu SMP Fri Jun 11 09:26:55 UTC 2010 i686 GNU/Linux
jadcock@HTPC:~$ 
```my system became unstable, locked up, and I've lost HDMI sound output.  system  locks up every now and then.  

Working with the multimedia & video group (very helpful) I've been asked to boot into an  earlier kernel and:

> Do this for me please. Reboot into an older kernel and go to synaptic.  Find and mark for complete removal your latest kernel and header  packages. Apply.
I'm unsure which items in synaptic to mark for complete removal.  There are several that reference the 2.6.32-23 kernel, but I'm hesitant to mark them all and cross my fingers.

See my  previous thread in multimedia & video:

[http://ubuntuforums.org/showthread.php?t=1533162](http://ubuntuforums.org/showthread.php?t=1533162)

Anyway, as usual, all comments and or suggestions will be  appreciated!

JA

---

### Post by iponeverything on 2010-07-23
Is pretty strait forward. So you have manged to boot into the earlier kernel I take it? 

post the output of:

```
uname -a
```

this will tell us what kernel currently running. 

If you are running the earlier kernel then just go into synaptic and mark:

linux-image-6.32-23-generic-pae

for removal if it is the bad kernel. Next in Synaptic - highlight the good working kernel check "Package -> Lock Version" in the Synaptic menu and it won't get upgraded next time. Then go to apply. If shouldn't, but if does want to remove any packages that are not related to bad kernel -- post what are and we can work out what is going. 

After you remove linux-image-6.32-23-generic-pae - the previous kernel will become the default.

---

### Post by jda8818 on 2010-07-23
Thanks you ipoeverything!

the -23 kernel is gone and my default boot is into the -22 ...

so i'm back  working on my original problem

Thanks again,

JA

---

