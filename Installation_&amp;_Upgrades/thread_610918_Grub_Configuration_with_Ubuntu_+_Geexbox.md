---
title: "Grub Configuration with Ubuntu + Geexbox"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by don_emilio_juan on 2007-11-12
Hi,

maybe it's not the 100% right place for this post, but I'll give it try because no one is responding to this in the geexbox forum and it's probably anyway a general linux / grub question:

I've been installing geexbox 1.1 on a seperate partition (Ext3). I am running Ubuntu Gutsy as main system and it already had Grub installed, so I did not choose to install grub again. However I have to edit the menu.lst and add an entry for geexbox in order to start geexbox.

My Ubuntu Gutsy Entry looks like this:
```

title   Ubuntu 7.10, kernel 2.6.22-14-generic
root   (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=1b95f759-0aa0-4005-9c53-3d68eefd1e77 ro quiet splash
initrd   /boot/initrd.img-2.6.22-14-generic
quiet
```

As I am a complete beginner I have no idea how to do this, the only thing I manage is to open the menu.lst with root rights, to add the title for the entry but for the rest I have no idea:

```
title		Geexbox
root   ???
kernel   ???
initrd   ???
quiet
```

Geexbox is installed in the partiton /dev/sda3, while ubuntu is in /dev/sda1. Can anyone help with that and the given information?

Thank you very much.
Best regards
Juan

---

### Post by mikewhatever on 2007-11-12
Load Ubuntu and mount /dev/sda3. In the terminal, type the following and get write down the outputs:
> ls /boot
ls -l /dev/disk/by-uuid/  

Now add the values to grub section for geexbox:
> title		Geexbox
root  (hd0,2)
kernel   /boot/vmlinuz- .....
initrd   /boot/initrd.img- .....
quiet

---

### Post by don_emilio_juan on 2007-11-12
Hi,

I mounted /dev/sda3:

```
mount /dev/sda3 /mnt/sda3
```

Then I did:

```
juan@juan-laptop:~$ ls /boot
abi-2.6.22-14-generic         initrd.img-2.6.22-14-generic.bak
config-2.6.22-14-generic      memtest86+.bin
grub                          System.map-2.6.22-14-generic
initrd.img-2.6.22-14-generic  vmlinuz-2.6.22-14-generic
juan@juan-laptop:~$ ls -l /dev/disk/by-uuid/
insgesamt 0
lrwxrwxrwx 1 root root 10 2007-11-12 21:39 006299ae-3c5d-4c63-933c-c2b32c1cf517 -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-11-12 21:39 1b95f759-0aa0-4005-9c53-3d68eefd1e77 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-11-12 21:39 c19d2844-0e6f-41fc-8d28-15f872a05915 -> ../../sda5
juan@juan-laptop:~$ 

```

With this information I entered the menu.lst:

```
title Geexbox
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=006299ae-3c5d-4c63-933c-c2b32c1cf517
initrd /boot/initrd.img-2.6.22-14-generic
quiet
```

Well, something must be wrong - still. Because it does not work. When trying to boot Geexbox it doesn't find anything to boot... Can someone help me with that? Thank you very much. Best regards

---

### Post by mikewhatever on 2007-11-14
Could you post the output of **sudo fdisk -l**.

---

### Post by meierfra on 2007-11-14
> ls /boot  

This will give you the  kernels for gutsy.

You need to use:

```
ls /mnt/sda3/boot
```

---

