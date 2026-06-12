---
title: "jrun libstdc++ jikesw compiler errors"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by jmck on 2007-05-04
I am running v6.06 with Jrun4 and Apache installed.  When I call my Java page I get a compiler error from jikesw (something in the JDK Jrun called.)  this is the error:

Jrun's output:
jrunx.compiler.JavaCompiler$NoCompilerFoundException: Could not invoke Java compiler, please make sure jikesw is in /usr/local/jrun4/bin or put a JDK bin directory in your path.
        at jrunx.compiler.JavaCompiler.outProcessCompile(JavaCompiler.java:467)
        at jrunx.compiler.JavaCompiler.compile(JavaCompiler.java:132)


To avoid the obvious...jikesw IS in /usr/local/jrun4/bin and the JDK DOES live in the $CLASSPATH and $PATH env vars.  Permissions are 755 for everything under /usr/local/jrun and /usr/local/jdk1.5.6_06

Calling jikesw directly:
bbysrv:/usr/local/jrun4/bin$ ./jikesw
./jikesw: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

According to the Jrun 'know issues' it appears I need to downgrade libstdc++ below v3.  How can I do this?  I tried installing both old/new versions but it's still seeing the new stuff and crashing.  apt-get won't let me remove the v3 version because of massive system dependencies.

Thanks.
-J

---

### Post by jmck on 2007-05-04
I figured it out myself. ...path issue  (I mean human error!)

-J

---

### Post by neurosis on 2007-06-25
So.. how did you fix it? I'm having the same problems :(

---

