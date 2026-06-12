---
title: "missing rights to run java applet in browser after upgrade to 10.04"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by a.dimuzio on 2010-05-07
I'm having a very strange error after upgrading to (K)Ubuntu 10.04.. basically Java Applets don't work in any browser (tried with Firefox, Chrome and Opera).
The applet loads (plugin and JVM detected by all browsers) but it is grayed out.

After trying all possible solutions I could think of (including installing alternatives jvm) I tried to run the browser as superuser: the applet is then working correctly.

So somehow it seems to be a user right problem, but I'm not sure where this is coming from, both java (sun-6) and the browsers were installed and working ok in 9.10.

Here is the directory list of /usr/lib/jvm/java-6-sun/jre/lib/i386

```

drwxr-xr-x 2 root root 4.0K 2010-05-07 14:03 client
drwxr-xr-x 2 root root 4.0K 2010-05-07 14:03 headless
drwxr-xr-x 2 root root 4.0K 2010-05-07 14:03 jli
lrwxrwxrwx 1 root root   23 2010-05-07 14:03 jvm.cfg -> /etc/java-6-sun/jvm.cfg
-rw-r--r-- 1 root root  13K 2010-04-12 23:36 libattach.so
-rw-r--r-- 1 root root 609K 2010-04-12 23:36 libawt.so
-rw-r--r-- 1 root root 395K 2010-04-12 23:36 libcmm.so
-rw-r--r-- 1 root root 177K 2010-04-12 23:36 libdcpr.so
-rw-r--r-- 1 root root 281K 2010-04-12 23:39 libdeploy.so
-rw-r--r-- 1 root root  19K 2010-04-12 23:36 libdt_socket.so
-rw-r--r-- 1 root root 636K 2010-04-12 23:36 libfontmanager.so
-rw-r--r-- 1 root root 218K 2010-04-12 23:36 libhprof.so
-rw-r--r-- 1 root root  46K 2010-04-12 23:36 libinstrument.so
-rw-r--r-- 1 root root  20K 2010-04-12 23:36 libioser12.so
-rw-r--r-- 1 root root  39K 2010-04-12 23:36 libj2gss.so
-rw-r--r-- 1 root root  12K 2010-04-12 23:36 libj2pcsc.so
-rw-r--r-- 1 root root  71K 2010-04-12 23:36 libj2pkcs11.so
-rw-r--r-- 1 root root 6.3K 2010-04-12 23:36 libjaas_unix.so
-rw-r--r-- 1 root root  25K 2010-04-12 23:36 libjava_crw_demo.so
-rw-r--r-- 1 root root  79K 2010-04-12 23:39 libjavaplugin_jni.so
-rw-r--r-- 1 root root 350K 2010-04-12 23:39 libjavaplugin_nscp_gcc29.so
-rw-r--r-- 1 root root 263K 2010-04-12 23:39 libjavaplugin_nscp.so
-rw-r--r-- 1 root root 185K 2010-04-12 23:36 libjava.so
-rw-r--r-- 1 root root 5.3K 2010-04-12 23:36 libjawt.so
-rw-r--r-- 1 root root  70K 2010-04-12 23:36 libJdbcOdbc.so
-rw-r--r-- 1 root root 273K 2010-04-12 23:36 libjdwp.so
-rw-r--r-- 1 root root 207K 2010-04-12 23:36 libjpeg.so
-rw-r--r-- 1 root root 8.0K 2010-04-12 23:36 libjsig.so
-rw-r--r-- 1 root root  80K 2010-04-12 23:36 libjsoundalsa.so
-rw-r--r-- 1 root root 231K 2010-04-12 23:36 libjsound.so
-rw-r--r-- 1 root root  34K 2010-04-12 23:36 libmanagement.so
-rw-r--r-- 1 root root 812K 2010-04-12 23:36 libmlib_image.so
-rw-r--r-- 1 root root 5.2K 2010-04-12 23:36 libnative_chmod_g.so
-rw-r--r-- 1 root root 5.3K 2010-04-12 23:36 libnative_chmod.so
-rw-r--r-- 1 root root  94K 2010-04-12 23:36 libnet.so
-rw-r--r-- 1 root root  37K 2010-04-12 23:36 libnio.so
-rw-r--r-- 1 root root  76K 2010-04-12 23:39 libnpjp2.so
-rw-r--r-- 1 root root  13K 2010-04-12 23:36 libnpt.so
lrwxrwxrwx 1 root root   31 2010-05-07 14:03 libodbcinst.so -> ../../../../../libodbcinst.so.1
lrwxrwxrwx 1 root root   27 2010-05-07 14:03 libodbc.so -> ../../../../../libodbc.so.1
-rw-r--r-- 1 root root 4.8K 2010-04-12 23:36 librmi.so
-rw-r--r-- 1 root root  38K 2010-04-12 23:36 libsaproc.so
-rw-r--r-- 1 root root 263K 2010-04-12 23:36 libsplashscreen.so
-rw-r--r-- 1 root root 141K 2010-04-12 23:36 libunpack.so
-rw-r--r-- 1 root root  56K 2010-04-12 23:36 libverify.so
-rw-r--r-- 1 root root  75K 2010-04-12 23:36 libzip.so
drwxr-xr-x 2 root root 4.0K 2010-05-07 14:03 motif21
drwxr-xr-x 2 root root 4.0K 2010-05-07 14:03 native_threads
drwxr-xr-x 2 root root 4.0K 2010-05-07 14:03 server
drwxr-xr-x 2 root root 4.0K 2010-05-07 14:03 xawt

```

