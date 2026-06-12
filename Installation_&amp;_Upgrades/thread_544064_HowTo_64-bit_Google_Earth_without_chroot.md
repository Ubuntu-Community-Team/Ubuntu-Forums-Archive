---
title: "HowTo: 64-bit Google Earth without chroot"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by IntuitiveNipple on 2007-09-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/62924](https://bugs.launchpad.net/ubuntu/+bug/62924) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I recently posted in a launchpad bug how to install and run Google Earth 4.x on Gutsy Tribe-5 64-bit. I was posting some other 64-bit 'HowTo's and thought I should add this one for completeness.

[Download the latest Google Earth for Linux](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin).

If not already installed, get the 32-bit libraries:
```
$ sudo apt-get install ia32-libs
$ wget http://gb.archive.ubuntu.com/ubuntu/pool/main/i/ia32-libs-gtk/ia32-libs-gtk_16_amd64.deb
$ sudo dpkg --force-all -i ia32-libs-gtk_16_amd64.deb
$ sudo apt-get -f install

```
Now you should be able to install 32-bit applications:
```
$ sudo ./GoogleEarthLinux.bin
$ sudo ln -s /opt/google-earth/googleearth /usr/bin/googleearth
$ googleearth

```

---

### Post by lentomies on 2007-12-04
Hello,

Your posting helped me install Google Eart in my 64 bit envir.... Thank you for the info!!!


Will this also allow me to run other 32 bit pieces of S/W too? 

thanks!

---

### Post by duruttye on 2007-12-23
[HTML]kucko@mashina:~/Desktop$ sudo ./GoogleEarthLinux.bin 
sudo: ./GoogleEarthLinux.bin: command not found
[/HTML]

This is where I'm stuck.

Any help will be greatly appreciated.
Thanx

---

### Post by duruttye on 2007-12-24
Ok, got it installed, this is where I'm stuck again:

[HTML]Xlib:  extension "XFree86-DRI" missing on display ":1.0".
[/HTML]

and stops forever.

Any ideas?
thanx

---

### Post by supernova_hq on 2008-02-27
I'm getting the exact same problem here.

when I try to run googlearth from console I get:
> ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
Xlib:  extension "XFree86-DRI" missing on display ":1.0".

I am running Ubuntu 7.1 on and AMD64
I am using compiz (with xserver-xorg).
The program did not work before switching to compiz and xserver-xorg either.

-supernova_hq

---

