---
title: "Installing Other Programs on Ubuntu?"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by JustKoichi on 2007-09-07
I'm completely new to Linux and ubuntu. And I've been trying to install [http://www.alice.org/](http://www.alice.org/)  and iI have no idea how. I downloaded the linux version with .tar.gz 

[http://www.alice.org/downloads/authoringtool/linux_readme.htm](http://www.alice.org/downloads/authoringtool/linux_readme.htm)


thats the download page for it 

I unzipped it and I don't know what to do from there. Can anyone help me?

---

### Post by eentonig on 2007-09-07
forget about downloading apps for now. Follow the appropriate link in my signature.

---

### Post by logos34 on 2007-09-07
Here's another quick howto:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

You might also consider using [checkinstall.]("https://help.ubuntu.com/community/CheckInstall")

---

### Post by erfahren on 2007-09-07
I went and took a look at their site, they sure don't have much documentation do they? From what little I read they say you don't actuall install it you just put it on the drive somewhere and run it from there (for Linux, your /home/<username> directory would work.

I was going to download it to help figure it out but it's a whopping 100 some-odd megs! I don't feel *that* helpful! 

You could go ask on their forums. Someone seemed to get it (somewhat) working on kubuntu. see: [http://www.alice.org/community/showthread.php?t=889](http://www.alice.org/community/showthread.php?t=889)

It sounds like you can run it from anywhere but it needs Java. You'd need Sun's Java installed and configured to run as systemwide default (there is an open-source alternative which comes with Ubuntu). In Fiesty you can get Sun's Java version 6 through Synaptic Package Manager.

you can see which version of Java is set for the system default by typing "java -version" (without quotes into the terminal. To set the default in the terminal enter:
```

sudo update-alternatives --config java

```
you should get an output like:
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 

... and you select which one (you'd want java-6-sun).

Then look in the program's folder for a README to see if it says how to launch it. If it doesn't say, post back. good luck.

---

### Post by JustKoichi on 2007-09-07
How do I open a terminal and what is it?

---

### Post by Pumalite on 2007-09-07
Applications>Accessories>Terminal
It's a CLI and you have to start learning it.

---

### Post by JustKoichi on 2007-09-07
Alright sweet! I got it to work by installing java. Thanks for your help :)

---

