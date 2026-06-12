---
title: "IcedTea Plugin Fails To Run Applets"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-03-18
I tried to install the icedtea 6 plugin to get web applets running in FF but it fails.

Ive reported this bug:

[https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/344705](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/344705)

Any ideas?

---

### Post by taavikko on 2009-03-18
Linked to related bug.

Have u removed conflicting jre's sun-java{5,6} and their browser-plugins

**sudo update-alternatives --config java**
Should show only one... (or nothing to configure ;) )

---

### Post by Nullack on 2009-03-18
Your a legend :) This will help debug the issue.

nullack@PPP:~$ sudo update-alternatives --config java
[sudo] password for nullack: 

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.3
          2    /usr/lib/jvm/java-gcj/jre/bin/java
*+        3    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number: 

Looking more deeply, I have default-jre-headless installed which came from installing the open office org java  common package. I also have both the openjdk-6-jre and the openjdk-6-jre-headless.

Is that the problem? If so, this mess all came about because of packaging problems. The install sequence was:

1. Install openoffice.org-java common which brings in the headless
2. Realising I dont have a web applet plugin installed, I install the icedtea6-plugin, which brings in full java not headless.

---

### Post by taavikko on 2009-03-18
> Is that the problem? If so, this mess all came about because of packaging problems. The install sequence was:

1. Install openoffice.org-java common which brings in the headless


Couldn't recreate this, I have sun-java6-plugin installed with correspondent jre
```
sudo apt-get -s install openoffice.org-java-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gcj-4.3-base libbackport-util-concurrent-java libcommons-codec-java
  libdom4j-java libgcj-bc libgcj-common libgcj9-0 libgcj9-jar libjaxen-java
  libjaxme-java libjaxp1.3-java libjaxp1.3-java-gcj libjdom1-java
  liblog4j1.2-java liblog4j1.2-java-gcj libsaxonb-java libxerces2-java
  libxerces2-java-gcj libxom-java libxpp2-java libxpp3-java
Suggested packages:
  libdom4j-java-doc libgcj9-dbg libgcj9-0-awt libgnumail-java
  libsaxonb-java-doc libxerces2-java-doc libxom-java-doc bsh
The following NEW packages will be installed:
  gcj-4.3-base libbackport-util-concurrent-java libcommons-codec-java
  libdom4j-java libgcj-bc libgcj-common libgcj9-0 libgcj9-jar libjaxen-java
  libjaxme-java libjaxp1.3-java libjaxp1.3-java-gcj libjdom1-java
  liblog4j1.2-java liblog4j1.2-java-gcj libsaxonb-java libxerces2-java
  libxerces2-java-gcj libxom-java libxpp2-java libxpp3-java
  openoffice.org-java-common
0 upgraded, 22 newly installed, 0 to remove and 0 not upgraded.
Inst libbackport-util-concurrent-java (2.2+dfsg-1ubuntu1 Ubuntu:9.04/jaunty)
Inst libjaxp1.3-java (1.3.04-3ubuntu2 Ubuntu:9.04/jaunty)
Inst libxerces2-java (2.9.1-2ubuntu2 Ubuntu:9.04/jaunty)
Inst libjaxen-java (1.1.1-3ubuntu1 Ubuntu:9.04/jaunty)
Inst libcommons-codec-java (1.3-4ubuntu1 Ubuntu:9.04/jaunty)
Inst liblog4j1.2-java (1.2.15-4 Ubuntu:9.04/jaunty)
Inst libjaxme-java (0.5.2+dfsg-2 Ubuntu:9.04/jaunty)
Inst libxpp2-java (2.1.10-4ubuntu1 Ubuntu:9.04/jaunty)
Inst libxpp3-java (1.1.3.4.O-4ubuntu1 Ubuntu:9.04/jaunty)
Inst libdom4j-java (1.6.1+dfsg-3ubuntu1 Ubuntu:9.04/jaunty)
Inst libjdom1-java (1.1+dfsg-1 Ubuntu:9.04/jaunty)
Inst libxom-java (1.1-3ubuntu4 Ubuntu:9.04/jaunty)
Inst libsaxonb-java (9.0.0.4+svn20080322-2ubuntu1 Ubuntu:9.04/jaunty)
Inst openoffice.org-java-common (1:3.0.1-5ubuntu2 Ubuntu:9.04/jaunty)
Inst gcj-4.3-base (4.3.3-5ubuntu4 Ubuntu:9.04/jaunty)
Inst libgcj-common (1:4.3.2-2ubuntu1 Ubuntu:9.04/jaunty)
Inst libgcj9-0 (4.3.3-5ubuntu4 Ubuntu:9.04/jaunty)
Inst libgcj-bc (4.3.2-2ubuntu1 Ubuntu:9.04/jaunty)
Inst libgcj9-jar (4.3.3-3ubuntu5 Ubuntu:9.04/jaunty)
Inst libjaxp1.3-java-gcj (1.3.04-3ubuntu2 Ubuntu:9.04/jaunty)
Inst liblog4j1.2-java-gcj (1.2.15-4 Ubuntu:9.04/jaunty)
Inst libxerces2-java-gcj (2.9.1-2ubuntu2 Ubuntu:9.04/jaunty)
Conf libbackport-util-concurrent-java (2.2+dfsg-1ubuntu1 Ubuntu:9.04/jaunty)
Conf libjaxp1.3-java (1.3.04-3ubuntu2 Ubuntu:9.04/jaunty)
Conf libxerces2-java (2.9.1-2ubuntu2 Ubuntu:9.04/jaunty)
Conf libjaxen-java (1.1.1-3ubuntu1 Ubuntu:9.04/jaunty)
Conf libcommons-codec-java (1.3-4ubuntu1 Ubuntu:9.04/jaunty)
Conf liblog4j1.2-java (1.2.15-4 Ubuntu:9.04/jaunty)
Conf libjaxme-java (0.5.2+dfsg-2 Ubuntu:9.04/jaunty)
Conf libxpp2-java (2.1.10-4ubuntu1 Ubuntu:9.04/jaunty)
Conf libxpp3-java (1.1.3.4.O-4ubuntu1 Ubuntu:9.04/jaunty)
Conf libdom4j-java (1.6.1+dfsg-3ubuntu1 Ubuntu:9.04/jaunty)
Conf libjdom1-java (1.1+dfsg-1 Ubuntu:9.04/jaunty)
Conf libxom-java (1.1-3ubuntu4 Ubuntu:9.04/jaunty)
Conf libsaxonb-java (9.0.0.4+svn20080322-2ubuntu1 Ubuntu:9.04/jaunty)
Conf openoffice.org-java-common (1:3.0.1-5ubuntu2 Ubuntu:9.04/jaunty)
Conf gcj-4.3-base (4.3.3-5ubuntu4 Ubuntu:9.04/jaunty)
Conf libgcj-common (1:4.3.2-2ubuntu1 Ubuntu:9.04/jaunty)
Conf libgcj9-0 (4.3.3-5ubuntu4 Ubuntu:9.04/jaunty)
Conf libgcj-bc (4.3.2-2ubuntu1 Ubuntu:9.04/jaunty)
Conf libgcj9-jar (4.3.3-3ubuntu5 Ubuntu:9.04/jaunty)
Conf libjaxp1.3-java-gcj (1.3.04-3ubuntu2 Ubuntu:9.04/jaunty)
Conf liblog4j1.2-java-gcj (1.2.15-4 Ubuntu:9.04/jaunty)
Conf libxerces2-java-gcj (2.9.1-2ubuntu2 Ubuntu:9.04/jaunty)
devil@elite:~$ 

```

