---
title: "Grub Broken"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by rustysail on 2007-07-04
Hey guys.  I had Feisty installed as my only OS, but I decided to play with Gentoo.  The gentoo install didn't go as well as I had hoped so I deleted with the intentions of starting over.  Unfortunately, I did grub-install on gentoo and forgot to do it on feisty before turning my computer off.  Now when I try to boot up grub shows an error.  I know that in order to fix this I need to do a grub-install (need a reminder of exact procedure) for ubuntu.  But I can't do that without somehow booting into feisty or chrooting.  My only place that I can chroot is the live cd of the feisty install disk.

Worst case I will install feisty again in a different partition and wait for grub on that install to detect my other OS.

I could use some help though.  I have some important things on fiesty right now and its set up just the way I like it so I would really not like to have to delete it.

Thanks

---

### Post by koshari on 2007-07-04
you dont have to reinstall or chroot,

just boot with a live disk, mount your hdd with ubuntu on it, 

run grub and use root and boot commends ,

---

### Post by Vajra Vrtti on 2007-07-04
After booting from the Live CD, this are the commands to restore grub:
```
sudo grub
find /boot/grub/stage1
root (hd#,#)
setup (hd#)
quit
```

Replace # with the appropriate values for you system, based on the response of the *find* command.

---

### Post by rustysail on 2007-07-04
Thanks guys it worked like a charm.
I'm back in my old perfectly configured feisty
Thanks so much

---

