---
title: "How do I Install an ISO from command?"
date: 2005-07-02
forum: Installation &amp; Upgrades
---

### Post by XDevHald on 2005-07-02
I have a second tower and no CD's yet to burn this image to it. Would anyone know how to install an ISO image from the command prompt?

Much help is greatly appreciated!

---

### Post by ranf on 2005-07-04
[QUOTE=BB]I have a second tower and no CD's yet to burn this image to it. Would anyone know how to install an ISO image from the command prompt?
[/QUOTE]

What OS is installed on your 2nd tower? 
Are these 2 machines in a network or standalone?
Do both have internet access?

Depending on the answers there are several options.
This might help you:
[Debian installation manual](http://www.us.debian.org/releases/stable/i386/ch02s02.html.en) 

BTW: you can mount any ISO like this:
```
sudo mount ubuntu.iso /mnt -o loop
```

---

### Post by RadixLecti on 2005-07-04
If you haven't already, check out [http://ubuntuguide.org/](http://ubuntuguide.org/)
It has all kinds of nifty tricks to do with your Ubuntu.

```
sudo mount file.iso /media/cdrom/ -o loop
```

usually does the trick for me.

to unmount, just type
```

sudo umount /media/cdrom/
```

---

### Post by XDevHald on 2005-07-04
Thanks guys, worked like a charm!

---

