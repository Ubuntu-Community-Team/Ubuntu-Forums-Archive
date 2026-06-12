---
title: "Getting symbol lookup error:    undefined symbol:  Need help!"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by abrrymnvette on 2010-01-13
I'm trying to move a program from Box A to Box B. The program is currently running on box A fine, but that is the only thing being used on the box. I'm trying to move it to box B so I can repurpose box A. 


Box A is running
# cat /proc/version
Linux version 2.6.17-10-server (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:47:26 UTC 2006 (Ubuntu 2.6.17-10.33-server)



Box B is running
# cat /proc/version
Linux version 2.6.24-23-server (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Wed Apr 1 22:22:14 UTC 2009


What I did was tar up the entire directory that the program was in on box A and moved it to the same spot on box B. 

When I run the program on box B is when I get the errors. 
# ./moved_program
./moved_program: symbol lookup error: ./moved_program: undefined symbol: zcalloc


So, if I do a ldd on the program I get different library dependencies. How can that be though? 


Box A  (program works)
# ldd moved_program
        linux-gate.so.1 =>  (0xffffe000)
        libcurl.so.3 => /usr/lib/libcurl.so.3 (0xb7f66000)
        libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0xb7f4a000)
        libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0xb7ece000)
        libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0xb7ea8000)
        libcom_err.so.2 => /lib/libcom_err.so.2 (0xb7ea5000)
        libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0xb7ea0000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7e8d000)
        libidn.so.11 => /usr/lib/libidn.so.11 (0xb7e5d000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7e59000)
        libssl.so.0.9.8 => /usr/lib/i686/cmov/libssl.so.0.9.8 (0xb7e19000)
        libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7cdf000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7ccb000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7bec000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7bc6000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7bbb000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7ba7000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7a73000)
        /lib/ld-linux.so.2 (0xb7fa1000)


Box B (doesn't work)
# ldd moved_program
        linux-gate.so.1 =>  (0xb7f49000)
        libcurl.so.3 => /usr/lib/libcurl.so.3 (0xb7f07000)
        libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0xb7ede000)
        libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0xb7e50000)
        libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0xb7e2d000)
        libcom_err.so.2 => /lib/libcom_err.so.2 (0xb7e2a000)
        libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0xb7e22000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7e0f000)
        libidn.so.11 => /usr/lib/libidn.so.11 (0xb7dde000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7dd9000)
        libssl.so.0.9.8 => /usr/lib/i686/cmov/libssl.so.0.9.8 (0xb7d97000)
        libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7c55000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7c40000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7b4d000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7b27000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7b1c000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7b04000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb79b5000)
        libldap_r-2.4.so.2 => /usr/lib/libldap_r-2.4.so.2 (0xb7975000)
        libkeyutils.so.1 => /lib/libkeyutils.so.1 (0xb7972000)
        /lib/ld-linux.so.2 (0xb7f4a000)
        liblber-2.4.so.2 => /usr/lib/liblber-2.4.so.2 (0xb7964000)
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb794d000)
        libgnutls.so.13 => /usr/lib/libgnutls.so.13 (0xb78d7000)
        libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0xb78c7000)
        libgcrypt.so.11 => /lib/libgcrypt.so.11 (0xb787a000)
        libgpg-error.so.0 => /lib/libgpg-error.so.0 (0xb7875000)



ANY help you guys have is greatly appreciated b/c I'm completely stuck now. I don't know how to tell what libraries I need to add, which ones are to new, which ones will screw some other program up that is currently running on box B, etc.

---

