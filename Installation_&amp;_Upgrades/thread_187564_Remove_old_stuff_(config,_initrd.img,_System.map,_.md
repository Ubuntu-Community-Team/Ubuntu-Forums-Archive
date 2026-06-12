---
title: "Remove old stuff (config, initrd.img, System.map, vmlinuz)"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by Dutch on 2006-06-03
Upgrading to 6.06 went great ! Thanks Ubuntu team !

Question:
Here below is my boot file, what and how can I remove ?

Do I use rm ore uninstall ?????

```

/boot/grub
/boot/abi-2.6.12-9-386
/boot/abi-2.6.12-10-386
/boot/abi-2.6.12-10-686
/boot/abi-2.6.15-23-386
/boot/abi-2.6.15-23-686
/boot/config-2.6.12-9-386
/boot/config-2.6.12-10-386
/boot/config-2.6.12-10-686
/boot/config-2.6.15-23-386
/boot/config-2.6.15-23-686
/boot/initrd.img-2.6.12-9-386
/boot/initrd.img-2.6.12-10-386
/boot/initrd.img-2.6.12-10-686
/boot/initrd.img-2.6.15-23-386
/boot/initrd.img-2.6.15-23-686
/boot/memtest86+.bin
/boot/System.map-2.6.12-9-386
/boot/System.map-2.6.12-10-386
/boot/System.map-2.6.12-10-686
/boot/System.map-2.6.15-23-386
/boot/System.map-2.6.15-23-686
/boot/vmlinuz-2.6.12-9-386
/boot/vmlinuz-2.6.12-10-386
/boot/vmlinuz-2.6.12-10-686
/boot/vmlinuz-2.6.15-23-386
/boot/vmlinuz-2.6.15-23-686

```

---

### Post by angkor on 2006-06-03
I'd use synaptic to uninstall kernels you don't need anymore. If you installed these kernels using apt that is.

Groetjes...;)

---

### Post by Dutch on 2006-06-03
[QUOTE=angkor]I'd use synaptic to uninstall kernels you don't need anymore. If you installed these kernels using apt that is.

Groetjes...;)[/QUOTE]

Oke Synaptis can't find these files.

En nu ? ;-)

---

### Post by angkor on 2006-06-03
[QUOTE=Dutch]Oke Synaptis can't find these files.
[/QUOTE]

Open up a terminal and type 'uname -r'. This is the kernel you're running right now and I assume you want to keep (if everything works that is). I also suggest keeping the default i386 kernel in case you run a different one (for example k7 or 686).

Do search in synaptic for 'linux-image'. You should now see all the available and installed kernels. Right-click the ones you don't need anymore and mark them for complete removal. Make sure you selected the right ones and apply the changes.

---

### Post by Dutch on 2006-06-03
Oke Thanks.
Now it looks like:
```

/boot/grub
/boot/abi-2.6.15-23-386
/boot/abi-2.6.15-23-686
/boot/config-2.6.15-23-386
/boot/config-2.6.15-23-686
/boot/initrd.img-2.6.15-23-386
/boot/initrd.img-2.6.15-23-686
/boot/memtest86+.bin
/boot/System.map-2.6.15-23-386
/boot/System.map-2.6.15-23-686
/boot/vmlinuz-2.6.15-23-386
/boot/vmlinuz-2.6.15-23-686

```

What is that vmlinuz stuf ?
And can I rm the initrd files ?

Thanks.

---

### Post by angkor on 2006-06-03
[QUOTE=Dutch]Oke Thanks.
Now it looks like:
```

/boot/grub
/boot/abi-2.6.15-23-386
/boot/abi-2.6.15-23-686
/boot/config-2.6.15-23-386
/boot/config-2.6.15-23-686
/boot/initrd.img-2.6.15-23-386
/boot/initrd.img-2.6.15-23-686
/boot/memtest86+.bin
/boot/System.map-2.6.15-23-386
/boot/System.map-2.6.15-23-686
/boot/vmlinuz-2.6.15-23-386
/boot/vmlinuz-2.6.15-23-686

```

What is that vmlinuz stuf ?
And can I rm the initrd files ?

Thanks.[/QUOTE]


I _think_ that vmlinuz stuff are the actual kernels...you do *not* want to delete those. :).

Don't delete the initrd files either, you'll render the kernels unbootable. I don't really know what all that stuff does. Maybe somebody else comes along who can explain.

I didn't read all of it but maybe you want to...;)

[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/initrd.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/initrd.html)
[http://www.bellevuelinux.org/vmlinuz.html](http://www.bellevuelinux.org/vmlinuz.html)


Btw, your /boot looks a lot cleaner now.

---

