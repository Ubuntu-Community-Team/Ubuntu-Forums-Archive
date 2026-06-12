---
title: "splash in ubuntu 6.06.1 server"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by mitjab on 2006-09-02
I install ubuntu 6.06.1 server and now i would like to do that in start i will have splah like in non server ubuntu 6.06.1 vesrion.

How i can make this?
i search in forum but i canb not find any post about this.

Thx

---

### Post by &#12465;&#12452;&#12488; on 2006-09-02
Try installing the usplash package.

---

### Post by mitjab on 2006-09-03
so i must just install usplash and then splah will start working?

---

### Post by &#12465;&#12452;&#12488; on 2006-09-03
I don't know if Ubuntu automatically configures usplash to work right after installation, Debian didn't, but I think it's quite likely that Ubuntu'll do the trick.

---

### Post by mitjab on 2006-09-03
yes it work nice now. Thx

What about that i will have image in console. Now is background black. Is it possible to have image in background of console?

---

### Post by &#12465;&#12452;&#12488; on 2006-09-03
You need a graphical display (X11) to display images, and installing and running xorg would be slightly impractical for such a little task.

---

### Post by mitjab on 2006-09-03
are you sure becouse in gentoo which i use it before there was no need xorg for this.

It runs on vesa. I hope you know what i am asking for. I think that it said Fbsplash.

---

### Post by codejunkie on 2006-09-03
it can be done on ubuntu, but you will have to patch and recompile your kernel to get fbsplash to work. just search the forums for ***fbsplash*** or ***bootsplash*** there's a couple of howto's on how to get it working in ubuntu if you feel like compiling a new kernel.

---

### Post by mitjab on 2006-09-03
without a compile a new kernel this is not possible? I do not want to compile a new kernel becouse i never not know if then will work like it must!

is it possible to make this in usplash?

---

### Post by Ptero-4 on 2006-09-03
It's AFAIK impossible b/c the image on consoles is done in an initrd and needs hooks that the ubuntu kernel doesn't have by default (it's said that the ubuntu dev's won't include fbsplash by default b/c a big megacorp treathened to put a lawsuit if the ubuntu dev's installed the fbsplash support in the kernel that ships with ubuntu).

---

