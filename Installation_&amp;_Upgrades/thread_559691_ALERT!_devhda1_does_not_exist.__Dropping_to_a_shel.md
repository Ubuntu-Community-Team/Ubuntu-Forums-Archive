---
title: "ALERT! /dev/hda1 does not exist.  Dropping to a shell!"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by PhantomWA3 on 2007-09-25
I getting a problem after upgrading to Fiesty, the upgrade went fine but when I reboot it stops at the logo then after 5mins bombs out to a command prompt and displays this:

```
 /bin/sh: Can't access tty; Job control turned off 
```

Now when it bombs out to a command prompt if I then press ctrl->F1 there is the following error messge:

```
Check root=bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hda1 does not exist.  Dropping to a shell!
```

I have managed to boot up using a the generic kernal from grub and once in Ubuntu if I run fdisk -l, i get the following:

```
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
**/dev/hda1   *           1       30024   241167748+  83  Linux**
/dev/hda2           30025       30401     3028252+   5  Extended
/dev/hda5           30025       30401     3028221   82  Linux swap / Solaris

```
[B]
So hda1 does exist so why is it complaining when I boot using the normal kernel?[/B]

Hope this helps.

---

### Post by billrad1 on 2007-09-25
My system has done this twice - once from upgrading versions, and most recently aftera small update.

The problem for me was the fact that in grub, menu.lst, the drive was no longer hda1, but became hde1, etc. Took me about 30 minutes to sort it out.

I ended up redoing menu.lst to a previous kernel, then doing the upgrade again. 

I haven't solved the latest snafu, last nights update

Bill

---

