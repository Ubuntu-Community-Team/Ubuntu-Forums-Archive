---
title: "[SOLVED] Which of the 4 x-application-vm (java) plugin options  do I choose?"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by hanzj on 2008-04-07
hi, folks. i'm using firefox (ver 3 beta 5) and clicked on a link that is "application/x-java-vm". Firefox is presenting me with 4 plugin choices.

 1) GCJ Web Browser Plugin.
 2) Java(TM) Plug-in, Java  SE 6.
 3) The Java (TM) plug-in, Java SE 5.0.
 4) The GCJ Web Browser Plugin (using IcedTea). 

How in the world should one choose? What should one choose? What are the differences between the 4?


on xubuntu 8.04 beta

---

### Post by QenBirQeni on 2008-04-07
Select option 4, or better yet, use aptitude (or apt-get) to install the java runtime environment, with plugins:

$ sudo aptitude install icedtea-java7-bin icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin

---

### Post by hanzj on 2008-04-07
What's the diff between "Option 4" and your sudo aptitude command?

---

### Post by hanzj on 2008-04-07
What's the diff between "Option 4" and your sudo aptitude command?

---

### Post by QenBirQeni on 2008-04-08
option 4 installs the plugin for the browser - sudo command install the java development kit environment for your system

---

### Post by hanzj on 2008-04-08
do i need the "sudo command" if i'm not going to be developing anything?

---

### Post by QenBirQeni on 2008-04-08
sorry if i'm confusing you. in order for you to "install" an application you need administrator privileges. jdk is used by many applications, therefore it may be a good idea to install it. it is entirey up to you - I did, since there are some applets I use for school and work. Again, the "sudo" command gives you the ability to install,update, and make changes to your system. For example, if you wanted to update your system, ubuntu won't let just any user update it: only super users can, such as system administrators:

[INDENT]$ sudo aptitude update[/INDENT]


Java Development Kit (JDK) is the technical name for Java SE. Sorry to sound a tad morose, but Java is used pretty much everywhere, so go ahead and install it:

[INDENT]$ sudo aptitude install icedtea-java7-bin icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin[/INDENT]

If you don't like to use the terminal, use Synaptic, Adept, or whatever other GUI package manager you have available. Let me know if you need any further help

---

### Post by hanzj on 2008-04-20
Can someone confirm what QenBirQeni recommends, namely, Option 4?

---

### Post by QenBirQeni on 2008-04-20
Here's two links to confirm your hesitation: 

Installing sun java5 in ubuntu:
[https://jdk-distros.dev.java.net/ubuntu.html]("https://jdk-distros.dev.java.net/ubuntu.html")

Google search results for "Java in ubuntu":
[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=java+in+ubuntu](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=java+in+ubuntu)

---

### Post by hanzj on 2008-04-20
ok. qenbirqeni.
i'm installing sun java6. i'm on hardy heron. when i do a search in synaptic, there is sun java 6. there is no java5. 

If option 4 is the best, why does firefox allow a user to choose options 1, 2, and 3?
Thanks.

---

### Post by mardawi on 2008-04-20
option 4 is not the absolutely best choice! it is just QenBirQeni's opinion

Here is a brief explanation of each one: 
1)GCJ Web Browser Plugin.
An open source Java virtual machine (runtime) implementation web browser plugin.
2)Java(TM) Plug-in, Java SE 6.
Java runtime browser plugin from Sun Microsystems (commercial, but free as in no cost) version 1.6
3) The Java (TM) plug-in, Java SE 5.0.
same as option 2 but using version 1.5, i don't really know why they are offering this option
4) The GCJ Web Browser Plugin (using IcedTea). 
same as option 1 but with using IcedTea to build it ([http://icedtea.classpath.org](http://icedtea.classpath.org))

If you don't care about using commercial software and keeping your system all free and open source, then I would advise you to choose option number 2 or install the whole package "java6" from synaptic as i understand you were doing.

Benchmarks had shown that Java 6 from Sun is faster and uses less memory than the other three options.

---

### Post by hanzj on 2008-04-21
If you guys have some time, pls answer related questions:
 [Which of the 4 x-pn-realaudio-plugin options do I choose for Firefox?]("http://ubuntuforums.org/showthread.php?t=761028")


and
 [Which of the 4 audio/mpeg options should I choose for Firefox?]("http://ubuntuforums.org/showthread.php?p=4756730")

---

