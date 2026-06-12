---
title: "compile python 2.4 and 2.6 on 12.04 x86_64"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by appociappo on 2012-05-09
I want to share how i compiled from source python versions 2.4 and 2.6 on precise pangolin. These versions of python where discarded on this ubuntu release, they can be compiled from source with just few quirks.

I am not completely sure about the required libs since i tried various combinations before looking at the actual code, so any comments on those are well accepted :)

**[SIZE="3"]python 2.6.8[/SIZE]**
required libs:
```
apt-get build-dep python
```

python source download:
```
wget [http://www.python.org/ftp/python/2.6.8/Python-2.6.8.tar.bz2](http://www.python.org/ftp/python/2.6.8/Python-2.6.8.tar.bz2)
```

exctract
```
tar xjvf Python-2.6.8.tar.bz2
cd Python-2.6.8
```

create a text file setup_py.patch with any preferred text editor (vim anyone?) with the following content:
```
--- Python-2.6.8/setup.py       2012-04-10 17:32:11.000000000 +0200
+++ Python-2.6.8_ok/setup.py    2012-05-08 12:42:23.893052724 +0200
@@ -410,6 +410,7 @@
         lib_dirs = self.compiler.library_dirs + [
             '/lib64', '/usr/lib64',
             '/lib', '/usr/lib',
+            '/usr/lib/x86_64-linux-gnu'
             ]
         inc_dirs = self.compiler.include_dirs + ['/usr/include']
         exts = []

```
apply the patch:
```
patch Modules/_ssl.c < _ssl.patch
```

create a text file ssl.patch with this content:
```
--- Modules/_ssl.c      2012-04-10 17:32:09.000000000 +0200
+++ Modules/_ssl.c      2012-05-08 17:50:46.929523605 +0200
@@ -302,8 +302,8 @@
         self->ctx = SSL_CTX_new(TLSv1_method()); /* Set up context */
     else if (proto_version == PY_SSL_VERSION_SSL3)
         self->ctx = SSL_CTX_new(SSLv3_method()); /* Set up context */
-    else if (proto_version == PY_SSL_VERSION_SSL2)
-        self->ctx = SSL_CTX_new(SSLv2_method()); /* Set up context */
+/*    else if (proto_version == PY_SSL_VERSION_SSL2)
+        self->ctx = SSL_CTX_new(SSLv2_method());*/ /* Set up context */
     else if (proto_version == PY_SSL_VERSION_SSL23)
         self->ctx = SSL_CTX_new(SSLv23_method()); /* Set up context */
     PySSL_END_ALLOW_THREADS
@@ -1688,8 +1688,8 @@
                             PY_SSL_CERT_REQUIRED);

     /* protocol versions */
-    PyModule_AddIntConstant(m, "PROTOCOL_SSLv2",
-                            PY_SSL_VERSION_SSL2);
+/*    PyModule_AddIntConstant(m, "PROTOCOL_SSLv2",
+                            PY_SSL_VERSION_SSL2);*/
     PyModule_AddIntConstant(m, "PROTOCOL_SSLv3",
                             PY_SSL_VERSION_SSL3);
     PyModule_AddIntConstant(m, "PROTOCOL_SSLv23",
```

apply the patch:
```
patch Modules/_ssl.c < _ssl.patch
```


launch the ./configure command with the following syntax:
```
env CPPFLAGS="-I/usr/lib/x86_64-linux-gnu" LDFLAGS="-L/usr/include/x86_64-linux-gnu"  ./configure --prefix=/opt/python2.6

```

be careful: the previous command will set the installation directory on /opt/python2.6. If you want to change that directory you have to change the --prefix parameter

actual compilation:
```
make
```

another patch file (ssl.py) to create:
```
--- Lib/ssl.py  2012-04-10 17:32:06.000000000 +0200
+++ Lib/ssl.py       2012-05-08 17:51:34.029522977 +0200
@@ -61,7 +61,7 @@

 from _ssl import SSLError
 from _ssl import CERT_NONE, CERT_OPTIONAL, CERT_REQUIRED
-from _ssl import PROTOCOL_SSLv2, PROTOCOL_SSLv3, PROTOCOL_SSLv23, PROTOCOL_TLSv1
+from _ssl import PROTOCOL_SSLv3, PROTOCOL_SSLv23, PROTOCOL_TLSv1
 from _ssl import RAND_status, RAND_egd, RAND_add
 from _ssl import \
      SSL_ERROR_ZERO_RETURN, \

```

apply the patch:
```
patch Lib/ssl.py < ssl_py.patch
```

system installation:
```
make install
```



[SIZE="3"]**Python 2.4.6**[/SIZE]
libs required:
```
apt-get build-dep python
```

python 2.4 source download:
```
wget [http://www.python.org/ftp/python/2.4.6/Python-2.4.6.tar.bz2](http://www.python.org/ftp/python/2.4.6/Python-2.4.6.tar.bz2)
```

