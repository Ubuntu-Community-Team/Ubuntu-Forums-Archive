---
title: "libfljni.so: libflfftw3.so.3: cannot open shared object file: No such file or dir..."
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by djibi on 2009-12-20
Hi everyone,

I'm trying to install Comsol 3.5.
When I try to launch the startup script once the installation finished, I've got the following error:

$ '/data/Comsol35/comsol35/bin/comsol' 
Exception in thread "main" java.lang.UnsatisfiedLinkError: /data/Comsol35/COMSOL35/lib/glnx86/libfljni.so: libflfftw3.so.3: cannot open shared object file: No such file or directory
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(Unknown Source)
	at java.lang.ClassLoader.loadLibrary(Unknown Source)
	at java.lang.Runtime.load0(Unknown Source)
	at java.lang.System.load(Unknown Source)
	at com.femlab.jni.FlNativeUtil.loadLibrary(Unknown Source)
	at com.femlab.jni.FlNativeUtil.ensureLibIsLoaded(Unknown Source)
	at com.femlab.server.Launcher.setup(Unknown Source)
	at com.femlab.server.Launcher.main(Unknown Source)

It seems to be a problem with the library and I should specify some links, but I don't know which...

Thanks for help!

Regards,

djibi!

---

