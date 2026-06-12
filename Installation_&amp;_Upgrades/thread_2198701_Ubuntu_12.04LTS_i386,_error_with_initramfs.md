---
title: "Ubuntu 12.04LTS i386, error with initramfs"
date: 2014-01-10
forum: Installation &amp; Upgrades
---

### Post by stschulze on 2014-01-10
hi,

i have some trouble with initrams:

```

root@ubuntu:~# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.2.0-58-generic
cp: »/usr/lib/klibc/bin/cpio“ und »/tmp/mkinitramfs_WwCtzF/bin/cpio“ sind die gleiche Datei
cp: »/usr/lib/klibc/bin/dd“ und »/tmp/mkinitramfs_WwCtzF/bin/dd“ sind die gleiche Datei
cp: »/usr/lib/klibc/bin/dmesg“ und »/tmp/mkinitramfs_WwCtzF/bin/dmesg“ sind die gleiche Datei
cp: »/usr/lib/klibc/bin/fstype“ und »/tmp/mkinitramfs_WwCtzF/bin/fstype“ sind die gleiche Datei
cp: »/usr/lib/klibc/bin/halt“ und »/tmp/mkinitramfs_WwCtzF/bin/halt“ sind die gleiche Datei
cp: »/usr/lib/klibc/bin/insmod“ und »/tmp/mkinitramfs_WwCtzF/bin/insmod“ sind die gleiche Datei
cp: »/usr/lib/klibc/bin/ipconfig“ und »/tmp/mkinitramfs_WwCtzF/bin/ipconfig“ sind die gleiche Datei
cp: »/usr/lib/klibc/bin/losetup“ und »/tmp/mkinitramfs_WwCtzF/bin/losetup“ sind die gleiche Datei
cp: »/usr/lib/klibc/bin/nfsmount“ und »/tmp/mkinitramfs_WwCtzF/bin/nfsmount“ sind die gleiche Datei
cp: »/usr/lib/klibc/bin/pivot_root“ und »/tmp/mkinitramfs_WwCtzF/bin/pivot_root“ sind die gleiche Datei
cp: »/usr/lib/klibc/bin/poweroff“ und »/tmp/mkinitramfs_WwCtzF/bin/poweroff“ sind die gleiche Datei
cp: »/usr/lib/klibc/bin/reboot“ und »/tmp/mkinitramfs_WwCtzF/bin/reboot“ sind die gleiche Datei
cp: »/usr/lib/klibc/bin/resume“ und »/tmp/mkinitramfs_WwCtzF/bin/resume“ sind die gleiche Datei
cp: »/usr/lib/klibc/bin/run-init“ und »/tmp/mkinitramfs_WwCtzF/bin/run-init“ sind die gleiche Datei
cp: »/lib/klibc-LZ1cv1NoEVO2ugnvqTw3e4qPc8Y.so“ und »/tmp/mkinitramfs_WwCtzF/lib/klibc-LZ1cv1NoEVO2ugnvqTw3e4qPc8Y.so“ sind die gleiche Datei
root@ubuntu:~# 

```

three kernes are installed:
```

root@ubuntu:~# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.3.7-030307-generic
Found initrd image: /boot/initrd.img-3.3.7-030307-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:~# 

```

how can i solve the problem ?

---

### Post by Bashing-om on 2014-01-10
stschulze; Hello ,

This is an English speaking forum ( I am handicapped in that respect), please translate to English:
> 
sind die gleiche Datei


This might be a big problem to resolve:
> 
Found linux image: /boot/vmlinuz-3.3.7-[color=red]030307[/color]-generic

As that filename is not an accepted format.
If we were to manually remove that file - behind the package managers back - I do not know what consequences this would entail. Certainly will break the system and require us to manually intervene to resolve the situation and restore the package manager !
Will await others advise, perhaps synaptic can cope with removal of this kernel image in an acceptable manner ? 

I know of no safe way to deal with that file with such a descriptor.

[INDENT][INDENT]break the system and then
[INDENT][INDENT][INDENT]try and fix it !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hansdown on 2014-01-10
Hi  Bashing-om.

A rough translation is,

> one and the same, the same as, etc.

---

### Post by Bashing-om on 2014-01-10
hansdown; Hey ,

I do not know what to make of that copy output -> one and the same.

Hang on and let's see what others advise. 

I plan on running "update-initramfs -u" on my system -- when it is in a stable situation and after I have updated grub .
I have a small intermittent problem mounting my root directory that I hope that updating initramfs will resolve.
Will compare my output to yours.

[INDENT][INDENT]hope'n to help
[/INDENT][/INDENT]

---

### Post by hansdown on 2014-01-10
I know, that you will shine,  Bashing-om.

Just try'in to shed some light.

---

### Post by hansdown on 2014-01-10
There is a security notice.

[https://www.net-security.org/advisory.php?id=17128](https://www.net-security.org/advisory.php?id=17128)

---

### Post by Bashing-om on 2014-01-12
@ Hansdown, Thanks -> I will give it a whirl !

stschulze; Hello ;

Lacking better advisement, I guess it is on me to deal with this,

Let's roll our sleeves up and go to work. Let's firstly see if we can make this as simple as possible and remain within the sphere of ubuntu's package management system.

show me the output of terminal code:
```

ls -la /usr/src

```
To get a better idea of what we are working with.

Background: I just ran "sudo update-initramfs -u" on my system, it ran clean and I feel better .

Work'n to make your system
[INDENT][INDENT][INDENT]do the same
[/INDENT][/INDENT][/INDENT]

---

