---
title: "Karmic (wubi install) won't boot after dist-upgrade"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by KubuntuKilledMe on 2010-01-11
Hi, i have Karmic installed with Wubi inside a Vista NTFS filesystem. 

Yesterday i did an apt-get dist-upgrade and Karmic never booted again. It won't even show the grub kernel list, it just shows some really quick text that vanishes before i can even figure out what it is and then drops to some sort of grub shell and then i can't figure out what to do.

I could boot a livecd and mount my karmic install and everything seems fine, the filesystem is clean and all that. But how do i fix it so it can boot again? 

Does anyone here know wtf happened? Was there a bad upgrade or something?

Thanks a lot for all help.

---

### Post by KubuntuKilledMe on 2010-01-12
[SIZE="1"]*bump*[/SIZE]

---

### Post by Dale61 on 2010-01-12
It sounds like the same problem I encountered a few weeks back.

Try this;

```
sh:grub linux /boot /vmlinuz-2.6.31-16-generic root=/dev/sda2 loop=ubuntu/disks/root.disk.ro
```

[ENTER]

```
sh:grub initrd /boot/initrd.img-2.6.31-16-generic
```

[ENTER]

```
sh:grub boot
```

If that works and brings your Ubuntu back, go into a terminal and 

```
sudo update-grub2
```

It worked for me on more than one instance.

---

### Post by dzon65 on 2010-01-12
Kernel update?Maybe something like this?:GNU GRUB version.....minimal bash-like line editing is supported.......? If so,it's most probably wubi-related and there are many threads on the forum.

---