```

tar xvjf Python-2.4.6.tar.bz2
cd Python-2.4.6
```

create a patch file setup_py.patch:
```
--- setup.py    2006-10-08 19:41:25.000000000 +0200
+++ setup.py        2012-05-08 14:02:14.325174357 +0200
@@ -269,6 +269,7 @@
         lib_dirs = self.compiler.library_dirs + [
             '/lib64', '/usr/lib64',
             '/lib', '/usr/lib',
+           '/usr/lib/x86_64-linux-gnu'
             ]
         inc_dirs = self.compiler.include_dirs + ['/usr/include']
         exts = []
@@ -496,7 +497,8 @@
                 ssl_incs += krb5_h
         ssl_libs = find_library_file(self.compiler, 'ssl',lib_dirs,
                                      ['/usr/local/ssl/lib',
-                                      '/usr/contrib/ssl/lib/'
+                                      '/usr/contrib/ssl/lib/',
+                                     'x86_64-linux-gnu'
                                      ] )
 
         if (ssl_incs is not None and

```

apply the patch1
```
patch setup.py < setup_py.patch
```

configure and set the installation directory on /opt/python2.4:
```
env CPPFLAGS="-I/usr/lib/x86_64-linux-gnu" LDFLAGS="-L/usr/include/x86_64-linux-gnu"  ./configure --prefix=/opt/python2.4
```

code compilation:
```
make
```

installation (/opt/python2.4)
```
make install
```

---

### Post by bruno.braga on 2012-05-16
I just installed python2.4 on my Ubuntu 12.04 64-bit, and didn't have the troubles stated here... but I didn't tested any SSL features (where these patches seem to fix problems).

I just got the source and compiled it, plain and simple:

```

wget http://www.python.org/ftp/python/2.4.6/Python-2.4.6.tgz
tar -zxvf Python-2.4.6.tgz
cd Python-2.4.6
./configure
make 
sudo make install

# then you need to remove the binary from your local bin, 
# which overrides the default (you don't want to do that)
sudo rm /usr/local/bin/python

# to access Python2.4
python2.4

```

---

### Post by mikemets on 2012-09-02
Hi,

I've just installed 2.4.6 as suggested but I still get Import Error: No module named ssl. Looking through the entire post (initially I just read the 2.4 bit) I see there are steps in the 2.6 section wrt ssl that are not in the the 2.4 section. Have I missed something?

Thanks
Mike

---

### Post by agger on 2012-09-24
> **bruno.braga said:**
> I just installed python2.4 on my Ubuntu 12.04 64-bit, and didn't have the troubles stated here... but I didn't tested any SSL features (where these patches seem to fix problems).

I just got the source and compiled it, plain and simple...

The first thing I did was just compile it, and it installed!

However, there was no ```
zlib
```, and thus I couldn't run Plone 3, which is why  needed Python 2.4 in the first place. Only after I applied the patch given in the start of this thread did I stand a chance, so I'm grateful for the documentation. :-)

---

### Post by jlsandell on 2012-10-25
> **appociappo said:**
> create a text file setup_py.patch with any preferred text editor (vim anyone?) with the following content:
```
--- Python-2.6.8/setup.py       2012-04-10 17:32:11.000000000 +0200
+++ Python-2.6.8_ok/setup.py    2012-05-08 12:42:23.893052724 +0200
@@ -410,6 +410,7 @@
         lib_dirs = self.compiler.library_dirs + [
             '/lib64', '/usr/lib64',
             '/lib', '/usr/lib',
+            '/usr/lib/x86_64-linux-gnu'
             ]
         inc_dirs = self.compiler.include_dirs + ['/usr/include']
         exts = []

```

For what it's worth, I found out today using Ubuntu 12.04 that I needed to add /lib/x86_64-linux-gnu to my LDFLAGS as well in order to pick up zlib, bz2, and friends. In fact, I found it much easier simply to create a file to pre-set these for me, i.e.:
```

jeremy@devnode:~/.pythonz$ cat ~/tools/build.sh 
export arch=$(dpkg-architecture -qDEB_HOST_MULTIARCH)
export LDFLAGS="-L/usr/lib/$arch -L/lib/$arch"
export CFLAGS="-I/usr/include/$arch"
export CPPFLAGS="-I/usr/include/$arch"

jeremy@devnode:~/.pythonz$ . ~/tools/build.sh
```

prior to building Python 2.6.8. I **did** need to apply the patch for Modules/_ssl.c, however. Otherwise I'd tend to get errors such as

```
WARNING: renaming "_ssl" since importing it failed: build/lib.linux-x86_64-2.6/_ssl.so: undefined symbol: SSLv2_method
```

while building.


Many thanks to you, appociappo, as your post certainly gave me enough information to figure out how to fix my problem. :D

---

