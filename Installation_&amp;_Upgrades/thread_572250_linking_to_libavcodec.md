---
title: "linking to libavcodec"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by coquinho61 on 2007-10-10
Hi,

I recently upgraded from a Mandrake machine to Ubuntu 7.0. I work at a University, so we use code written by loads of different people, who have often left ages ago.

Now I tried to use  a program that needs libavcodec.so.0 The error message I get is, to be specific:

ImportError: libavcodec.so.0: cannot open shared object file: No such file or directory

Now, at first I didn't have this so. So, I tried the following:

ln -s libavcodec.so.51.45.0 /usr/local/lib/libavcodec.so.0 

so as to link to the libavcodec I'm using. For good measure I continued to issue a

ldconfig -v

command. However, the problem didn't go away. Does anyone know what I'm doing wrong here? The program had similar problems with libboost_python, but that was solved by inserting the proper symbolic link.

Thanks,

Michel

---

