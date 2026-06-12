---
title: "i/o error."
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by Necrom@ncer on 2008-08-15
I am trying to install ubuntu 8.10 on my IBM thimkpad. Here are the specs:

Pentium m 2.0 ghz
768 mb ram
dvd rom drive installed
floppy bay can be installed

I get buffer I/o error on device sda and buffer i/o error on device sda on the live cd, going to try the alt cd. I am putting ubuntu on because it had XP, but it stopped booting past bios. I can provide more info if needed

---

### Post by spiderbatdad on 2008-08-15
what model? Thinkpads are great with ubuntu, but many models require some boot options. My T30 boot and installs well with the options: lapic pci=routeirq, other thinkpads use other options, you might google ubuntu boot options <your model>

---

### Post by Necrom@ncer on 2008-08-15
I dont know. I looked in the bios, but it is called  type 2366

---

### Post by Necrom@ncer on 2008-08-15
by the way. when the errors get to a certain # it brings up busy box, which does not recognize sudo or other basic debian commands. I typed help, but I cant stop the errors. I will try your command on the live cd.

---

### Post by spiderbatdad on 2008-08-15
That's a T30 i believe. From the startup page, select F6 and delete quiet splash-- from the end of the kernel line. Then type in: lapic pci=routeirq

After the installation, the first boot will require you to do the same, then you need to edit the file /boot/grub/menu.lst```
gksu gedit /boot/grub/menu.lst
```
Make it look like this:
```
# savedefault=true

## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel 2.6.26-5-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26-5-server root=UUID=(#'s) ro **lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.26-5-server
quiet
savedefault
```As highlighted above...your kernel is different, you only want to change what is highlighted.

---

### Post by Necrom@ncer on 2008-08-15
i am trying it now

---

### Post by spiderbatdad on 2008-08-15
standing by.:)

---

### Post by Necrom@ncer on 2008-08-15
i will post again l8r

---

### Post by Necrom@ncer on 2008-08-16
ok, the alternate cd works, but it fails to detect my cd drive during installation, failing the install process. the drive is an IBM dvd rom on a t30 thinkpad.

---

