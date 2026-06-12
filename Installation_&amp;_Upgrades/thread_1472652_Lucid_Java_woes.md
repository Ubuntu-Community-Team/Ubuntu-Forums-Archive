---
title: "Lucid Java woes"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by maphilli14 on 2010-05-04
I posted this to ABT, but didn't think it was the right audience, and don't know how to move the thread.  Please let me know if anyone can help get me in the right direction...

[http://ubuntuforums.org/showthread.php?t=1471144]("http://ubuntuforums.org/showthread.php?t=1471144")

---

### Post by frantid on 2010-05-04
check the release notes, they removed sun java from the repositories -- you need to add it separately -- directions in the release notes.

---

### Post by maphilli14 on 2010-05-04
I added the Sun repo's from the software center and installed:

```
miphilli@Aquila:~$ dpkg -l | grep sun-java
ii  sun-java6-bin                                               6.20dlj-1ubuntu3                                Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-javadb                                            6.20dlj-1ubuntu3                                Java(TM) DB, Sun Microsystems' distribution 
ii  sun-java6-jdk                                               6.20dlj-1ubuntu3                                Sun Java(TM) Development Kit (JDK) 6
ii  sun-java6-jre                                               6.20dlj-1ubuntu3                                Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-plugin                                            6.20dlj-1ubuntu3                                The Java(TM) Plug-in, Java SE 6
ii  sun-java6-source                                            6.20dlj-1ubuntu3                                Sun Java(TM) Development Kit (JDK) 6 source 
ii  sun-javadb-client                                           10.3.2.1-0ubuntu2                               Java DB client
ii  sun-javadb-common                                           10.3.2.1-0ubuntu2                               Java DB common files
ii  sun-javadb-core                                             10.3.2.1-0ubuntu2                               Java DB core
ii  sun-javadb-doc                                              10.3.2.1-0ubuntu2                               Java DB documentation
miphilli@Aquila:~$
```

```
miphilli@Aquila:~$ java -version
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)
miphilli@Aquila:~$ 
```

What am I missing from the release notes?

---

### Post by frantid on 2010-05-04
Nothing...  you were already there, my apologies.  I'm not sure why it won't work for you.

---

### Post by maphilli14 on 2010-05-04
> **frantid said:**
> Nothing...  you were already there, my apologies.  I'm not sure why it won't work for you.

That's OK, you were just trying to help!  :(  Strange issue, and I think other folks in my organization have solved this issue by switching from OpenJDK to Sun Java, which worked once but never again.  I have cleaned java cache via console and manually.  Any steps to take  to gather more info are appreciated!

Mike

---

### Post by timwebuk on 2010-05-04
I'm having some Java problems too.  I'm relatively new to Ubuntu actually, in fact I installed 9.10 a few days ago and then this was released!  So I attempted to update and now I cannot run 'java' as it isn't installed.

I am trying to use aptitude and apt-get... but much to no avail.  Now I have a feeling I'm starting to make a mess on the OS from running all of these installs, any idea how to clean it up and actually get it working?

Sorry for the noob questions!

I've been using this site as a reference:

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

---

### Post by PRC09 on 2010-05-04
Maybe.....post#4 or post#6


[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/532174](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/532174)

---

### Post by occams_beard on 2010-05-04
> **frantid said:**
> check the release notes, they removed sun java from the repositories -- you need to add it separately -- directions in the release notes.

I need to use sun java. It's a real bummer that they removed it from the official repo.

What is the rationale for their decision to remove it?  On the release notes it says OpenJDK is recommended. Why?

---

### Post by frantid on 2010-05-04
I don't know.  But if I had to bet, I'd bet that it is because it's "sun's".  With MS going after some linux distro's, I could see it as a means to prevent any legal action from Sun against Canonical.

---

### Post by occams_beard on 2010-05-05
> I don't know. But if I had to bet, I'd bet that it is because it's "sun's". With MS going after some linux distro's, I could see it as a means to prevent any legal action from Sun against Canonical.

Well, sadly, Sun does not exist any more. Swallowed up by Oracle, so maybe that has something to do with it. 

Sun, I think, has always been very friendly toward open source communities, Why would they not want their products distributed?

In any case, I would like to know the reason why the "sun/oracle" version of java was removed.

---

### Post by bm.riyadh on 2010-05-05
I am in problem with java in firefox. Each time I enter into a site that use java like facebook image uploader, firefox shows "missing required plugin" but when I search using plugin finder service it does not got it and tells to install it manually. In java homepage I saw that the JRE files are in either rpm or bin file. How can I install a bin or rpm file? Please help me. Thanks.:mad:



-----------------------------
Java jobs in Chicago
[http://mmdtech.com/job_list.php](http://mmdtech.com/job_list.php)

---

### Post by infamous-online on 2010-05-05
> **bm.riyadh said:**
> I am in problem with java in firefox. Each time I enter into a site that use java like facebook image uploader, firefox shows "missing required plugin" but when I search using plugin finder service it does not got it and tells to install it manually. In java homepage I saw that the JRE files are in either rpm or bin file. How can I install a bin or rpm file? Please help me. Thanks.:mad:



-----------------------------
Java jobs in Chicago
[http://mmdtech.com/job_list.php](http://mmdtech.com/job_list.php)

Here's what someone here suggested that worked for me, uninstall the openjdk version of java and everything related to it. Next, open synaptic and go to repositories and check the ubuntu lucid parter link. Then, hit the reload button and close it after it's done. now open up a terminal and type in the following. 

**sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts**

and after that's done, open up firefox and type in about:plugins in the address bar and it should let you know if java is enabled on your browser or not. Try it out and let me know your results. :guitar:

---

