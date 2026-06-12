---
title: "libGL.so location changed from update, now g++ wont compile"
date: 2014-01-28
forum: Installation &amp; Upgrades
---

### Post by ionray on 2014-01-28
Hi,
 
 I am running Ubuntu 12.0.4 LTS and just did an update from the update manager, It looks like the NVidia graphics library was updated.  I had code that compiled with g++ now the entire library (OpenCV) gives the error: g++: error: /usr/lib/libGL.so: No such file or directory

 I than ran the following command to find its location: sudo find / -name libGL.so

 Output:
 /usr/lib/nvidia-304/libGL.so 
 /usr/lib/x86_64-linux-gnu/libGL.so 
 /usr/lib/x86_64-linux-gnu/mesa/libGL.so 
 /usr/lib32/nvidia-304/libGL.so 
 
 I then navigated to cd /etc/ld.so.conf.d/ and used ls
 Output:
 i386-linux-gnu_GL.conf  libc.conf              x86_64-linux-gnu_GL.conf 
 i686-linux-gnu.conf     x86_64-linux-gnu.conf  zz_i386-biarch-compat.conf 
 
 seeing the connection between  x86_64-linux-gnu opened that file with vi x86_64-linux-gnu.conf
 Output:
 # Multiarch support 
 /lib/x86_64-linux-gnu 
 /usr/lib/x86_64-linux-gnu 
 
The location change seems to be in the file so I ran sudo ldconfig -v but no sucess.

I got this information from using google, I do not know how to fix the problem but it seems there should be a work around.

 Any help is appreciated,

---

