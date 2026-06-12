---
title: "httpd-2.3.8 installation from source problem"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by alfchung on 2010-12-20
Hi,
I installed apache2 (httpd-2.3.8) from source. Here is what I did, download the source package from the apache2 website. ./configure, installed all the package it depends on, and finally, configure successfully.
make
sudo make install

I think it installed in  
/usr/local/apache2

So I cd to /usr/local/apache2/bin
try
./httpd start

and it shows
./httpd: error while loading shared libraries: libpcre.so.0: cannot open shared object file: No such file or directory

ldd ./httpd
it shows
    linux-gate.so.1 =>  (0xb7747000)
    libpcre.so.0 => not found
    libaprutil-1.so.0 => /usr/local/apr/lib/libaprutil-1.so.0 (0xb771b000)
    libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb76f9000)
    libapr-1.so.0 => /usr/local/apr/lib/libapr-1.so.0 (0xb76d1000)
    libuuid.so.1 => /lib/libuuid.so.1 (0xb76cd000)
    librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb76c4000)
    libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7692000)
    libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7679000)
    libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7675000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7526000)

My libpcre.so.0 is located in /usr/local/lib/libpcre.so.0, I checked that

How can I fix this problem?

Thanks!
Alfred

---

### Post by PhantmKllr on 2010-12-21
Install the packages libpcrecpp0 and libpcre++0 in Synaptic.

---

### Post by alfchung on 2010-12-21
$ synaptic 
Segmentation fault

it doesn't work...

But I installed pcre-8.11 from source already, and it doesn't work

---

### Post by PhantmKllr on 2010-12-21
"System -> Administration -> Synaptic Package Manager"

---

### Post by Colin Keenan on 2012-11-10
This question was never really answered properly. I'm having the same problem and found the correct answer. First of all, you can see all the libraries and where they are with:
> cd /usr/local/apache2/bin
ldd httpd
Assuming you used the default settings for where httpd gets installed. When you do that, you should see everything's fine except:
> libpcre.so.1 => not found

Now, to fix that, you have to delete the file where that library info is stored, and then rebuild the library info. These two commands will do that:
> sudo rm /etc/ld.so.cache
sudo /sbin/ldconfig

To double check it worked, you can run 
> ldd httpd
again and see that httpd now knows where all the libraries are.

---

### Post by elracorey on 2013-01-18
Many thanks Colin for this spot on answer!

---

