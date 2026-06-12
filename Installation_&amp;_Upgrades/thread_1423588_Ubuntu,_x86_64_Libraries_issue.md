---
title: "Ubuntu, x86_64 Libraries issue?"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by pbureau on 2010-03-06
so here I was installing my first program after a fresh install of Ubuntu 910 x86_64 DVD

I run the program and I get 

/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64 Failed to load module: /usr/lib/gio/modules/libgiogconf.so

/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64 Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so

/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64 Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

/usr/lib/gio/modules/libgiofam.so: wrong ELF class: ELFCLASS64 Failed to load module: /usr/lib/gio/modules/libgiofam.so

So I investigated and discovered

readelf -h /usr/lib/gio/modules/libgiogconf.so
ELF Header:
Magic: 7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00
Class: ELF64

readelf -h /usr/lib/gio/modules/libgioremote-volume-monitor.so
ELF Header:
Magic: 7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00
Class: ELF64

readelf -h /usr/lib/gio/modules/libgvfsdbus.so
ELF Header:
Magic: 7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00
Class: ELF64

readelf -h /usr/lib/gio/modules/libgiofam.so
ELF Header:
Magic: 7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00
Class: ELF64

Now the question I have is why is there a 
/usr/lib with 64bits libs when we have /usr/lib64 for 64 bits and /usr/lib32 for 32 bits.. isnt it the default to always have 32 bits in the /usr/lib directory.??

if not then this will be an issue with many 32 bits apps.
please advise.

---

