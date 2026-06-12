---
title: "Upgrade broke dpkg: gdbus links to libffi.so.7"
date: 2023-03-20
forum: Installation &amp; Upgrades
---

### Post by jassop on 2023-03-20
So, I did an upgrade from 20.04 to 22.04, and the upgrade proceduce seemed to go well. Afterwards running apt, it said I had some auto-installed things I can get rid if, so sure I''ll do that. Then found some errors. 

The main one seems to be when running apt, that uses dpkg, which uses /usr/bin/gdbus, which is linked to libffi.so.7, which is no longer installed and the whole thing fails with errors. It seems like libffi.so.7 has been superseded by libffi.so.8, and so reinstalling gdbus would fix this, but apt being broken means I can can't reload it. 


```
/usr/bin/gdbus: error while loading shared libraries: libffi.so.7: cannot open shared object file: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
file /usr/bin/gdbus
/usr/bin/gdbus: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=cf76eaa2f1a44e3c7b3904292b2b5548edd86633, for GNU/Linux 3.2.0, stripped
```

I have these versions installed at the moment. I'm hoping they are the right ones? 
dpkg:
  Installed: 1.21.1ubuntu2.1
libglib2.0-bin:
  Installed: 2.72.4-0ubuntu1

Is there a way to solve this? Can I manually relink gdbus to libffi.so.8? Or is there another way to solve this?

Thanks!

---

### Post by #&amp;thj^% on 2023-03-20
Please also include:
```
sudo apt update
### and
sudo apt upgrade
```

---

### Post by Impavidus on 2023-03-20
You've got the right version of libglib2.0-bin, but the wrong version of /usr/bin/gdbus:```
$ ldd /usr/bin/gdbus
    linux-vdso.so.1 (0x00007ffeb11cf000)
    libgio-2.0.so.0 => /lib/x86_64-linux-gnu/libgio-2.0.so.0 (0x00007f8b1d402000)
    libgmodule-2.0.so.0 => /lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007f8b1d3fb000)
    libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007f8b1d2c1000)
    libgobject-2.0.so.0 => /lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007f8b1d261000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f8b1d039000)
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f8b1d01d000)
    libmount.so.1 => /lib/x86_64-linux-gnu/libmount.so.1 (0x00007f8b1cfd7000)
    libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007f8b1cfab000)
    libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f8b1cf35000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f8b1ce4e000)
    libffi.so.8 => /lib/x86_64-linux-gnu/libffi.so.8 (0x00007f8b1ce41000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f8b1d5fe000)
    libblkid.so.1 => /lib/x86_64-linux-gnu/libblkid.so.1 (0x00007f8b1ce08000)
    libpcre2-8.so.0 => /lib/x86_64-linux-gnu/libpcre2-8.so.0 (0x00007f8b1cd71000)
$ apt-cache policy libglib2.0-bin
libglib2.0-bin:
  Geïnstalleerd: 2.72.4-0ubuntu1
  Kandidaat:     2.72.4-0ubuntu1
  Versietabel:
 *** 2.72.4-0ubuntu1 500
        500 http://nl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.72.1-1 500
        500 http://nl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
$ file /usr/bin/gdbus
/usr/bin/gdbus: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=d55ab1a0d7201021fda92b38848fc5a661120311, for GNU/Linux 3.2.0, stripped
```Re-downloading and re-installing libglib2.0-bin should fix that, but if you can't run dpkg due to this error, that's a bit harder. You could try from a live disk, chroot into your installed system and use the package management tools of the live disk to fix this.

One wonders how this could go wrong and if there're more packages not correctly upgraded. Killed upgrade process? Broken harddrive? Faulty mirror? I've encountered all of them in my time on Ubuntuforums.

---

