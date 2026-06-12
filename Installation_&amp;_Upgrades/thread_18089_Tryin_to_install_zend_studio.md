---
title: "Tryin to install zend studio"
date: 2005-03-04
forum: Installation &amp; Upgrades
---

### Post by Isengrim on 2005-03-04
Hello, today I installed ubuntu hoary,  I have everything working now (even wireless connection @ startup =D> )
But I can't install Zend Studio 4.
I have java installed 
```

root@LAPTOP:/home/anne/Desktop/ZendStudio-4_0_0a # java -version
java version "1.5.0_01"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_01-b08)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_01-b08, mixed mode)

```

If I try installing Zend I get this message everytime

```

root@LAPTOP:/home/anne/Desktop/ZendStudio-4_0_0a # ./ZendStudio-4_0_0a.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libresolv.so.2: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
current locale is not supported in X11, locale is set to CX locale modifiers are not supported, using defaultInvocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.InternalError: Current locale is not supported
        at sun.awt.motif.MWindowPeer.pSetTitle(Native Method)
        at sun.awt.motif.MWindowPeer.init(Unknown Source)
        at sun.awt.motif.MFramePeer.<init>(Unknown Source)
        at sun.awt.motif.MToolkit.createFrame(Unknown Source)
        at java.awt.Frame.addNotify(Unknown Source)
        at com.zerog.ia.installer.LifeCycleManager.f(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

```

I don't have a clue what this means (I am kinda linux n00b), can someone explain me how to fix it please.

I run the 64 bit version of hoary btw

---

### Post by yippy on 2005-03-28
I'm having the same problem.  Do I need a complete 32bit chroot to use Zend?

---

### Post by yippy on 2005-03-28
I was able to get Zend 4.0.1 to successfully install and run.

I created a 32bit environment following the instructions at:
[https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id274246](https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id274246)
(I replaced all the references to sid to be hoary instead, and used the ubuntu url to download from on the dechroot command line)

The first part just links the libraries (just like the ia32 packages do right now), but that wasn't enough for the Zend installer.  I had to actually chroot into the new system to run it.  I also had to install a few other packages:
libxp6
libxt6
libxtst6

In order to install packages you'll need to copy your sources.list to the chrooted system.  On mine:
cp /etc/apt/sources.list /var/chroot/hoary-ia32/etc/apt/sources.list  

The installer wouldn't run as root, it said other packages were missing.  I don't need the server stuff so I did't worry about that.  It would run with sudo, though, so I also recommend you copy /etc/sudoers to /var/chroot/hoary-ia32/root, then chroot in and use visudo to import it into the chroot sudoers file.

I haven't gotten to using dchroot yet, so I'll report on that when I get there.

---

### Post by TheJoker on 2005-10-11
I just managed to ge Zend Studio 5 Beta 2 going, by first installing it as normal user, but I created /usr/local/Zend/ as root and gave full permissions to my user.

I then installed the JRE as descibed here:
[http://ubuntuforums.org/showpost.php?p=211395&postcount=15](http://ubuntuforums.org/showpost.php?p=211395&postcount=15)
Please note next in thread that gives the correct "ln -s"

I got this jre-1_5_0_03-linux-amd64.bin as mentioned in the thread above.
[http://public.planetmirror.com/pub/java-sun/J2SE/5.0_03/amd64/](http://public.planetmirror.com/pub/java-sun/J2SE/5.0_03/amd64/)
which installed just fine.

I then made a copy of /usr/local/Zend/ZendStudioClient-5.0.0Beta2/bin/runStudio_unix.sh and edited the copy by changing the path to the JRE to the one given by executing
which jre
In my case the new line in runStudio_unix2.sh (nice name :)) is:
/usr/bin/java -Xms16m -Xmx192m -cp ZendIDE.jar:MRJToolkitStubs.zip:sftp.jar:jhall.jar:../docs/he
lp.zip com.zend.ide.desktop.Main


Hope that helps! 

PS still haven't got Zend Studio 4 running it b0rks on the aforementioned messages as described. :( But I guess I can make do with the ZDE5B2 now... humdidum!

---

### Post by D1M on 2005-12-02
IT WORKS!

[http://www.tenshu.net/archives/2005/06/01/zend-studio-64bitness/](http://www.tenshu.net/archives/2005/06/01/zend-studio-64bitness/)
Works also with ZendStudio v5.0.0

But there are some difficulties with cyrillic fonts... :???:

---

### Post by raphaelcmf on 2008-05-29
A easy way to fix this is renaming the folder ZDE at user's home.

Regards.

> **Isengrim said:**
> Hello, today I installed ubuntu hoary,  I have everything working now (even wireless connection @ startup =D> )
But I can't install Zend Studio 4.
I have java installed 
```

root@LAPTOP:/home/anne/Desktop/ZendStudio-4_0_0a # java -version
java version "1.5.0_01"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_01-b08)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_01-b08, mixed mode)

```

If I try installing Zend I get this message everytime

```

root@LAPTOP:/home/anne/Desktop/ZendStudio-4_0_0a # ./ZendStudio-4_0_0a.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libresolv.so.2: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
current locale is not supported in X11, locale is set to CX locale modifiers are not supported, using defaultInvocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.InternalError: Current locale is not supported
        at sun.awt.motif.MWindowPeer.pSetTitle(Native Method)
        at sun.awt.motif.MWindowPeer.init(Unknown Source)
        at sun.awt.motif.MFramePeer.<init>(Unknown Source)
        at sun.awt.motif.MToolkit.createFrame(Unknown Source)
        at java.awt.Frame.addNotify(Unknown Source)
        at com.zerog.ia.installer.LifeCycleManager.f(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

```

I don't have a clue what this means (I am kinda linux n00b), can someone explain me how to fix it please.

I run the 64 bit version of hoary btw

---

