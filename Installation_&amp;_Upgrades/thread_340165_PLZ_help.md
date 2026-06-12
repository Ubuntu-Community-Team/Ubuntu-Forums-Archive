---
title: "PLZ help"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by lllooonnniiieee on 2007-01-16
is there a way to install ubuntu without a disc just like a program?

---

### Post by invalid on 2007-01-16
Are you looking to run it through an emulator from within Windows?

---

### Post by meng on 2007-01-16
[http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)

---

### Post by x1a4 on 2007-01-16
Not exactly like a program, but you can install the ISO as if it was on a CD in the drive bay and use it or boot to it.  Simply mount the ISO image as a filesystem via your loopback device, then modify your boot-loader to include the iso filesystem if you want to boot to it.  

Here's how you can mount the iso image.  

As the superuser: 

1) Create a mount point, in this example it's /mnt/xubuntu.  This is where your DVD will be located.  

```
mkdir -p /mnt/xubuntu
```

2) Mount the ISO image. 

```
mount -o loop -t iso9660 /path/to/xubuntu.iso /mnt/xubuntu
```

( **IMPORTANT** Don't use this post as your sole guide as I haven't done this in a while and when I did it was on a different distro.  The first part (mounting the ISO) is a no brainer and should work, booting to it is a different matter and you should research things more before doing anything.  )

Now you have to modify your boot loader.  If you're using GRUB, here's how.

As the superuser: 

1) Using your favourite text editor edit the file

*/boot/grub/menu.lst*

to include the following (modify according to your system's specifications): 

title      XUbuntu ISO (or whatever else you want)
root     (hd0,0)
kernel /mnt/xubuntu/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro
initrd   /mnt/xubuntu/boot/initrd.img-2.6.17-10-generic
boot

The above example assumes the following: 
a) You've mounted the ISO image on the first partition of the first drive (hd0=hard drive 0, 0=partition 0, hence hd0,0)
b) The kernel file name is vmlinuz-2.6.17-10-generic
c) The kernel image file name is initrd.img-2.6.17-10-generic


2) Update GRUB

```
update-grub
```

I've a feeling I'm missing something here but can't, for the life of me, remember what.  So anybody who knows more than I feel free to chime in here.


Is it possible to run the mounted iso in Xnest, as if you were booting to it?

---

