---
title: "Java...Help. (Logmein)"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by ltcolfury on 2007-05-08
I have been having nothing but major issues since this new Java has been out. I am using Ubuntu 7.04 since I upgraded from 6.10. (New install as well)  I have followed every single documentation that I could find and after 2 weeks of this I decided to see if anyone knew what my problem could be.

I am currently using JRE 1.6 as you can see below. If I go to the "Test Page" it says I don't have the newest version. I have uninstalled/installed JRE so many times already. I am using Firefox & Swiftfox. Swiftfox doesn't seem to update whenever I install JRE so I was just using Firefox. (Opera or Flock doesn't work either.)

chaz@chaz-linux:~$ java -versionjava version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

If I go to any Java page I don't see anything and get an error. I use logmein for all of my work PC's and I am unable to access any PC's.

If I do a:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
sun-java6-fonts is already the newest version.
The following packages were automatically installed and are no longer required:
  fakeroot debhelper intltool-debian sysutils po-debconf procinfo tofrodos
  gettext dpkg-dev memtester html2text
Use 'apt-get autoremove' to remove them.


In Firefox/Swiftfox and I do a "about: plugins" I see the Java Plugins listed but not sure exactly what I am looking for. (I'm not most knowledgeable in the Java area.) I do see it say "Java(TM) Plug-in Blackdown-1.4.2-02." Now, I've uninstalled that Blackdown already but it is still listed. Why so confusing and why so many Java versions? What is it I need for this to work again? Perhaps I am making this harder than it really is. (?)

Thank you very, very much in advance for any assistance you can provide.

---

### Post by bollix47 on 2007-05-08
Try running the following in a terminal:

```
sudo update-alternatives --config java 
```

Make sure the java-6-sun is the default.

---

### Post by ltcolfury on 2007-05-08
Thank you for the reply. 

I did run that command and it is set to 1.6 as I posted. (I chose that as well.) I have been using that command recently as well. I also tried using 1.5.0.11 Java previously and that doesn't work either.

My laptop uses 1.5.0.11 and it still works great. That's what I have to use but not my preference to use. I went into Synaptic and made sure I had all the same Java installs/plugins and it still doesn't work.

Needless to say it is quite frustrating.

One other thing I thought of: When I go to Sun Java and do the test, this is what I get.

[I]Description 	Your Environment
Java Runtime Vendor:
	
Sun Microsystems Inc.
Java Runtime Version
	
1.6.0
 

You do NOT have the latest version of Java software.
The latest version of Java software = Java Runtime Environment Version 6 Update 1[/I]

Isn't this the version I am using? I've downloaded/installed/uninstalled Java through Synaptic, Automatix, and even installed it with the .bin file from their site & still no luck. As I mentioned in my other post, I even reformatted my HD with just Ubuntu 7.04 (instead of updating from 6.10) to hopefully believe it would fix my issue.

---

### Post by bollix47 on 2007-05-08
Open a terminal and run the following command:

```
ls -l /usr/lib/firefox/plugins
```

Copy and paste the output here.

---

### Post by mlind on 2007-05-08
use **update-java-alternatives** instead if you installed JRE from Ubuntu's repository. Does this problem appear also with Java 1.5 ?
Java 6 is not yet suitable for production use.

---

### Post by ltcolfury on 2007-05-08
> **bollix47 said:**
> Open a terminal and run the following command:

```
ls -l /usr/lib/firefox/plugins
```

Copy and paste the output here.

Here is the output from the command.

chaz@chaz-linux:~$ ls -l /usr/lib/firefox/plugins
total 6972
lrwxrwxrwx 1 root root      39 2007-05-06 21:15 kaffeineplugin.so -> ../../mozilla/plugins/kaffeineplugin.so
-rwxr-xr-x 1 root root 7040080 2007-05-07 19:42 libflashplayer.so
lrwxrwxrwx 1 root root      39 2007-05-08 12:09 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
-rw-r--r-- 1 root root    8936 2007-04-03 11:44 libunixprintplugin.so
lrwxrwxrwx 1 root root      37 2007-05-06 20:30 libvlcplugin.so -> ../../mozilla/plugins/libvlcplugin.so
lrwxrwxrwx 1 root root      42 2007-05-04 14:28 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root      43 2007-05-04 14:28 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root      42 2007-05-04 14:28 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root      43 2007-05-04 14:28 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root      39 2007-05-04 14:28 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root      43 2007-05-04 14:28 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root      44 2007-05-04 14:28 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root      40 2007-05-04 14:28 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
-rw-r--r-- 1 root root   58656 2007-01-24 07:11 nphelix.so
-rwxr-xr-x 1 root root    5086 2007-01-24 07:11 nphelix.xpt
lrwxrwxrwx 1 root root      50 2007-05-06 21:11 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so

I don't see the firefox plugin. Perhaps that's my problem? I don't know how to get it in their.

---

### Post by ltcolfury on 2007-05-08
> **mlind said:**
> use **update-java-alternatives** instead if you installed JRE from Ubuntu's repository. Does this problem appear also with Java 1.5 ?
Java 6 is not yet suitable for production use.

I still have the same problem when I use 1.5 as well. I must have something installed that it doesn't like. 

I haven't tried: 

update-java-alternatives

If I did would I just use "-s java-6-sun" at the end of it?

Thank you very much for assisting me all those that have posted.

---

### Post by bollix47 on 2007-05-08
Your java plugin is linking to /etc/alternatives/firefox-javaplugin.so.
That will probably link to the actual jre file that firefox is using.

It should be /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so for version 6.

about:plugins in firefox should have the following:

Java(TM) Plug-in 1.6.0-b105

    File name: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0

---

### Post by mlind on 2007-05-08
> **ltcolfury said:**
> I still have the same problem when I use 1.5 as well. I must have something installed that it doesn't like. 

I haven't tried: 

update-java-alternatives

If I did would I just use "-s java-6-sun" at the end of it?

Thank you very much for assisting me all those that have posted.

To see all available options
```

update-java-alternatives -l

```

I don't have java 6 installed, but for java 1.5 it's like this
```

$ update-java-alternatives -l
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
$ sudo update-java-alternatives -s java-1.5.0-sun

```

This will also symlink java-plugin correctly, which update-alternatives doesn't seem to do.

---

### Post by ltcolfury on 2007-05-08
> **mlind said:**
> To see all available options
```

update-java-alternatives -l

```

I don't have java 6 installed, but for java 1.5 it's like this
```

$ update-java-alternatives -l
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
$ sudo update-java-alternatives -s java-1.5.0-sun

```

This will also symlink java-plugin correctly, which update-alternatives doesn't seem to do.

Wow, you are awesome! It worked! I followed exactly what you wrote. I uninstalled everything related to Java and then followed your directions. I rebooted (just in case) and I checked it and it is working again like a charm!

I really, really appreciate your assistance! Thank you very much!

---

### Post by drmbogo on 2007-05-09
Hi folks!
I followed everything above and it *almost* works!
I too am using Logmein, and am trying to do it from my Ubuntu box.
I can log in to my remote computer (FRED) but when I click remote control, I get this error:

java.security.AccessControlException: access denied (SocketPermission fred-bzoieorums.app14.logmein.com:443 connect,resolve)

I realize this may not be a java error, but, anyone else have this problem?
Also, ltcolfury, did the Java Test work after you fixed your installation? Mine still says I don't have the latest version...

Thanks to all for your help
dB

---

### Post by BigNeek on 2007-05-14
Did you figure this out?  I'm having the exact same issue.

I found this on the LMI site, but NO JOY

Note, you will need to go to Preferences > Remote Control settings and disable remote printing for the Remote Control feature to load properly and not with errors, since this isn't supported in Java on Linux. 

Thanks,

John

---

### Post by manro on 2007-05-18
> **drmbogo said:**
> Hi folks!
I followed everything above and it *almost* works!
I too am using Logmein, and am trying to do it from my Ubuntu box.
I can log in to my remote computer (FRED) but when I click remote control, I get this error:

java.security.AccessControlException: access denied (SocketPermission fred-bzoieorums.app14.logmein.com:443 connect,resolve)

I realize this may not be a java error, but, anyone else have this problem?
Also, ltcolfury, did the Java Test work after you fixed your installation? Mine still says I don't have the latest version...

Thanks to all for your help
dB

The only way I found to fix this issue was:

First uninstall sun-java6```
sudo apt-get --purge remove sun-java6-fonts sun-java6-jre sun-java6-bin sun-java6-plugin
```Then install sun-java5```
sudo apt-get install sun-java5-fonts sun-java5-jre sun-java5-bin sun-java5-plugin
```After that do the *"necessary"* links:

Firefox```
ln -fs /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/
```Swiftfox```
ln -fs /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/plugin/i386/ns7/libjavaplugin_oji.so /opt/swiftfox/plugins/
```Hope that help! :D

Regards!

---

### Post by david.rahrer on 2007-05-24
This procedure worked perfectly for me and the same LogMeIn error.  Thanks!

---

### Post by manro on 2007-05-25
> **david.rahrer said:**
> This procedure worked perfectly for me and the same LogMeIn error.  Thanks!

Good to know that! :D

Take care! ;)

---

### Post by msoucy on 2007-05-26
FINALLY! 

I fixed my logmein troubles with this thread - I had to uninstall Java 6 and re-install 5,  symlink the browser plugun and VOILA!   Success!

Thanks Everyone!

---

### Post by manro on 2007-05-26
> **msoucy said:**
> FINALLY! 

I fixed my logmein troubles with this thread - I had to uninstall Java 6 and re-install 5,  symlink the browser plugun and VOILA!   Success!

Thanks Everyone!

Great!  :p

---

### Post by saleemjavid on 2007-06-26
Thanks for the advice. This was a life saver.
:p:D:D:D:D

---

### Post by drfox on 2007-06-27
Helped me too! Thanks so much!
:D
Larry

---

### Post by manro on 2007-06-27
> **drfox said:**
> Helped me too! Thanks so much!
:D
Larry

 You're welcome! :D

Regards,
MaNRo

---

### Post by stigmate on 2007-08-25
> **manro said:**
> Firefox
Code:

ln -fs /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/

Swiftfox
Code:

ln -fs /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/plugin/i386/ns7/libjavaplugin_oji.so /opt/swiftfox/plugins/



i dont fave a folder plugins in my .mozilla folder. where else can the plugins folder be ?

thx

p.s. i didnt do anything to my firefox its normal installation from ubuntu feisty

---

### Post by david.rahrer on 2007-08-25
I noticed that too and used:
```
/usr/lib/firefox/plugins/
```
Full line to  create symlink:
```
ln -fs /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/
```
Works fine here, though I'm wondering how long before Logmein actually corrects the issue with the newer version.

I'm on Feisty with the default Firefox install.

---

### Post by RickL66 on 2007-10-22
Has anyone got this to work with 7.10 Gusty? I was able to install Java 5, and do the "fix" but when I go to my remote computer via logmein, I cannot type in anything (like the Windows login password). when I click in the password text box it just refreshes.

---

### Post by david.rahrer on 2007-10-23
I installed Gutsy, then chose Java 6 just to see how it would work, and Logmein worked fine without any workarounds.

---

### Post by glickmiller on 2007-10-23
I'm having the same problem as Rick on my Gutsy installation.

---

### Post by RickL66 on 2007-10-26
Finally got it to work. I went up to Java6 and it works now. Thanks!

---

### Post by glickmiller on 2007-10-27
> **glickmiller said:**
> I'm having the same problem as Rick on my Gutsy installation.

I ended up reinstalling Gutsy for other reasons and made sure to install only Java 6 on the new installation.  Now it works like a charm.

---

