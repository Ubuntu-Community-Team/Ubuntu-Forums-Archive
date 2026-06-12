---
title: "JDownloader wont start the downloads"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by Don_Shifty on 2008-03-10
hello
i recently installed the JDownloader to manage my Rapidshare downloads... but when i want to start the downloads they just stay "in queue" and never start. here is the log file:

10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> Exception in thread "JD-StartDownloads" java.lang.NoClassDefFoundError: com/sun/image/codec/jpeg/ImageFormatException
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.captcha.JAntiCaptcha.createLetterDBFormMTH(JAntiCaptcha.java:341)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.captcha.JAntiCaptcha.loadMTHFile(JAntiCaptcha.java:318)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.captcha.JAntiCaptcha.<init>(JAntiCaptcha.java:162)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.utils.JDUtilities.getCaptcha(JDUtilities.java:738)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.plugins.Plugin.getCaptchaCode(Plugin.java:1642)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.plugins.host.Rapidshare.doFreeStep(Rapidshare.java:643)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.plugins.host.Rapidshare.doStep(Rapidshare.java:433)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.plugins.PluginForHost.doStep(PluginForHost.java:183)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.plugins.PluginForHost.doNextStep(PluginForHost.java:64)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.controlling.SingleDownloadController.run(SingleDownloadController.java:197)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> Caused by: java.lang.ClassNotFoundException: com.sun.image.codec.jpeg.ImageFormatException
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.net.URLClassLoader$1.run(URLClassLoader.java:221)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.security.AccessController.doPrivileged(Native Method)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.net.URLClassLoader.findClass(URLClassLoader.java:209)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader.loadClass(ClassLoader.java:324)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader.loadClass(ClassLoader.java:269)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:337)
10-Mar-2008 20:48:58 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	... 10 more
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> Exception in thread "JD-StartDownloads" java.lang.NoClassDefFoundError: com/sun/image/codec/jpeg/ImageFormatException
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.captcha.JAntiCaptcha.createLetterDBFormMTH(JAntiCaptcha.java:341)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.captcha.JAntiCaptcha.loadMTHFile(JAntiCaptcha.java:318)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.captcha.JAntiCaptcha.<init>(JAntiCaptcha.java:162)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.utils.JDUtilities.getCaptcha(JDUtilities.java:738)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.plugins.Plugin.getCaptchaCode(Plugin.java:1642)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.plugins.host.Rapidshare.doFreeStep(Rapidshare.java:643)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.plugins.host.Rapidshare.doStep(Rapidshare.java:433)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.plugins.PluginForHost.doStep(PluginForHost.java:183)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.plugins.PluginForHost.doNextStep(PluginForHost.java:64)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at jd.controlling.SingleDownloadController.run(SingleDownloadController.java:197)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> Caused by: java.lang.ClassNotFoundException: com.sun.image.codec.jpeg.ImageFormatException
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.net.URLClassLoader$1.run(URLClassLoader.java:221)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.security.AccessController.doPrivileged(Native Method)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.net.URLClassLoader.findClass(URLClassLoader.java:209)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader.loadClass(ClassLoader.java:324)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader.loadClass(ClassLoader.java:269)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:337)
10-Mar-2008 20:49:39 - SEVERE [jd.utils.JDUtilities$2(write)] -> 	... 10 more

thanks for the help!

---

### Post by jonnylinuxnerd on 2008-04-20
Delete jDownloader and re-download the lastest version off the official site. That could work.

BTW Where did you actually install jDownloader?

---

### Post by coco banderos on 2008-06-09
got this to work:

1)  make a directory for JDownloader

```

mkdir JDownloader

```

2)  Move the JDownloader rar file into the new directory
```

mv JDownloader_01475.rar JDownloader

```

3)  CD into the new directory
```

cd JDownloader

```

4)  Make a directory called 'libs'
```

mkdir libs

```

5)  Move jl1.0.jar into the libs directory
```

mv jl1.0.jar libs/.

```

6)  Run JDownloader
```

java -jar JDownloader.jar

```

JDownloader should download the rest of the files you'll need.

Hope it works for you.

---

