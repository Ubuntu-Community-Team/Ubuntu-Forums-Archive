---
title: "problem with java plugin"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by sandy0594 on 2011-08-20
Hi all,my OS version is Ubuntu 10.10.I have Java installed in my machine.But,when it comes to web browser(Firefox) I can't see Java plug-in in the Add ons.Can anyone tell me what's the cause of this issue.

```

sandy@ubuntu:~$ java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.9) (6b20-1.9.9-0ubuntu1~10.10.2)
OpenJDK Server VM (build 19.0-b09, mixed mode)


```When I go to this web page([http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp)) a message appears saying "Something is wrong.Java is not working"

---

### Post by Sef on 2011-08-20
Have you added ice tea?  It is the plug in for Open JDK and available in the repositories.

---

### Post by sandy0594 on 2011-08-20
sorry for my ignorance,what's this ice tea anyway.By installing java in our machine doesn't it get added to browser automatically.In windows it usually does.

---

### Post by sandy0594 on 2011-08-21
With your suggestion from the above i created a symbolic link in the mozilla directory.But,still Java plugin doesn't showup in firefox addons menu.

```

sandy@ubuntu:~$ sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.26/jre/plugin/i386/ns/libjavaplugin_oji.so /usr/lib/mozilla/plugins

sandy@ubuntu:~$ sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.26/jre/plugin/i386/ns/libjavaplugin_oji.so /usr/lib/firefox-6.0/plugins

```

I even added in firefox plugins directory,but to vain.What might be the problem?

---

### Post by dino99 on 2011-08-21
sudo update-alternatives --config java

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by sandy0594 on 2011-08-21
IcedTea is working for java web pages.Thanks all for your replies.

---

