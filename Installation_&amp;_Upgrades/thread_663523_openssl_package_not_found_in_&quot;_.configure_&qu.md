---
title: "openssl package not found in &quot; ./configure &quot;"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by SandyKhan on 2008-01-10
Please guide me how to get openssl package?

The following are the last a few lines of  ./configure output.


checking for SSL... configure: error: Package requirements (openssl >= 0.9.7) were not met:

No package 'openssl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SSL_CFLAGS
and SSL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by PmDematagoda on 2008-01-10
Try:-
```
sudo apt-get install openssl
```

---

### Post by SandyKhan on 2008-01-10
I have run the command, and the following output appears:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But,  ./configure still shows the same error and make command still says this:

make: *** No targets specified and no makefile found.  Stop.

---

### Post by PmDematagoda on 2008-01-10
It would make things more easier if you could post what application you are trying to compile.

---

### Post by andrew.46 on 2008-03-01
Hi,

 If you are compiling I suspect that you may also require the openssl dev file. To find the appropriate one for your Ubuntu distro try:

```
$ apt-cache search openssl | grep dev
```

and then download and install the suggested dev file + compile again.

      Andrew

---

