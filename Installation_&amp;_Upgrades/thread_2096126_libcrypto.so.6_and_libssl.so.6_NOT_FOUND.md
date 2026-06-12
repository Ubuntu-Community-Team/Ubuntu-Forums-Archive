---
title: "libcrypto.so.6 and libssl.so.6 NOT FOUND"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by aviks on 2012-12-19
Hello ubuntu users
I am trying to install GATE 6.2 (Geant4 application for tomographic emission) and when I give make -j2 command I am getting the following error --------------------
 
avinash@avinash-desktop:~/sim/gate.6.2-build$ make -j2
[  2%] Built target itkzlib
[  7%] Built target ITKMetaIO
Linking CXX executable Gate
/usr/bin/ld: warning: libcrypto.so.6, needed by
/home/avinash/sim/root_v5.34/lib/libNet.so, not found (try using -rpath or
-rpath-link)
/usr/bin/ld: warning: libssl.so.6, needed by
/home/avinash/sim/root_v5.34/lib/libNet.so, not found (try using -rpath or
-rpath-link)
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_set_quiet_shutdown'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_CTX_load_verify_locations'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_peek'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_read'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_connect'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_free'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to `SSL_new'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`EVP_sha1'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_CTX_new'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_set_fd'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_CTX_use_certificate_chain_file'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_shutdown'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_get_error'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSLv23_method'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_CTX_use_PrivateKey_file'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_library_init'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_write'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to `HMAC'
/home/avinash/sim/root_v5.34/lib/libNet.so: undefined reference to
`SSL_CTX_free'
collect2: ld returned 1 exit status
make[2]: *** [Gate] Error 1
make[1]: *** [CMakeFiles/Gate.dir/all] Error 2
make: *** [all] Error 2
-------------------------------------------------------------------------------------------------------------------------------------------

I think this is problem related to OS, I am using ubuntu 10.10 and after some search in the Internet I found that these two files (libcrypto.so.6 and libssl.so.6) are related to openssl package but I have already installed it.I think I have to create a softlink to these files and I am new to ubuntu.
Any help ?

---

### Post by Ozymandias_117 on 2012-12-19
You need the development files for ssl, you probably only installed the program files. Try ```
sudo apt-get install libssl-dev
```

---

### Post by aviks on 2012-12-19
I have already installed libssl-dev.
(avinash@avinash-desktop:~$ sudo apt-get install libssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libssl-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  lib32bz2-1.0 extra-xdg-menus lib32ncurses5 ia32-libs libsdl-mixer1.2
  libcap2-bin libc6-i386 lib32gcc1 lib32asound2 libsmi2ldbl libc-ares2 lib32z1
  lib32stdc++6 lib32v4l-0 libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.)

---

### Post by Ozymandias_117 on 2012-12-19
Oh. That library was from an older version.  You can try linking the new version to the old one to see if it will compile with the current version if you want: ```
ln -s /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 /lib/x86_64-linux-gnu/libcrypto.so.6
```
and replace crypto with ssl there for the other library.

---

### Post by aviks on 2012-12-19
I tried it but I am getting an error-

avinash@avinash-desktop:~$ ln -s /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 /lib/x86_64-linux-gnu/libcrypto.so.6
ln: creating symbolic link `/lib/x86_64-linux-gnu/libcrypto.so.6': No such file or directory.
actually by looking at the error which I am getting, when I type make -j2
(
/usr/bin/ld: warning: libcrypto.so.6, needed by
/home/avinash/sim/root_v5.34/lib/libNet.so, not found (try using -rpath or
-rpath-link)
/usr/bin/ld: warning: libssl.so.6, needed by
/home/avinash/sim/root_v5.34/lib/libNet.so, not found (try using -rpath or
-rpath-link)
)
I think the sybolic link has to be created in /usr/bin/ld, but I am not able to see ld (for checking to which .so file I should create the link to libcrypto.so.6) (sorry if I am talking utterly nonsense ! I am new to ubuntu and my knowledge over ld is very poor)

---

### Post by Ozymandias_117 on 2012-12-19
Sorry, I didn't add sudo at the beginning, you need root privilages to run that command.  ld is just a linker used by the compiler, it's not a folder that you can put libraries in :P

```
sudo ln -s /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 /lib/x86_64-linux-gnu/libcrypto.so.6
sudo ln -s /lib/x86_64-linux-gnu/libssl.so.1.0.0 /lib/x86_64-linux-gnu/libssl.so.6
```

---

### Post by aviks on 2012-12-19
I don't have libcrypto.so.1.0.0 and libssl.so.1.0.0 in folder /usr/lib/x86_64-linux-gnu.

I have libcrypto.so and libcrypto.so.0.9.8 in /usr/lib folder.
And libssl.so and libssl.so.0.9.8 also in /usr/lib folder.

To which .so (.so or .so.0.9.8) I have to create link?

---

### Post by aviks on 2012-12-19
[SOLVED]
I just copied libcrypto.so and renamed it to libcrypto.so.6 (same to libssl.so) Now its working!! 
Thank you for the help.
):P

---

### Post by chaitanya3 on 2013-09-30
Hi,

I have the same problem while installing Gate. 

Could you please tell me how to fix this issue?

Thanks,
Chaitanya

Edit: I have libssl.so in /usr/lib linked to libssl.so.1.0.0 in /lib/x86_64-linux-gnu (Same for libcrypto.so)

---

