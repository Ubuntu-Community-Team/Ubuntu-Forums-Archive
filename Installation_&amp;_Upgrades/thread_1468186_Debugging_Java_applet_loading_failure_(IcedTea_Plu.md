---
title: "Debugging Java applet loading failure (IcedTea Plugin in Ubuntu 10.04)"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by acharseth on 2010-05-01
I have just installed Ubuntu 10.04. When trying to run a Java Applet on a web page I discovered that Java is not installed in 10.04 and the SUN Java JRE is not available to install any more so I installed the OpenJDK and IcedTea Plugin:

java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK 64-Bit Server VM (build 14.0-b16, mixed mode)
Java version       : 1.6.0_18
Java vendor        : Sun Microsystems Inc.
Java vendor url    : [http://java.sun.com/](http://java.sun.com/)
Java class version : 50.0
OS NAME            : Linux
OS Arch            : amd64
OS Version         : 2.6.32-21-generic

I use Firefox 3.6.3.

Most applets work fine but one specific, for me a very important one, dos not. Specifically the log inn applet used in my net bank: [http://www.dnbnor.no](http://www.dnbnor.no). See login entry on top left.

After entering userID I am redirected to a page giving the following error message:
HTTP 404 - The resource cannot be located. The file cannot be found.         

This applet runs fine in Windows.

I have started Firefox in a terminal window but do not get any error messages there when trying to start the applet.

The applet runs fine in Opera (though slow start up) in Ubuntu 10.04. Opera does not use plug in but run the applet directly from JRE. This indicates that the problem could be in the IcedTea plugin.

How can I debug this problem to get it reported?

Best regards,
Arne

---

### Post by TJSL on 2010-05-01
I am a new Ubuntu user and using 10.04.  I may be having a similar problem.  It does not appear that I can open applets.  Uninstalling icedtea eliminated error that applet could not initialize at the bottom of the browser.  See [http://ubuntuforums.org/showthread.php?t=767222](http://ubuntuforums.org/showthread.php?t=767222)

---

### Post by acharseth on 2010-05-02
Uninstalling IcedTea plugin just makes **all** applets not work. I guess uninstalling IcedTea plugin works for those who have a conflicting java installation with both SUN JVM plugin and IcedTea plugin. "sudo update-alternatives --config java" as mentioned in the forum thread you link to is also a way to resolve such a conflict. Was this the case for you? Did you have SUN JVM installed? How did you instal SUN JVM. I found another thread describing how to manually install SUN JVM (since Ubuntu seem to no longer support SUN JVM) but then I have to also manually upgrade it so this is no ideal solution.

I guess the solution is to install SUN JVM but I would like to first debug the IcedTea plug in so that I can report the problem. So any tip on how to debug it is appreciated.

Arne

---

### Post by josteinaj on 2010-05-08
> **acharseth said:**
> Most applets work fine but one specific, for me a very important one, dos not. Specifically the log inn applet used in my net bank: [http://www.dnbnor.no](http://www.dnbnor.no).

I'm having the exact same problem with DnB NOR and BankID. Did you find a solution?

---

### Post by acharseth on 2010-05-08
I have not found a solution yet. 
I suspect it is a problem with the java version check DnB NOR uses and not with the IcedTea plug in as such (since it is working with java applets on other sites and the redirect seem to come before the start up of the applet). I have reported the problem to DnB NOR and received some tip that did not help.
To get attention to the problem at DnB NOR/BankID I suggest that every DnB NOR customer with this problem report it to DnB NOR.

---

### Post by dabpayi on 2010-05-11
Hello,

I have similar problem but on different site, this is what I do to solve the problem:
- disable/uninstall IcedTea plugin then replace it with sun-java6-plugin
- replace openjdk-jre with sun-java6-jre

Btw, the sun-java packages in 10.04 has been moved to partner repositories ( [http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html) ). Notice: do not copy paste the add-apt-repository from the site, some how the " character is not right. And then run:
```
update-alternatives --config java
``` to select the sun jre.

---

### Post by acharseth on 2010-05-11
Hi!

This could be a solution and is the same solution my bank suggest (but they suggest only replace IcedTea plugin with the SUN plugin).

The problem with this solution, as I understand it, is that the plugin (and JRE if you choose to use SUN JRE) will not be automatically updated but must be done by you manually. This poses a security threat. Especially for a bank application like the one I use. I therefore suggest that everyone with this problem urge the web site to support the IcedTea plug in.

Arne

---

### Post by josteinaj on 2010-05-11
It still doesn't work for me.

I've sent an email to both DnB NOR and BankID. I suspect that BankID is the one that will have to fix this.

---

### Post by josteinaj on 2010-05-12
I got this PDF from DnB NOR explaining how to make Java work in Ubuntu 10.04. I'll try it when I get home, but it seems to just be a graphical guide to what dabpayi suggested. It's in norwegian, but it should be clear from the screenshots what you are supposed to do.

Also, I just noticed that dabpayi also suggested uninstalling IcedTea as well...

I'll try again when I get home.

---

### Post by acharseth on 2010-05-14
Hi!

Uninstalling IcedTea plugin (keeping the OpenJDK) and then installing SUN plugin worked for me.
As I said previously it is not a perfect solution though since I have to manually update the plugin when new updates arrive. I have asked DNBNOR to support the IcedTea plugin to get a secure auto update installation.

Arne

---

### Post by josteinaj on 2010-05-14
I also tried myself now, and uninstalling IcedTea worked for me as well.

---

### Post by lapalorky on 2010-06-08
I have the same issue with the DnBNOR website and BankID. But none of these solutions work for me.

Instead I have to delete the /home/[username]/.java directory every time I want to use the DnBNOR website. Then the BankID-applet shows up and I can log in. Of course I have to confirm the applet every time, like it has never run before.
It looks like there is something written in that folder that messes up the loading of the applet a second time.

Any thoughts?

---

### Post by lapalorky on 2010-06-09
Disabling Java-caching makes it work permanently for me.

---

### Post by onamattuphere on 2010-06-29
Thanks so much. I rejoice in the fact that there are people like you who are a part of the Linux/Ubuntu community who shares such vital information. We are after all talking about BankID.
Worked for me and I use Nordea; uninstalled icedtea and installed the sun java plugin.
You should mark this thread solved in my opinion.

Tusen takk.

---

### Post by vmohanraaj on 2012-07-30
Me too facing same problem. This is because Icedtea plugin not 100% compatible with old sun-java6 applets. It is better to go for sun-java6-plugin. Any how ubuntu repositories not have sun-java6.

This is a nice [how to for installing sun-java6 plugin in ubuntu]("http://infoware.org/847/install-sun-java6-jre-sun-java6-plugin-and-sun-java6-jdk-in-ubuntu/").

---

