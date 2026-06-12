---
title: "JRE plugin problem in Swiftfox"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by @tticus on 2010-03-20
Hi guys,

   I have a strange problem with Swiftfox. I am using Ubuntu 9.10 with Swiftfox 3.6, and OpenJDK Runtime Environment (IcedTea6 1.6.1).

I can not get Swiftfox recognize the JRE plugin. I have a symlink 
at /usr/lib/swiftfox/plugins/ that points to /usr/lib/jvm/java-6-sun-1.6.0.15/jre/plugin/i386/ns7/libjavaplugin_oji.so and still Swiftfox would not recognize my JRE. The same symlink is at /usr/lib/mozulla/plugins 
Any ideas what could be wrong? 

Thanks, 
  @tticus

---

### Post by n0dix on 2010-03-20
Recheck with [this]("http://ubuntuforums.org/showthread.php?t=142798") guide. Step 2.

Btw, check is the symlinks are well set up. Also the permissions.

---

### Post by @tticus on 2010-03-20
The symlinks are well set when I ls the folder they are in, I can see the references. Both the symlink, both the referenced files have 777 permissions now, and it still does not work. BTW, all the other plugins are working. 
Regular Firefox was never installed on this machine. May this be the cause?

---

### Post by n0dix on 2010-03-20
Or maybe is a bug, see [this]("http://forums.getswiftfox.com/viewtopic.php?f=2&t=561").

---

### Post by n0dix on 2010-03-20
This can be promissing: [link]("http://forums.getswiftfox.com/viewtopic.php?f=2&t=492&p=1641&hilit=java+plugin#p1641").

---

### Post by @tticus on 2010-03-20
Thanks for the reply. The [link]("http://forums.getswiftfox.com/viewtopic.php?f=2&t=492&p=1641&hilit=java+plugin#p1641") you have posted worked for me. No Swiftfox restart needed. Everything worked right after executing the command.

---

