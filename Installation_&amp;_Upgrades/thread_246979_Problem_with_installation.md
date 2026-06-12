---
title: "Problem with installation"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by azad on 2006-08-30
Hi, I just downloaded the iso of the Desktop edition and burned it in a CD. I inserted the disk in the drive and rebooted the computer. The initial Ubuntu screen came up where there were some options. I chose Install and a new box popped up that said "loading kernel". The progress made up to 9% and then it showed an error box that said:

I/O Error : Kernel error
Reboot

I pressed reboot and tried it again. The same thing happened. The next time I tried "check disk" (or something like that) instead of "install" and the same thing happened again.

I didnt get any errors while downloading or burning the .iso
so what seems to be the problem? should I download the image again or should I try burning the existing image on a new disk?

---

### Post by amo-ej1 on 2006-08-30
you should verify the correctness of your image using the md5 checksum. The ftp server where you got the image from should provide a file MD5SUM

e.g. 
```

b9a5be3a5858ade278d664d41310a4ab  ubuntu-6.06.1-alternate-amd64.iso
6cb8582aa5615ed4616165743a0868d7  ubuntu-6.06.1-alternate-i386.iso
0b5b3df02da3d9ed6f4ac482cf541f04  ubuntu-6.06.1-alternate-powerpc.iso
50e3912c555f98f7bca56b2a0200b205  ubuntu-6.06.1-desktop-amd64.iso
fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
502911770ad173dbe82c698379ed7d11  ubuntu-6.06.1-desktop-powerpc.iso
8254b0f3696ed17c52a2cb59c9ebd2cc  ubuntu-6.06.1-server-amd64.iso
5ad76d8b380ab5be713e5daa9ea84475  ubuntu-6.06.1-server-i386.iso
6d1c3b5cb41661365b3db5cf12bb2836  ubuntu-6.06.1-server-powerpc.iso
2ccc1ec608040e6aac8913a016c31bed  ubuntu-6.06.1-server-sparc.iso

```

Now you should run something like *md5sum my_image_iso* and compare if the result of the checksum equals to the one on the MD5SUMS file of your ftp/www/whtvr server. If this number matches your image is downloaded correctly and all you need to do is create a new cd if this number doesn't match you'll have to download it again.

---

