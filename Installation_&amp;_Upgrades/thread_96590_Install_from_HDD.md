---
title: "Install from HDD?"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by rensu on 2005-11-29
Do anyone know how i can install Ubuntu from HDD?:confused:

---

### Post by gborbolla on 2005-11-29
Take a look at this Wiki page: [https://wiki.ubuntu.com/Installation]("https://wiki.ubuntu.com/Installation")

How would you boot the machine, using a floppy? from windows? from another linux distribution?

---

### Post by rensu on 2005-11-29
This procedure should be possible using a disk image, but it may be necessary to use a different kernel and pass some special argument in menu.lst to tell it to boot from the CD image (Has been achieved using Knoppix). 

Could someone help me to write those few lines? I need to install it from disk image.

---

### Post by rensu on 2005-11-30
Hey can someone help me ?:P

---

### Post by gborbolla on 2005-11-30
[QUOTE=rensu]This procedure should be possible using a disk image, but it may be necessary to use a different kernel and pass some special argument in menu.lst to tell it to boot from the CD image (Has been achieved using Knoppix). 

Could someone help me to write those few lines? I need to install it from disk image.[/QUOTE]

Of what procedure are you talking about?

---

### Post by delbene on 2005-11-30
[quote=rensu]Hey can someone help me ?:P[/quote]

Follow "The CD approach" part of [https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows) and you should be fine... it worked for me.

---

### Post by rensu on 2005-12-01
Actually im trying to install from disk image... whats on HDD drive G: whats mounted with daemon tools... And i need to find out what are the lines for menu.lst for to load the installation from G:.

---

### Post by gborbolla on 2005-12-01
[QUOTE=rensu]Actually im trying to install from disk image... whats on HDD drive G: whats mounted with daemon tools... And i need to find out what are the lines for menu.lst for to load the installation from G:.[/QUOTE]

You won't be able to install from a drive mounted by daemon tools because its an application that runs on windows so when you restart it will be lost, the best you can do is to copy the contents of the cd to your harddrive and install from there.

---

### Post by delbene on 2005-12-01
[quote=rensu]Actually im trying to install from disk image... whats on HDD drive G: whats mounted with daemon tools... And i need to find out what are the lines for menu.lst for to load the installation from G:.[/quote]
 
Follow the guide mentioned above. ;) 
 
You have to unpack (using a software like WinRar [www.rarlabs.com]("http://www.rarlabs.com") ) the iso in a directory and then link the menu.lst to it.
 
For example if you unpack the iso in c:\ubuntu create a menu.lst with this inside:
```
 
title Install Ubuntu
kernel   (hd0,0)/ubuntu/install/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd   (hd0,0)/ubuntu/install/initrd.gz

```

---

### Post by rensu on 2005-12-01
It still asks for CD :(

---

### Post by delbene on 2005-12-02
I don't know if is it possible changing the parameters passed at boot to avoid this.
 
Another way, as I think it search for the mounted cdrom in the "/cdrom" directory, is to link your directory cointaining the unpacked iso on "/cdrom"...
 
Look at this too:
[http://marc.herbert.free.fr/linux/win2linstall.html]("http://marc.herbert.free.fr/linux/win2linstall.html")

---

