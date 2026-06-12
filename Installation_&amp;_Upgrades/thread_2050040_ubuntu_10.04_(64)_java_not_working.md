---
title: "ubuntu 10.04 (64) java not working"
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by linux83 on 2012-08-29
Hello freinds,

i have problem running java applet for any site using firefox or any browser.
i follow some instruction but isn't work for me, each time i try to open a site instead of applet, it download the java file and nothing is opening:

[http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html)

[http://blog.tersmitten.nl/how-to-install-64bit-java-jre-6u20-on-64bit-firefox-ubuntu-10-04.html](http://blog.tersmitten.nl/how-to-install-64bit-java-jre-6u20-on-64bit-firefox-ubuntu-10-04.html)

could any one help me please and thanks alot.

linux83.

---

### Post by QIII on 2012-08-29
Both of those sets of instructions are for outdated and vulnerable versions of Oracle Java 6.

The current version is Oracle Java 7 Update 6.

**You  should be aware that at the moment there is a very dangerous, very  fast-spreading exploit taking advantage of a vulnerability in Oracle  Java 7, OpenJDK 7 and IBM Java 7.  Using Java 6 is not a good  substitute, since there are some very bad critters that it is subject  to.  Until a patch is released by Oracle, you should not use the Oracle java 7 browser plugin and Mozilla is disabling it automatically, which may be the source of the behavior.  Red Hat has advised its enterprise customers to disable the browser plugin immediately.**

If what I am about to point you to will even work on Lucid, then immediately disable the Java browser plugin if it works -- both  OpenJDK if you have it and Oracle Java 7.

Again, this may NOT work on Lucid.

In the Community Java Wiki in my signature, under "Oracle Java 7", "Command line methods", click the link "Using webupd8.org's strikingly simple method".  The instructions automate the download of the files from Oracle and their installation.  Furthermore, when webupd8's installer is installed, updates to Oracle Java 7 will be installed automatically when you do your normal Ubuntu updates.  

[B]AGAIN:  Beware!  Disable the Oracle Java 7, OpenJDK 7 or IBM Java 7 browser plugins to avoid a very dangerous security issue.  You will have to simply live without the Java content until this is resolved.  My advice is to forgo the installation of Java altogether until a patch has been made available -- and this is from one of the guys who maintains the wiki!
[/B]

---

### Post by linux83 on 2012-08-30
Hello [QIII]("http://ubuntuforums.org/member.php?u=628170"),
thanks alot for your time to expand my knowledgeable about this issue before you point to the solution.

in this case, can i install java6 instead of 7, is it a valid option for ubuntu 10.04 x(64) ??

in 10.04 (32) it's working fine without any problem.

i'm stuck on x(64).

could you please point me out.

thanks alot.

---

### Post by QIII on 2012-08-30
Oracle quietly released Oracle 7 Update 7 today to fix this flaw.  If you use the method I pointed out, you will likely get Oracle Java 7 update 7 either immediately or when you do your updates.  So try to use webupd8's method.

---

### Post by linux83 on 2012-08-31
Hello QIII,
thanks alot for your help and support appreicated.
i will go ahead and follow webupd8 method.

thanks again.

Update: perfectly working without any issue.

---

