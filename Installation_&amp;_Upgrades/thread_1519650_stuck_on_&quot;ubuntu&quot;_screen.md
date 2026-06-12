---
title: "stuck on &quot;ubuntu&quot; screen"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by supermooshman on 2010-06-28
Hey all,

Recently I decided to install ubuntu on an old desktop which was gathering dust.
All went well, but during the first update, the screen suddenly went to the "ubuntu" screen (the one that you can see when starting up, the one with the four dots).
After a while being stuck there, I decided for a reboot, but now I am stuck on the same screen (before login)

does anyone know what to do?
Thanks

---

### Post by Rubi1200 on 2010-06-28
Hi,
first of all please tell us a little bit more about your computer e.g. laptop/desktop, RAM, graphics card etc.

If you have Intel graphics this might do the trick:

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter in this order:

i915.modeset=1

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz i915.modeset=1 --**

Now hit Enter and hopefully you will be at the desktop admiring Lucid Lynx 10.4

If this works, you can then install Ubuntu and follow the workarounds in this link to make it more permanent:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Use the  Glasen's PPA fix: it works, but only for Intel 855gm chips.

Use this to see information about your chip:

```
lspci -nn | grep VGA
```


Good luck!

---

