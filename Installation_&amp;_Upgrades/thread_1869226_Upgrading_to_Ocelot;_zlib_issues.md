---
title: "Upgrading to Ocelot; zlib issues"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by nlucaroni on 2011-10-25
I have a project that I am working on that uses zlib and after this upgrade it cannot compile against the library. The application cannot find any of the functions provided by the library**.

Running, [FONT="Courier New"]ld -verbose -lz[/FONT] I obtain the following (along with the internal linker script), 

```
attempt to open /usr/x86_64-linux-gnu/lib64/libz.so failed
attempt to open /usr/x86_64-linux-gnu/lib64/libz.a failed
attempt to open /usr/local/lib/x86_64-linux-gnu/libz.so failed
attempt to open /usr/local/lib/x86_64-linux-gnu/libz.a failed
attempt to open /usr/local/lib64/libz.so failed
attempt to open /usr/local/lib64/libz.a failed
attempt to open /lib/x86_64-linux-gnu/libz.so failed
attempt to open /lib/x86_64-linux-gnu/libz.a failed
attempt to open /lib64/libz.so failed
attempt to open /lib64/libz.a failed
attempt to open /usr/lib/x86_64-linux-gnu/libz.so succeeded
-lz (/usr/lib/x86_64-linux-gnu/libz.so)
libc.so.6 needed by /usr/lib/x86_64-linux-gnu/libz.so
found libc.so.6 at /lib/x86_64-linux-gnu/libc.so.6
ld-linux-x86-64.so.2 needed by /lib/x86_64-linux-gnu/libc.so.6
found ld-linux-x86-64.so.2 at /lib/x86_64-linux-gnu/ld-linux-x86-64.so.2
ld: warning: cannot find entry symbol _start; not setting start address

```

Obviously I'm on a 64bit system and Ubuntu 11.10. 

** the functions it cannot find are gzerror, gzclose, zlibVersion, gzopen, gzsetparams, gzread, gzwrite, gzwrite, gzeof, gzgets, gzputc, gzgetc, gzrewind, gzeof, gzclose, gzflush, gzseek, gzseek, gztell, compress2, uncompress. These can all be found in my zlib.h or zconf.h header files.

---

### Post by nlucaroni on 2011-10-25
I'm really not sure about the problem still. Switching to gcc-4.4 everything is fine. 


I also had to create a symbolic link from libgfortran.so.3 to libgfortran.so.

I didn't directly see that this link was present before the upgrade, but I can only assume it was since it fixed the issue and makes sense. Is there a known issue with the alternatives set-up in upgrading Ubuntu 11.10?

---

