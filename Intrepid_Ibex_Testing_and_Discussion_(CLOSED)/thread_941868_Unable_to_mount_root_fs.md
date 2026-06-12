---
title: "Unable to mount root fs"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by OsamaK on 2008-10-08
I installed Ubuntu 8.10 beta on my desktop computer using the LiveCD.

I had no errors in this version (note that I tried installing 7.10, 8.04 and 8.04.1 months ago in the same partition, All of them has been failed while copying files) and the LiveCD worked very well.

When I restarted the computer for first time, and when I tried to run Ubuntu 8.10 I had the problem:
> 
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)


My Linux version is kernel 2.6.24-12-generic.

---

### Post by OsamaK on 2008-10-09
To go up!

---

### Post by vniksic on 2008-10-17
I just upgraded to Intrepid Ibex, and had the exact same problem. Turns out the script that updated the /boot/grub/menu.lst didn't include the initrd line for some insane reason. So, in menu.lst I had:
```
title           Ubuntu intrepid (development branch), kernel 2.6.27-7-generic
root            (hd0,4)
kernel          /vmlinuz-2.6.27-7-generic root=UUID=78fc7c6b-7c44-4ec5-8ca0-350a547ba21c ro quiet splash
quiet
```


No initrd line!!! Just add the initrd line so it looks like this:

```
title           Ubuntu intrepid (development branch), kernel 2.6.27-7-generic
root            (hd0,4)
kernel          /vmlinuz-2.6.27-7-generic root=UUID=78fc7c6b-7c44-4ec5-8ca0-350a547ba21c ro quiet splash
**initrd          /initrd.img-2.6.27-7-generic**
quiet
```

and it should work like a charm. Don't forget to change your UUID to suit you. You can find out what the UUID of a filesystem is with the vol_id command. For example "vol_id /dev/sda1". You can always discard the UUID, and just use root=/dev/sda**x**.

---

