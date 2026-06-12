---
title: "Error with compiling wlan-driver"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by kryss on 2005-03-20
Hello,
I'm new to Ubuntu, but not to Linux. I've been using Linux on Desktop for 2 years with Gentoo. Ubuntu seems to be a great distribution, so I'll give it a try  \\:D/ 

The installation of ubuntu was easy, but I can't get my USB-WLAN (Netgear MA101) to work.

I've installed the driver source code with
```
# apt-get install at76c503a-source
```

and afterwards tried to compile with
```
cd /usr/src/modules/at76c503a/
# make
```

Now I get this error-message (sorry for the german wording - file or directory is missing)
```

mkdir -p .tmp_versions
cp /lib/modules/2.6.10-5-386/build/.tmp_versions/*.mod /usr/src/modules/at76c503a/.tmp_versions
cp: Aufruf von stat für „/lib/modules/2.6.10-5-386/build/.tmp_versions/*.mod“ nicht möglich: Datei oder Verzeichnis nicht gefunden
make: [modules] Fehler 1 (ignoriert)
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/usr/src/modules/at76c503a MODVERDIR=/usr/src/modules/at76c503a/.tmp_versions \
EXTRA_CFLAGS="" modules
make: *** /lib/modules/2.6.10-5-386/build: Datei oder Verzeichnis nicht gefunden.  Schluss.
make: *** [modules] Fehler 2

```

It seems to be something is missing for compilation. I've searched in the forum... and installed "build-essentials" ... but without any success  ](*,) 

Can anyone help me?
Thanks, Christian

---

### Post by kryss on 2005-03-20
ok, I get it for my own  \\:D/ 

I just had to
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Afterwards it does work!

Christian

---

### Post by kryss on 2005-03-21
as mentioned above I've solved the "make"-problem. Afterwards I did a "make install" - without an error.

But there are no modules for my WLAN-adapter in /lib/modules/[kernel-version]... and below.

Also at "make install" I couldn't see any "cp"-command moving the modules from local directory to /lib/modules/...

Did I miss something?

Thanks,
Christian

---

### Post by kryss on 2005-03-22
The error occurs using the driver-package with apt-get
```
apt-get install at76c503a-source
```
Now I'm using the nightly cvs-build from [http://at76c503a.berlios.de/](http://at76c503a.berlios.de/). It is working like a charm!

It seems to be that the old package doesn't support kernel 2.6...

Now everything is working under Ubuntu  :smile: 
Christian

---

