---
title: "Problems accesing block devices out of chroot"
date: 2008-09-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MALEADt on 2008-09-11
Hi all,

I'm experiencing a problem since I'm using Intrepid. On hardy, I could without any problem generate a toolchain with buildroot, chroot into it, and use it's block devices to do some stuff (/dev/zero, /dev/loop to mount images, ...)

But since hardy, I get with exactly the same toolchain (I even build a new one, so it's no permissions problem at the toolchain's side) errors while accesing block devices:
```
bash-3.2# dd if=/dev/zero bs=620 count=1 >> filesystem.img
opening `/dev/zero': Permission denied

bash-3.2# mount filesystem.img image/ -o loop -t ext2
mount: no permission to look at /dev/loop#
```

I have entered the chroot (obviousely) using sudo. Have any permissions on block devices changed, or what could cause this problem?

maleadt

---

