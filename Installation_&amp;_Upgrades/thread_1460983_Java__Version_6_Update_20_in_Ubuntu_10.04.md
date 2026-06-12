---
title: "Java  Version 6 Update 20 in Ubuntu 10.04"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by abra1 on 2010-04-23
In Ubuntu 10.04,  I have upgraded Java to Version 6 Update 20.
Java site says that I have the recommended Java installed (Version 6 Update 20).
Firefox says : 'application/x-java-applet;jpi-version=1.6.0_20 ' and 'application/x-java-bean;jpi-version=1.6.0_20'.
/opt/java/32$ has 2 folders: jre1.6.0_20   as well as  jre-6u20-linux-i586.bin.

But the Repositories have Java 6b18-1.80 Oubuntu1 as the latest version.

And in the terminal , entry for  'java -version' gives :
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK Client VM (build 14.0-b16, mixed mode, sharing)                          

How can I fix the  discrepancy?

---

### Post by nico.huysamen on 2010-04-24
[FONT=Courier New]sudo update-java-alternatives -s java-6-sun[/FONT]

---

### Post by abra1 on 2010-04-24
> **nico.huysamen said:**
> [FONT=Courier New]sudo update-java-alternatives -s java-6-sun[/FONT]

tried that and got:

update-java-alternatives: directory does not exist: /usr/lib/jvm/java-6-sun

---

### Post by jocko on 2010-04-24
> **abra1 said:**
> In Ubuntu 10.04,  I have upgraded Java to Version 6 Update 20.
Java site says that I have the recommended Java installed (Version 6 Update 20).
Firefox says : 'application/x-java-applet;jpi-version=1.6.0_20 ' and 'application/x-java-bean;jpi-version=1.6.0_20'.
/opt/java/32$ has 2 folders: jre1.6.0_20   as well as  jre-6u20-linux-i586.bin.

But the Repositories have Java 6b18-1.80 Oubuntu1 as the latest version.

And in the terminal , entry for  'java -version' gives :
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK Client VM (build 14.0-b16, mixed mode, sharing)                          

How can I fix the  discrepancy?
You have confused two different java's. The latest open source java (openjdk) is at version 6b18 in the repos, but the latest version of sun's java is 6.20.
Did you install sun's java from the repos (you need to enable the partner repo first), or from java.com? I don't think the "update-java-alternatives" command will know about anything you have installed from any other source than the repo...

You could try this command instead:
```
sudo update-alternatives --all
```It will ask you which alternative to use for anything that has more than one alternative. Just change those that concern java to use java-6-sun instead of openjdk and leave the rest (fonts, editors, etc.. .) at the default settings. But I'm pretty sure you have to install the repo version to get it working, as I think sun's java installer will install everything somewhere else than in /usr/lib/jvm/java-6-sun.

---

### Post by abra1 on 2010-04-24
> **jocko said:**
>  ...   I think sun's java installer will install everything somewhere else than in /usr/lib/jvm/java-6-sun.

Thanks jocko,  You guessed right : I  installed sun's java  from java.com.

And as you guessed right again :  '  /opt/java/32$ has 2 folders: jre1.6.0_20   as well as   jre-6u20-linux-i586.bin. '    
      
Using the command : sudo update-alternatives --all
kept giving me various alternatives and the alternatives gave more alternatives which I did not understand and did not know which to chose.

My main concern is to use the latest Java because of the reported bug ( I do play a little chess on flyordie and was concerned about the bug).

---

### Post by jocko on 2010-04-24
> **abra1 said:**
> Thanks jocko,  You guessed right : I  installed sun's java  from java.com.

And as you guessed right again :  '  /opt/java/32$ has 2 folders: jre1.6.0_20   as well as   jre-6u20-linux-i586.bin. '    
      
Using the command : sudo update-alternatives --all
kept giving me various alternatives and the alternatives gave more alternatives which I did not understand and did not know which to chose.

My main concern is to use the latest Java because of the reported bug ( I do play a little chess on flyordie and was concerned about the bug).
No idea which bug you talk about, but since the partner repo already contains the latest available java version from sun, why not install that instead?

---

### Post by abra1 on 2010-04-26
> **jocko said:**
> No idea which bug you talk about, but since the partner repo already contains the latest available java version from sun, why not install that instead?

Thanks  jocko,

Sorry for the delayed reply.

Here is the reported bug for Java: [http://seclists.org/fulldisclosure/2010/Apr/119](http://seclists.org/fulldisclosure/2010/Apr/119) .
While it affects mainly Windows, I have dual boot and sometimes use Windows.

And here is the report about Java in Ubuntu Lucid Lynx: 
[http://www.zdnet.co.uk/blogs/jamies-random-musings-10006480/ubuntu-1004-lucid-lynx-and-java-10015534/](http://www.zdnet.co.uk/blogs/jamies-random-musings-10006480/ubuntu-1004-lucid-lynx-and-java-10015534/)

---

