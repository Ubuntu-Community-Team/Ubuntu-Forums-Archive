---
title: "&quot;Unable to mount root fs..&quot; Boots on one PC but not in another one"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by thenuke on 2005-04-10
I had to use my desktop-PC to install Ubuntu into my server-PC's harddisk.
It booted ok in my desktop-PC but my server-PC wont boot it.

My desktop PC is AMD Barton, and server-PC is an old Pentium 133MHz.

```
/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)
```

Server-PC booted when I did *apt-get remove libc6* (lib.so.6 belongs to that lib), removing that lib of course was not appropriate solution for this :-)

I have another p133 with ubuntu installed on it. I took kernel 2.6.8.1-5-386 and initrd from it and then I was able to boot my problematic server-PC with those!

Kernel&Initrd which does not work on this server but which still works on newer AMD machines is 2.6.10-5-386


Now I am seeking for your knowledge about how to trace the cause?

---

### Post by JoieOee on 2005-04-24
I came across this same problem, and found a solution (though not an amazingly clever one).

The problem is that the initrd image doesn't contain a suitable libc for the old machine to use - it only contains an i686 optimised one, which is added because that's what your new PC is using.

To fix it, I removed the optimised libc package ("apt-get remove libc6-i686") and rebuilt initrd ("mkinitrd -o /boot/initrd.img-2.6.10-5-386"). Subsitiute the correct filename for the image. It'll then work correctly on the old machine.

You may find that when you remove libc6-i686 that it tries to remove ubuntu-base too. If so, you can just re-install it once you've got it working in the old machine.

Hope this helps!

Joe

---