Any idea? It seems I'm the only one to have this problem so I'm hesitating to fill a bug report...

---

### Post by a.dimuzio on 2010-05-07
Another interesting clue, I can't run policytool as a regolar user:
```

 ./policytool 
Warning: Cannot convert string "-dejavu-dejavu sans-medium-r-normal--*-140-*-*-p-*-iso10646-1" to type FontStruct
Exception in thread "main" java.lang.NullPointerException: NullPointerException
        at sun.awt.motif.MTextFieldPeer.setFont(Native Method)
        at sun.awt.motif.MComponentPeer.initialize(MComponentPeer.java:179)
        at sun.awt.motif.MTextFieldPeer.initialize(MTextFieldPeer.java:70)
        at sun.awt.motif.MComponentPeer.init(MComponentPeer.java:223)
        at sun.awt.motif.MComponentPeer.<init>(MComponentPeer.java:227)
        at sun.awt.motif.MTextFieldPeer.<init>(MTextFieldPeer.java:74)
        at sun.awt.motif.MToolkit.createTextField(MToolkit.java:186)
        at java.awt.TextField.addNotify(TextField.java:205)
        at java.awt.Container.addNotify(Container.java:2578)
        at java.awt.Window.addNotify(Window.java:663)
        at java.awt.Frame.addNotify(Frame.java:470)
        at java.awt.Window.show(Window.java:859)
        at java.awt.Component.show(Component.java:1563)
        at java.awt.Component.setVisible(Component.java:1515)
        at java.awt.Window.setVisible(Window.java:842)
        at sun.security.tools.ToolWindow.initWindow(PolicyTool.java:1030)
        at sun.security.tools.ToolWindow.displayToolWindow(PolicyTool.java:1129)
        at sun.security.tools.PolicyTool.main(PolicyTool.java:705)

```

Running the same command as superuser (kdesudo ./policytool) works without exceptions.

---

### Post by a.dimuzio on 2010-05-07
Solved :-) 
It was not at all a rights problem.. I figured it out by creating another normal user and testing it again.. everything is working.

Then I figured it was a profile problem, something I set in the past in either .bashrc or .profile was driving java crazy.

And then I remember I had to add 
```

export AWT_TOOLKIT="MToolkit"

```
to .profile to fix a bug in 9.10 avoiding java GUi to dispaly correctly.

Once this line removed everything started to work again.

The question remains, why did it happen after the upgrade? If somebody has an explication it is very much appreciated.

---

