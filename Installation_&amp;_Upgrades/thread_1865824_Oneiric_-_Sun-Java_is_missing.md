---
title: "Oneiric - Sun-Java is missing"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by ShakataGaNai on 2011-10-20
It seems that the sun-java packages have been removed from the Ubuntu Partners PPA for Oneiric? Is this correct? Where are we supposed to get the packages now?

---

### Post by oldos2er on 2011-10-20
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by ShakataGaNai on 2011-10-20
> **oldos2er said:**
> [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

So they did tactically nuke it from the Repo? That's obnoxious.  I like Ubuntu _BECAUSE_ everything's in the repo (and/or people provide other repos).  Sigh...

---

### Post by mpkossen on 2011-11-01
They didn't "nuke" it from the repo and it wasn't anything obnoxious. It was a planned move and it makes sense. Please read [http://robilad.livejournal.com/90792.html](http://robilad.livejournal.com/90792.html) for more information. If you would still like to use Sun/Oracle java, either keep using Natty or install it yourself (or wait for it to appear in a PPA).

---

### Post by ShakataGaNai on 2011-11-01
> **mpkossen said:**
> They didn't "nuke" it from the repo and it wasn't anything obnoxious. It was a planned move and it makes sense. Please read [http://robilad.livejournal.com/90792.html](http://robilad.livejournal.com/90792.html) for more information. If you would still like to use Sun/Oracle java, either keep using Natty or install it yourself (or wait for it to appear in a PPA).

Or wait for it to appear in a PPA?  So they took it out of the existing repo's (for whatever reason, doesn't much matter), and didn't provide any other in-repo options.  Obnoxious.

---

### Post by TBABill on 2011-11-01
It is in a PPA. I'll try to find it for you. I have it on my 11.10 install because open source still is inferior on some sites for now. I'll search Oneiric and Sun Java and hopefully find you the resource I used. I think it was off a website, not the forums.

---

### Post by TBABill on 2011-11-01
You can add the following PPA: **ppa:ferramroberto/java** and then ```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

---

### Post by reaxion on 2011-11-04
According to Oracle, OpenJDK is now the official version of Java.  [http://blogs.oracle.com/henrik/entry/moving_to_openjdk_as_the](http://blogs.oracle.com/henrik/entry/moving_to_openjdk_as_the)

To install in Ubuntu, just type in:

    sudo apt-get install openjdk-7-jdk

That'll get everything working for you without problems.  Enjoy.

---

### Post by jalmargyyk on 2011-11-04
Too bad that OpenJDK doesn't seem to work with Juniper Network Connect (VPN Client). Applet loads fine, but the connection times out immediately.

---

### Post by i8bugs on 2011-11-04
reaxion- just tried "sudo apt-get install openjdk-7-jdk" and seemed to be a successful install, but Firefox still can't pick it up.  I'm using Scottrade trading streamer and I get a popup saying it can't detect Java.  Suggestions?

---

### Post by ACupOfCoffee on 2011-11-04
If you read the above linked document, it says that OpenJDK is the official reference implementation, not the official Oracle/Sun release. Installing OpenJDK 7 will not install a plugin because it is just a compiler. You can download Sun JRE 6u29 from java.com

---

### Post by edantes on 2011-11-06
> **ACupOfCoffee said:**
> If you read the above linked document, it says that OpenJDK is the official reference implementation, not the official Oracle/Sun release. Installing OpenJDK 7 will not install a plugin because it is just a compiler. You can download Sun JRE 6u29 from java.com

I am still confused about the veredict on this issue.  I tried OpenJDK 6 and 7 with respective plugins and my bank's security applet goes into a loop, quickly using 100% of the processor.

The problem goes away by using the sun-java-6 packages.  Is the problem with the applet itself, with OpenJDK or with the plugin?

---

### Post by vangop on 2011-11-06
Hi!
I was very cautious with open jdk before 11.10, used only sun.
But now I think it's the way to go. Ive installed openjdk6 + icedtea6-plugin and don't have any problems with java apps or applets.
If you don't need java7, I'd go with icedtea6-plugin and openjdk-6-jdk.

---

### Post by edantes on 2011-11-06
> **vangop said:**
> Hi!
I was very cautious with open jdk before 11.10, used only sun.
But now I think it's the way to go. Ive installed openjdk6 + icedtea6-plugin and don't have any problems with Java apps or applets.
If you don't need java7, I'd go with icedtea6-plugin and openjdk-6-jdk.

I tried the openjdk6 + icedtea6-plugin combination  and it breaks with this particular banking security applet.  Not from first hand experience, but from other reports in forums and blogs, other security applets and games have problems with OpenJDK. 

From [Oracle's semi-official blog]("https://blogs.oracle.com/henrik/entry/moving_to_openjdk_as_the"), it looks like OpenJDK is the reference implementation beginning with Java 7. Maybe the rub is with the icedtea plugin?

---

### Post by MAFoElffen on 2011-11-06
> **i8bugs said:**
> reaxion- just tried "sudo apt-get install openjdk-7-jdk" and seemed to be a successful install, but Firefox still can't pick it up.  I'm using Scottrade trading streamer and I get a popup saying it can't detect Java.  Suggestions?
Sorry about jumping into this late...

I go to Java.com to test my java:
[http://java.com/en/download/installed.jsp]("http://java.com/en/download/installed.jsp?jre_version=1.6.0_22&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.38-12-generic")

This page is the industry standard for Java. If it can't be picked up on this page, something is wrong, not working or not in compliance with the standard.

Even though people say that the sunjdk and openjdk are the same- There have been some differences. I don't know how it is now, but the openjdk didn't used to get picked up by this, my javascript app's weren't going right, my past Sun (later Oracle) Java dev tool suites weren't working right... so I installed Java from here and have never had a problem with them since. (originally was the sunjdk)

I bookamark that page and go to it every once in a while to ensure I'm up to date. I also have this installed on all my instances of Windows, but they "notify" on boot if an update is available.

---

### Post by Pjotr123 on 2011-11-12
> **MAFoElffen said:**
> 
I go to Java.com to test my java:
[http://java.com/en/download/installed.jsp?jre_version=1.6.0_22&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.38-12-generic](http://java.com/en/download/installed.jsp?jre_version=1.6.0_22&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.38-12-generic)

This page is the industry standard for Java. If it can't be picked up on this page, something is wrong, not working or not in compliance with the standard.

You gave the link *after* the test on your machine.... :)
The correct link is (pre-test):
[http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)

For the record: my how-to for Oracle (Sun) Java is fully up to date, so feel free to use it:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by negativeSero on 2011-11-15
> **Pjotr123 said:**
> You gave the link *after* the test on your machine.... :)
The correct link is (pre-test):
[http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)

For the record: my how-to for Oracle (Sun) Java is fully up to date, so feel free to use it:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)


Thanks for the how-to. Worked like a charm.

---

