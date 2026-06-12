---
title: "Remove Ubuntu"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by jdt05 on 2007-05-13
Hey everyone,

I need to remove Ubuntu freom my laptop due to lack of space. I have moved Ubuntu onto my main desktop but need to keep Vista on my laptop.

I have the GRUB loader with Ubuntu and Vista as menu items.

I know to get rid of Ubuntu I just need to overwrite the partition but I do not know how to get rid of Grub in place of the default vista loader.

I have tried running the downloadable utility VistaBootPRO 3.2 but this does not see the ubuntu partition and only sees Vista.

Thanks for any help,

j

---

### Post by theaceoffire on 2007-05-13
The easiest way to do this is as follows:

1. Get a copy of GParted here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

GParted is a live CD that lets you move, resize, and delete partitons.

2. Delete the ubuntu partitions after backing up your data.
(Swap, and so forth).

You can just leave it as unallocated.

3. Use the partitioning tool in Vista to absorb that (now) empty space.

Not sure about this, but I think that when you change the partition that Vista will rewrite your Master Boot Record...

^_^ Anywho, this will get rid of it. Have fun.

---

### Post by rillip on 2007-05-13
I'm not 100% sure on vista, but if you have the CD loader, go to the recovery console and do the following to have Windows rewrite your MBR:

Enter fixmbr then fixboot.

This will overwrite the mbr and replace GRUB with the Windows loader, at least, has for past versions, I don't know anything Vista specific but I imagine it hasn't changed much.  If you can get to a recovery console, the above should work.

---

### Post by Aryra on 2007-05-13
> **rillip said:**
> I'm not 100% sure on vista, but if you have the CD loader, go to the recovery console and do the following to have Windows rewrite your MBR:

Enter fixmbr then fixboot.

This will overwrite the mbr and replace GRUB with the Windows loader, at least, has for past versions, I don't know anything Vista specific but I imagine it hasn't changed much.  If you can get to a recovery console, the above should work.

Rillip is correct. Using your install disk for Windows, navigate into setup and then to the recovery console.

```
FIXMBR

Y

FIXBOOT

Y (Not always asked for)

EXIT
```

---

### Post by jdt05 on 2007-05-13
I found the answer out by doing a bit more googlng. fixmbr doesn't work.

For those interested in this, 

load up vista CD

and click to repair windows

click command prompt (bottom window)

Type  Bootrec.exe /FixMbr

Source: [http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html]("http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html")

Thanks for your suggestions,

jT

---

