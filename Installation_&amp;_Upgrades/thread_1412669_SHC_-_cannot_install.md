---
title: "SHC - cannot install"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by d3v1150m471c on 2010-02-21
I'm trying to install shc-3.8.6. and this is what I get:

```

*** &#65533;Do you want to install shc?
*** Please try...  make install
d3v11@d3v11m4ch1n3:~/Downloads/shc-3.8.6$ make install
*** Installing shc and shc.1 on /usr/local
*** &#65533;Do you want to continue? yes
install -c -s shc /usr/local/bin/
install: cannot remove `/usr/local/bin/shc': Permission denied
make: *** [install] Error 1
d3v11@d3v11m4ch1n3:~/Downloads/shc-3.8.6$ sudo make install
[sudo] password for d3v11:
*** Installing shc and shc.1 on /usr/local
*** &#65533;Do you want to continue? yes
install -c -s shc /usr/local/bin/
install -c -m 644 shc.1 /usr/local/man/man1/
install: target `/usr/local/man/man1/' is not a directory: No such file or directory
make: *** [install] Error 1
d3v11@d3v11m4ch1n3:~/Downloads/shc-3.8.6$ sudo make install
*** Installing shc and shc.1 on /usr/local
*** &#65533;Do you want to continue? install
make: *** [install] Error 1

```

What am I missing?

---

### Post by d3v1150m471c on 2010-02-21
Update:

```

cd ~/Downloads/shc-3.8.6. && ./shc -f /path/to/script

```

Fixed...

---

