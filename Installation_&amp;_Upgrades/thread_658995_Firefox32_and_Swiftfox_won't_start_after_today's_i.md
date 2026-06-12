---
title: "Firefox32 and Swiftfox won't start after today's ia32 upgrade"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by martinrandau on 2008-01-05
This are the error messages I get. I run Hardy Heron 64-bit, and I got the errors after today's upgrade. I've tried to reinstall the older version of ia32 but I'm not totally sure how to do that.

```
martin@znote3415:~$ firefox32 
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
esd: no process killed
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
/usr/local/firefox32/firefox-bin: error while loading shared libraries: libselinux.so.1: cannot open shared object file: No such file or directory
```
```

martin@znote3415:~$ swiftfox 
/opt/swiftfox/swiftfox-bin: error while loading shared libraries: libpixman-1.so.0: cannot open shared object file: No such file or director
```

:guitar:

---

### Post by fain on 2008-01-05
I get  "object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored." but firefox32 still starts.

---

### Post by hey_ygbsm on 2008-01-05
Same problem here...
Code:
```
pete@pete-desktop:~$ swiftfox/usr/lib/swiftfox/swiftfox-bin: error while loading shared libraries: libpixman-1.so.0: cannot open shared object file: No such file or directory
```

---

### Post by akwatve on 2008-01-31
I too see these error messages on terminal but firefox starts and works (apprently) flawlessly....

> (Thu Jan 31 08:17:44)~/Desktop> firefox32
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
esd: no process killed
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(firefox-bin:6022): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

(firefox-bin:6022): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64


---

