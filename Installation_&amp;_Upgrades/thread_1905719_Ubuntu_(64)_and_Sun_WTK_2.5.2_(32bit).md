---
title: "Ubuntu (64) and Sun WTK 2.5.2 (32bit)"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by wiskeyplm on 2012-01-07
Hi, 
I'm trying to run Sun Wireless Toolkit 2.5.2 (which is 32b) on ubuntu 11.04 64b. WTK requires JDK 1.5 or 1.6.
I have tried using WTK with JDK 1.5 32 and 64b but none seem to work. After building the package successfully, I get the following error when I run it:


java.lang.UnsatisfiedLinkError: /home/username/WTK2.5.2/bin/sublime.so: Can't load IA 32-bit .so on a AMD 64-bit platform
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
	at java.lang.Runtime.load0(Runtime.java:769)
	at java.lang.System.load(System.java:968)
	at com.sun.kvem.Sublime.<init>(Unknown Source)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at java.lang.Class.newInstance0(Class.java:350)
	at java.lang.Class.newInstance(Class.java:303)
	at com.sun.kvem.Lime.createLime(Unknown Source)
	at com.sun.kvem.KVMBridge.<init>(Unknown Source)
	at com.sun.kvem.KVMBridge.getBridge(Unknown Source)
	at com.sun.kvem.midp.MIDP.run(Unknown Source)
	at com.sun.kvem.environment.EmulatorInvoker.runEmulatorImpl(Unknown Source)
	at com.sun.kvem.environment.EmulatorInvoker.main(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.sun.kvem.environment.JVM.main(Unknown Source)


With the 32b jdk it's pretty much the same error, just replaces 64 with 32 on the first line of error.

I'm dual booting Ubuntu 11.04 64b next to Windows 7 64b.
Since there is no 64 bit version of WTK 2.5.2 and it doesn't seem to work with jdk 64 or 32 bit... I'm stuck. 

Is there a workaround this? If I install Ubuntu 32bit, will it work then? Will Ubuntu 32 bit work on my laptop? 

I have an hp Pavilion quad core 1.8ghz(AMD) with 8gb ram and I'm a new Linux user.
Any help is greatly appreciated. Thank you!

---

### Post by wiskeyplm on 2012-01-07
HA! All I had to do is install the libraries to be able to run properly 32bit apps :
sudo apt-get install ia32-libs

---

