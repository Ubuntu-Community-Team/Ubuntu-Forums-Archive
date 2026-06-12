---
title: "IcedTea - HELP!"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by iaskedalice09 on 2009-04-10
I installed the openJDK 6 package and icedtea6-plugin for Firefox. Yet the Java page I visit (there's only one, aleks.com) STILL pops up a "I don't want to work" page. I assume I have to make a symbolic link, but I can't find a file to link. Assistance please?

Thanks so much!

---

### Post by Chemical Imbalance on 2009-04-10
uninstall that plugin and install "sun-java6-plugin" instead.  It works much better than icedtea.

---

### Post by iaskedalice09 on 2009-04-10
I would prefer to use a Free Software alternative. For now I have installed sun-java6-jre but would you mind telling me where I can link the .so file? Thanks.

---

### Post by novafluxx on 2009-04-10
You'll need to install the plugin too, just installing the JRE won't install the plugin!

---

### Post by Chemical Imbalance on 2009-04-10
The free software versions simply don't work as well now.

I believe '/usr/lib64/jvm/java-6-sun/jre/lib/amd64' is what you are looking for? (unless you are using 32-bit...)

---

### Post by iaskedalice09 on 2009-04-10
Using 32bit. Which file(s) should I symbolically link? I think the second end is in the mozilla plugins folder, and I know where that is.

---

### Post by Nullack on 2009-04-10
iceadtea didnt work and there has been ubuntu bug work going on. Synch to main and try it again now that the bug has been fixed.

---

### Post by Chemical Imbalance on 2009-04-10
I don't know what you have to link to because I'm using the plugin and firefox from the repos, so it automatically links.  I tried looking through my folders, but I can't tell you where atm.

---

### Post by Zorael on 2009-04-11
The plugin itself is at **/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so**, provided you have the icedtea6-plugin package installed. I'd make a symbolic link in **/usr/lib/mozilla/plugins/** to one of the java plugin symlinks in **/etc/alternatives/**, and then make sure it points to the real file with **sudo update-alternatives --config <said symlink>**. I think it defaulted to some xulrunner*javaplugin.so alternative on my system.

The bug, by the way, has been fixed. See [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/344705](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/344705).

---

