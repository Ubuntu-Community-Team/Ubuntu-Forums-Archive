---
title: "Current jaunty OpenJDK+IcedTea plugin and Firefox = grey box, process at 100% cpu"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Zorael on 2009-03-17
I'm running Kubuntu Jaunty x86, installed as alpha 5 but with all packages kept up-to-date with aptitude full-upgrade.

So I thought I'd try out OpenJDK instead of Sun Java.
```
$ sudo aptitude install **openjdk-6-jdk icedtea6-plugin [COLOR="Red"]pulseaudio_**[/COLOR]
```
**openjdk-6-jdk** depends on **openjdk-6-jre**, so I get all the OpenJDK packages I need. However, **openjdk-6-jre** *recommends* **pulseaudio** - which I don't want - so I explicitly tell it to refrain from installing it. And of course **icedtea6-plugin** to get the browser plugin.
```
$ dpkg -L icedtea6-plugin | grep -i plugin | grep openjdk
[COLOR="Lime"]**/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so**[/COLOR]
```
Proof that everything is as it should be:
```
$ java -version
java version "1.6.0_0"
[COLOR="Lime"]OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu4)
OpenJDK Server VM (build 14.0-b08, mixed mode)[/COLOR]

$ ls -l **/usr/lib/mozilla/plugins/*java***
lrwxrwxrwx 1 root root 45 2009-03-17 18:29 /usr/lib/mozilla/plugins/javaplugin.so -> **/etc/alternatives/xulrunner-1.9-javaplugin.so**

$ ls -l **/etc/alternatives/xulrunner-1.9-javaplugin.so**
lrwxrwxrwx 1 root root 57 2009-03-10 20:52 /etc/alternatives/xulrunner-1.9-javaplugin.so -> **/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so**

$ ls -l **/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so**
-rw-r--r-- 1 root root 215300 2009-03-14 03:17 [COLOR="Lime"]**/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so**[/COLOR]
```
In Firefox, **about:plugins** page:
> [SIZE="4"]IcedTea Java Web Browser Plugin[/SIZE]

    File name: [COLOR="Lime"]IcedTeaPlugin.so[/COLOR]
    The IcedTea Java Web Browser Plugin 1.4.1 (6b14-1.4.1-0ubuntu4) executes Java applets.

All seems well. In reality, I get a grey box when I should get a java applet, and the applet viewer process maxes out cpu usage; see the first screenshot. Worth mentioning is that Konqueror has no issues displaying the very same applet; see the second screenshot. Also, Sun's Java and its plugin package does the job marvellously even in Firefox, so were this an installation meant for everyday (desktop) use, I'd default to that. That's beside the point, though.

```
$ uname -a
Linux lethe 2.6.28-10-generic #32-Ubuntu SMP Mon Mar 16 02:49:09 UTC 2009 i686 GNU/Linux

$ apt-cache policy openjdk-6-jre icedtea6-plugin firefox
openjdk-6-jre:
  Installed: 6b14-1.4.1-0ubuntu4
  Candidate: 6b14-1.4.1-0ubuntu4
  Version table:
 *** 6b14-1.4.1-0ubuntu4 0
        500 http://se.archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status
icedtea6-plugin:
  Installed: 6b14-1.4.1-0ubuntu4
  Candidate: 6b14-1.4.1-0ubuntu4
  Version table:
 *** 6b14-1.4.1-0ubuntu4 0
        500 http://se.archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status
firefox:
  Installed: 3.0.7+nobinonly-0ubuntu1
  Candidate: 3.0.7+nobinonly-0ubuntu1
  Version table:
 *** 3.0.7+nobinonly-0ubuntu1 0
        500 http://se.archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status
```


Any ideas? I don't really see what I've done wrong, but obviously Firefox disagrees.

---

### Post by flammon on 2009-03-27
I'm having the same problem. Did you submit a bug report?

---