---

### Post by dBuster on 2009-03-18
I run the 64bit version of Jaunty and I have no need to install the icedtea java as the latest 64 bit java and its plugin works amazing for me.  I take it this is the 32 bit version you are talking about? 

I used the 64 bit script for installing java found in the 64bit threads and I modified it for each time there was a new release and each time it installs and runs perfectly.  Runs all java web apps that I have tried...

---

### Post by taavikko on 2009-03-18
> **dBuster said:**
> I run the 64bit version of Jaunty and I have no need to install the icedtea java as the latest 64 bit java and its plugin works amazing for me.  I take it this is the 32 bit version you are talking about? 

I used the 64 bit script for installing java found in the 64bit threads and I modified it for each time there was a new release and each time it installs and runs perfectly.  Runs all java web apps that I have tried...

Not everyone wants to use closed source software, sun's java being one of them.
I too would switch to openjdk ASAP. But these kind of bugs are the showstoppers. 

Slowly openjdk is catching up...

As for using scipts to install latest sun-java6 X86_64 plugins, that's a waste of time, since it's installable via repos.

---

### Post by dBuster on 2009-03-18
> **taavikko said:**
> Not everyone wants to use closed source software, sun's java being one of them.
I too would switch to openjdk ASAP. But these kind of bugs are the showstoppers. 

Slowly openjdk is catching up...

As for using scipts to install latest sun-java6 X86_64 plugins, that's a waste of time, since it's installable via repos.

I was not aware that the latest 64bit java and plug in are now available in the repos.  So then does that mean it will be part of the final of Jaunty when it is released?  I do not find the scripts a waste of time as they do more than just install for me, it makes sure that if I had installed some other version it removes it as well.  But if you claim they are in the repos then I can stop using the scripts...

I understand about not wanting to run or use closed source software however If it runs well why not use it?  That is how I see it...  But you are right it is a show stopper and should be fixed.

---

### Post by taavikko on 2009-03-18
> **dBuster said:**
> I was not aware that the latest 64bit java and plug in are now available in the repos.  So then does that mean it will be part of the final of Jaunty when it is released?

At the moment sun-java6-plugin is 64bit available.
And installable via repos. If nothing changes it would be same after official release

---

### Post by Nullack on 2009-03-18
My motivation was to stop using the closed source sun jre and plugin.

Clearly though, the open java isnt robust yet

---

### Post by Nullack on 2009-03-18
Well I turfed all of the openjdk and icedtea stuff, replaced it with Sun's jre and plugin - result: it all works.

---

### Post by Zorael on 2009-03-18
I posted a thread about this yesterday, see [http://ubuntuforums.org/showthread.php?t=1098830](http://ubuntuforums.org/showthread.php?t=1098830).

Basically everything looks right but IcedTea (in Firefox) soars to 100% cpu when it should be drawing applets. Sun's works great, but I want to use OpenJDK.

---

### Post by philinux on 2009-03-18
I wish this applet would work first time. My isp requires it for fault reports. Dont ask me why this site other than you can create a profile or maybe there is an affiliation.

[http://www.thinkbroadband.com/speedtest.html](http://www.thinkbroadband.com/speedtest.html)

To get it to work I have to refresh the screen about 10 times then it runs. Weird.

---

### Post by taavikko on 2009-03-19
> **Nullack said:**
> Well I turfed all of the openjdk and icedtea stuff, replaced it with Sun's jre and plugin - result: it all works.

Did you try using icedtea-plugin with sun-java{5,6} runtime-enviroment?
If it doesn't work, then the problem is in the plugin,
Otherwise it's in the openjdk-jre... just a little more triaging:)

Sorry if somebody already asked this but didn't read all the posts or threads...

---

