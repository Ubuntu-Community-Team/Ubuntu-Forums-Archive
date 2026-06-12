---
title: "How do I tell what libraries I'm missing for a program to run right?"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by abrrymnvette on 2010-01-15
I moved a program from one machine to a different one. When I run it on the new one I get errors. How do I tell what libraries it's missing and then find them? 

Thanks.

---

### Post by kellemes on 2010-01-15
[Search for package-info]("http://packages.ubuntu.com/")

For example, if you need info about smplayer and all of it's dependencies, you search the Database and get [this as result]("http://packages.ubuntu.com/karmic/smplayer").

---

### Post by abrrymnvette on 2010-01-15
What about if it's not a package in the list?

---

### Post by d3v1150m471c on 2010-01-15
Is this something you installed with apt-get or synaptic? If so then you probably need to do the same on the other computer, granted it's the same os. Or...if you are avoiding having to do that, do a complete uninstall of the program, run sudo apt-get autoclean and sudo apt-get autoremove, and when you reinstall it, pay attention to the dependencies that go along with it. Then, copy these packages over to the other machine and also install them.

---

### Post by abrrymnvette on 2010-01-15
> **d3v1150m471c said:**
> Is this something you installed with apt-get or synaptic? If so then you probably need to do the same on the other computer, granted it's the same os. Or...if you are avoiding having to do that, do a complete uninstall of the program, run sudo apt-get autoclean and sudo apt-get autoremove, and when you reinstall it, pay attention to the dependencies that go along with it. Then, copy these packages over to the other machine and also install them.


No, it's something that is "part" of a commercial product that we pay for the use of. It's a one off install bascially. I can't uninstall it b/c it's in production currently. I'm not very much help am I.

---

### Post by slakkie on 2010-01-15
You can use ldd /path/to/binary and then you will get a list of shared libs it will use and which ones cannot be found. Then use apt-file (aptitude install apt-file) to search for those files and install the correct libraries.

```

ldd $(which aptitude)
        linux-gate.so.1 =>  (0xb76e9000)
        libapt-pkg-libc6.10-6.so.4.8 => not found
        libncursesw.so.5 => /lib/libncursesw.so.5 (0xb768a000)
        libsigc-2.0.so.0 => /usr/lib/libsigc-2.0.so.0 (0xb7682000)
        libcwidget.so.3 => /usr/lib/libcwidget.so.3 (0xb75c4000)
        libept.so.0 => /usr/lib/libept.so.0 (0xb7553000)
        libxapian.so.15 => /usr/lib/libxapian.so.15 (0xb740a000)
        libz.so.1 => /lib/libz.so.1 (0xb73f5000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb73dc000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb72e8000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb72c2000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb72a4000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7160000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb715c000)
        /lib/ld-linux.so.2 (0xb76ea000)
        libapt-pkg-libc6.10-6.so.4.8 => not found

```

As you can see I'm missing some libs, which aptitude needed. To get the correct packages for these files:

```

apt-file search libapt-pkg-libc6.10-6.so.4.8

```

---

### Post by abrrymnvette on 2010-01-15
Awesome! Thanks, that's exactly what I was looking for.

---

### Post by abrrymnvette on 2010-01-15
That worked. So, this is what I get when I run ldd now. 
 linux-gate.so.1 =>  (0xb7f5f000)
        libcurl.so.3 => /usr/lib/libcurl.so.3 (0xb7f1d000)
        libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0xb7ef4000)
        libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0xb7e66000)
        libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0xb7e43000)
        libcom_err.so.2 => /lib/libcom_err.so.2 (0xb7e40000)
        libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0xb7e38000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7e25000)
        libidn.so.11 => /usr/lib/libidn.so.11 (0xb7df4000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7def000)
        libssl.so.0.9.8 => /usr/lib/i686/cmov/libssl.so.0.9.8 (0xb7dad000)
        libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7c6b000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7c56000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7b63000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7b3d000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7b32000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7b1a000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb79cb000)
        libldap_r-2.4.so.2 => /usr/lib/libldap_r-2.4.so.2 (0xb798b000)
        libkeyutils.so.1 => /lib/libkeyutils.so.1 (0xb7988000)
        /lib/ld-linux.so.2 (0xb7f60000)
        liblber-2.4.so.2 => /usr/lib/liblber-2.4.so.2 (0xb797a000)
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7963000)
        libgnutls.so.13 => /usr/lib/libgnutls.so.13 (0xb78ed000)
        libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0xb78dd000)
        libgcrypt.so.11 => /lib/libgcrypt.so.11 (0xb7890000)
        libgpg-error.so.0 => /lib/libgpg-error.so.0 (0xb788b000)



But then when I run the program I get this:

 undefined symbol: zcalloc

---

### Post by slakkie on 2010-01-15
uhm.. yes. I think you might want to have a closer look at this problem and perhaps contact your supplier.

---

