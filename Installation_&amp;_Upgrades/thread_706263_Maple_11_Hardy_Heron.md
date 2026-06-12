---
title: "Maple 11 Hardy Heron"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by frohchar on 2008-02-24
I recently upgraded to Hardy Heron alpha 5. When I try to start Maple 11 I get the following
error message. Does anybody have a way to solve this problem?

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb2773767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb27738b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0x931b829d]
#3 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x93292a76]
#4 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x9327880a]
#5 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x93278a51]
#6 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0x93278c5c]
#7 [0xb2800fa8]
#8 [0xb27faaeb]
#9 [0xb27faaeb]
#10 [0xb27f81b4]
#11 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0xb76037ec]
#12 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0xb77c6828]
#13 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0xb760361f]
#14 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xb7660d1d]
#15 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb73122cd]
#16 [0xb2800838]
#17 [0xb27faa14]
#18 [0xb27f81b4]
#19 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0xb76037ec]
java: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Aborted (core dumped)


Thanks!

---

### Post by loko on 2008-02-24
google is your friend

[http://gentoo-wiki.com/Compiz_fusion#XCB_workaround]("http://gentoo-wiki.com/Compiz_fusion#XCB_workaround")

if the link above doesn't solve your problem:

[http://www.google.de/search?q=java%3A+xcb_xlib.c%3A82%3A+xcb_xlib_unlock%3A+Assertion+%60c-%3Exlib.lock'+failed.&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:de:official&client=firefox-a]("http://www.google.de/search?q=java%3A+xcb_xlib.c%3A82%3A+xcb_xlib_unlock%3A+Assertion+%60c-%3Exlib.lock'+failed.&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:de:official&client=firefox-a")

---

### Post by frohchar on 2008-02-24
Thanks. Following your google link I found this script written by someone named
S. Correia that patches the files.  Save it as a script and run it with sudo and it
patches all the occurences of the libmawt.so file.

#!/bin/sh
# S. Correia
# 2007 11 21
# A simple script to patch the java library in order
# to solve the problem with "Assertion 'c->xlib.lock' failed."
# see bug [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373)
LIB_TO_PATCH=libmawt.so
for f in `find /usr/lib/jvm -name "$LIB_TO_PATCH"`
do
echo "Patching library $f"
sudo sed -i 's/XINERAMA/FAKEEXTN/g' "$f"
done


unfortunately, Maple still doesn't start, and I get the error message,




charlie@circle:~$ xm11
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb73be767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb73be8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0x9322529d]
#3 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x932ffa76]
#4 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x932e580a]
#5 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x932e5a51]
#6 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0x932e5c5c]
#7 [0xb2850fa8]
#8 [0xb284aaeb]
#9 [0xb284aaeb]
#10 [0xb28481b4]
#11 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0xb76537ec]
#12 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0xb7816828]
#13 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0xb765361f]
#14 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xb76b0d1d]
#15 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb73622cd]
#16 [0xb2850838]
#17 [0xb284aa14]
#18 [0xb28481b4]
#19 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0xb76537ec]
java: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Aborted (core dumped)


Charlie

---

### Post by frohchar on 2008-02-24
So then I just patched the libmawt.so files by hand and I got the error:


charlie@circle:~$ xm11
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb73be767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb73be8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0x9322529d]
#3 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x932ffa76]
#4 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x932e580a]
#5 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x932e5a51]
#6 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0x932e5c5c]
#7 [0xb2850fa8]
#8 [0xb284aaeb]
#9 [0xb284aaeb]
#10 [0xb28481b4]
#11 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0xb76537ec]
#12 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0xb7816828]
#13 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0xb765361f]
#14 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xb76b0d1d]
#15 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb73622cd]
#16 [0xb2850838]
#17 [0xb284aa14]
#18 [0xb28481b4]
#19 /usr/local/maple11/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0xb76537ec]
java: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Aborted (core dumped)


I then use the same line to try to patch libjvm.so living in my maple directory but no soap.

---

### Post by frohchar on 2008-02-24
Finally, I patched the copies of the library  libmawt.so living in my maple installation directory
and it works again!

Thanks for your help!

Charlie

---

### Post by Peneus on 2008-02-26
I am trying to install Maple on Hardy too.
Can you be more explicit about how to patch those files,  
especially the ones in your installation directory. when you say installation directory do you mean something like /tmp/install.dir.6618?

thanks

---

### Post by frohchar on 2008-03-01
I installed maple in /usr/local/maple11, inside that directory is a copy of Java that
needed to be patched.  I just found the three occurrences of libmawt.so in that 
directory and patched it by adapting the appropriate line from the script.

Hope thats enough. If not, i can get more explicit, with some work.

---

