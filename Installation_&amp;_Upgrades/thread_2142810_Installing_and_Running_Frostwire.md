---
title: "Installing and Running Frostwire"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by lege101 on 2013-05-06
I have already read all the websites and the other forum topics regarding this and I have watched about 5 youtube videos, it all comes down to nothing is working. I have an updated version of sun java, 

[COLOR=#ff0000]user@ChrUbuntu:~$ java -version[/COLOR]
[COLOR=#ff0000]java version "1.7.0_21"[/COLOR]
[COLOR=#ff0000]Java(TM) SE Runtime Environment (build 1.7.0_21-b11)[/COLOR]
[COLOR=#ff0000]Java HotSpot(TM) Server VM (build 23.21-b01, mixed mode)[/COLOR]

and I have frostwire downloaded and it still isn't running properly, I even have the icon for it but it doesn't open. I get this message every time I try to run it through terminal as well

[COLOR=#ff0000]user@ChrUbuntu:~$ frostwire[/COLOR]
[COLOR=#ff0000]HOSTNAME IS ChrUbuntu[/COLOR]
[COLOR=#ff0000]Starting FrostWire...[/COLOR]
[COLOR=#ff0000]Java exec found in PATH. Verifying...[/COLOR]
[COLOR=#ff0000]Suitable java version found [java = 1.7.0_21][/COLOR]
[COLOR=#ff0000]Configuring environment...[/COLOR]
[COLOR=#ff0000]Loading FrostWire:[/COLOR]
[COLOR=#ff0000]CLASSPATH SET TO: .:lw-alexandria.jar:lw-azureus.jar:lw-common.jar:lw-jdownloader.jar:lw-medialib.jar:lw-osx_stub.jar:lw-resources.jar:lw-setting.jar:commons-logging.jar:dnsjava-2.1.3.jar:frostwire.jar:gettext-commons.jar:gson-1.4.jar:h2-1.3.164.jar:httpclient-4.0.jar:httpcore-4.0.1.jar:laf-widget.jar:lucene-3.5.0.jar:messages.jar:MRJAdapter.jar:netx.jar:splash.jar:substance.jar:trident.jar[/COLOR]
[COLOR=#ff0000]OS: linux[/COLOR]
[COLOR=#ff0000]java.lang.UnsatisfiedLinkError: /opt/java/32/jdk1.7.0_21/jre/lib/i386/xawt/libmawt.so: libXtst.so.6: cannot open shared object file: No such file or directory[/COLOR]
[COLOR=#ff0000]    at java.lang.ClassLoader$NativeLibrary.load(Native Method)[/COLOR]
[COLOR=#ff0000]    at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1939)[/COLOR]
[COLOR=#ff0000]    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1864)[/COLOR]
[COLOR=#ff0000]    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1825)[/COLOR]
[COLOR=#ff0000]    at java.lang.Runtime.load0(Runtime.java:792)[/COLOR]
[COLOR=#ff0000]    at java.lang.System.load(System.java:1059)[/COLOR]
[COLOR=#ff0000]    at java.lang.ClassLoader$NativeLibrary.load(Native Method)[/COLOR]
[COLOR=#ff0000]    at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1939)[/COLOR]
[COLOR=#ff0000]    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1864)[/COLOR]
[COLOR=#ff0000]    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1846)[/COLOR]
[COLOR=#ff0000]    at java.lang.Runtime.loadLibrary0(Runtime.java:845)[/COLOR]
[COLOR=#ff0000]    at java.lang.System.loadLibrary(System.java:1084)[/COLOR]
[COLOR=#ff0000]    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)[/COLOR]
[COLOR=#ff0000]    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)[/COLOR]
[COLOR=#ff0000]    at java.security.AccessController.doPrivileged(Native Method)[/COLOR]
[COLOR=#ff0000]    at sun.java2d.Disposer.<clinit>(Disposer.java:59)[/COLOR]
[COLOR=#ff0000]    at javax.imageio.stream.FileCacheImageInputStream.<init>(FileCacheImageInputStream.java:114)[/COLOR]
[COLOR=#ff0000]    at com.sun.imageio.spi.InputStreamImageInputStreamSpi.createInputStreamInstance(InputStreamImageInputStreamSpi.java:69)[/COLOR]
[COLOR=#ff0000]    at javax.imageio.ImageIO.createImageInputStream(ImageIO.java:357)[/COLOR]
[COLOR=#ff0000]    at javax.imageio.ImageIO.read(ImageIO.java:1397)[/COLOR]
[COLOR=#ff0000]    at com.limegroup.gnutella.gui.Main.showInitialSplash(Unknown Source)[/COLOR]
[COLOR=#ff0000]    at com.limegroup.gnutella.gui.Main.main(Unknown Source)[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]******************************************************************[/COLOR]
[COLOR=#ff0000]Something went wrong with FrostWire.[/COLOR]
[COLOR=#ff0000]Maybe you're using the wrong version of Java?[/COLOR]
[COLOR=#ff0000](FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)[/COLOR]
[COLOR=#ff0000]The version of Java in your PATH is:[/COLOR]
[COLOR=#ff0000]java version "1.7.0_21"[/COLOR]
[COLOR=#ff0000]Java(TM) SE Runtime Environment (build 1.7.0_21-b11)[/COLOR]
[COLOR=#ff0000]Java HotSpot(TM) Server VM (build 23.21-b01, mixed mode)[/COLOR]

So, what am I doing wrong or what can I do to fix this?



Kind regards,
Lege

---

