---
title: "Strange Java errors in chromium-browser after upgrade"
date: 2013-08-24
forum: Installation &amp; Upgrades
---

### Post by jesushlincoln on 2013-08-24
Hey all,

I recently upgraded from 11.04 to 12.04 (a little late, I know) on my EEE PC so that I could upgrade pepper flash and java in chromium so that my mother could keep playing these horrid, poorly-coded little games on a website called pogo.com. Just today, although the flash-based games still continue to work fine, the java games refused to load altogether giving an error that I MUST upgrade to Oracle Java 7 Update 25 due to necessary security updates.

I followed some instructions online that led to me adding a webupd8 PPA to install the "oracle-java7-installer" package via apt-get. Running "java -version" tells me it's Java 7 Update 25, but chromium still reports the plugin as being out-of-date even after symbolically linking the updated libnpjp2.so to the right directories. When running it from a terminal, the following error shows up whenever I try to load any java applet:

```
Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/jvm/java-7-oracle/jre/lib/i386/libnio.so: /usr/lib/chromium-browser/libs/libnet.so: version `SUNWprivate_1.1' not found (required by /usr/lib/jvm/java-7-oracle/jre/lib/i386/libnio.so)    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1957)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1882)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1864)
    at java.lang.Runtime.loadLibrary0(Runtime.java:849)
    at java.lang.System.loadLibrary(System.java:1087)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
    at java.security.AccessController.doPrivileged(Native Method)
    at sun.nio.ch.Util.load(Util.java:487)
    at sun.nio.ch.IOUtil.<clinit>(IOUtil.java:351)
    at sun.nio.ch.Util.<clinit>(Util.java:48)
    at sun.nio.ch.FileChannelImpl.<clinit>(FileChannelImpl.java:1132)
    at java.io.FileInputStream.getChannel(FileInputStream.java:364)
    at com.sun.deploy.util.SyncFileAccess.openLockFileObject(Unknown Source)
    at com.sun.deploy.util.SyncFileAccess.openLockFileInputStream(Unknown Source)
    at com.sun.deploy.config.ClientConfig.loadPropertiesFile(Unknown Source)
    at com.sun.deploy.config.ClientConfig.refreshProperties(Unknown Source)
    at com.sun.deploy.config.ClientConfig.init(Unknown Source)
    at com.sun.deploy.config.ClientConfig.<init>(Unknown Source)
    at com.sun.deploy.config.PluginServerConfig.<init>(Unknown Source)
    at sun.plugin2.main.server.JVMManager.<init>(Unknown Source)
    at sun.plugin2.main.server.JVMManager.getManager(Unknown Source)
    at sun.plugin2.main.server.MozillaPlugin.maybeStartApplet(Unknown Source)
    at sun.plugin2.main.server.MozillaPlugin.setWindow(Unknown Source)

```

I was able to find some vaguely similar errors on Google, but every single instance was somebody programming new Java code and having the errors pop up during compilation; nobody else seems to be or have been experiencing this same issue with Oracle Java 7 Update 25. If anybody can give me some leads or info on what I might do (other than completely uninstalling and reinstalling Ubuntu 12.04 and seeing if it suddenly starts working), that would be MUCH appreciated.

---

### Post by valvegrid on 2013-08-25
I've got a similar problem, I've tried all sorts of links and nothing works, I would have thought this should have worked:-

```
cd /usr/lib/chromium-browser/plugins
```

```
sudo ln -s /usr/lib/jvm/java-7-oracle/jre/lib/i386/libnpjp2.so libnpjp2.so
```

I can see the link in the plugins folder and it points to the right place. 

Both Firefox and Opera have found [COLOR=#000000]Java 7 Update 25, it will be interesting to see if you get any replies on what we are doing wrong. We are probably are doing something wrong, but I can't see it.[/COLOR]

---

### Post by nico_r2 on 2013-10-03
Same problem here after Upgrade from 12.10 to 13.04.

about:plugins shows
> [COLOR=#000000][FONT=Ubuntu]**Java(TM)**[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]- Version: 10.40.2[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]Next Generation Java Plug-in 10.40.2 for Mozilla browsers
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu][TABLE]
[TR]
[TD="class: plugin-details-label"]Name:[/TD]
[TD]Java(TM) Plug-in 10.40.2[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Description:[/TD]
[TD]Next Generation Java Plug-in 10.40.2 for Mozilla browsers[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Version:[/TD]
[TD]10.40.2[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Location:[/TD]
[TD]/usr/lib/jvm/java-7-oracle/jre/lib/i386/libnpjp2.so[/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]
Plugin is loaded via symlinks in /usr/lib/mozilla/plugins and works absolutely fine in Firefox. Has something changed in Chromium's libnet.so?

"strings /usr/lib/chromium-browser/libs/libnet.so | grep SUNWprivate" returns nothing.


[/FONT][/COLOR]

---

### Post by EdRoxter on 2013-10-25
Upgrading xUbuntu to 13.10 Saucy with Chromium 29.x makes everything work again. Pity there's no backport or PPA that ports the absolutely recent Chromium versions to 13.04.

---

### Post by erevilla on 2013-11-12
Hi.

Today I did a dist-upgrade on my 12.04 (Precise) and I had exactly the same issue with Chromium 30.

I uninstalled chromium-browser packages and installed versión 29 from ppa:chromium-daily/stable:

$ sudo add-apt-repository ppa:chromium-daily/stable
$ sudo apt-get install chromium-browser=29.0.1547.57-0ubuntu0~cm4 chromium-browser-l10n=29.0.1547.57-0ubuntu0~cm4

Now, the applets are working again.

Regards.
Erny

---

### Post by erevilla on 2013-11-12
I've just submitted a bug: [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1250550](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1250550)

---

