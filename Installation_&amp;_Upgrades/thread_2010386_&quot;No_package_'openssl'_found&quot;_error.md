---
title: "&quot;No package 'openssl' found&quot; error"
date: 2012-06-25
forum: Installation &amp; Upgrades
---

### Post by LutraMan on 2012-06-25
Hi all,
I'm trying to install ruTorrent by following this wiki: [http://code.google.com/p/rutorrent/wiki/MainInstall](http://code.google.com/p/rutorrent/wiki/MainInstall)
All of the dependencies are already installed on my system including openssl (I've checked that using synaptic and apt-get)
everything went smoothly until I've reached the 6th line in the rTorrent installation "./configure". All of the output is 'ok' or 'yes' until the following:
```

checking for OPENSSL... configure: error: Package requirements (openssl) were not met:

No package 'openssl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables OPENSSL_CFLAGS
and OPENSSL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

this is the output I'm getting when running "sudo apt-get install openssl":
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssl is already the newest version.
The following packages were automatically installed and are no longer required:
  libapache2-mod-scgi libxmlrpc-c3-0 libtorrent11
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

and this is my PKG_CONFIG_PATH: (which I've exported after seeing it fixed a similar problem on another forum post)
```
/usr/local/lib/pkgconfig
```

all of the above attempts did not achieve anything, and the output from the "./configure" is still the same.

Any advice will be appreciated.

---

### Post by LutraMan on 2012-06-27
Hey I just posted this,
And this is crazy,
but bump, maybe?

---

### Post by anhhh on 2012-11-20
> **LutraMan said:**
> Hi all,
I'm trying to install ruTorrent by following this wiki: [http://code.google.com/p/rutorrent/wiki/MainInstall](http://code.google.com/p/rutorrent/wiki/MainInstall)
All of the dependencies are already installed on my system including openssl (I've checked that using synaptic and apt-get)
everything went smoothly until I've reached the 6th line in the rTorrent installation "./configure". All of the output is 'ok' or 'yes' until the following:
```

checking for OPENSSL... configure: error: Package requirements (openssl) were not met:

No package 'openssl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables OPENSSL_CFLAGS
and OPENSSL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```this is the output I'm getting when running "sudo apt-get install openssl":
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssl is already the newest version.
The following packages were automatically installed and are no longer required:
  libapache2-mod-scgi libxmlrpc-c3-0 libtorrent11
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```and this is my PKG_CONFIG_PATH: (which I've exported after seeing it fixed a similar problem on another forum post)
```
/usr/local/lib/pkgconfig
```all of the above attempts did not achieve anything, and the output from the "./configure" is still the same.

Any advice will be appreciated.

Just
```
sudo apt-get install libssl-dev
```

---

### Post by LutraMan on 2012-11-20
I've actually already solved it, with the following
```
sudo apt-get install openssl-devel
```

which if I remember correctly also installed libssl-dev as a dependency.

Thank you anyway.

---

