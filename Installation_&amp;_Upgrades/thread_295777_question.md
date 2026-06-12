---
title: "question"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by doh224 on 2006-11-08
i've installed java but it does not work? :confused:  can anybody help me with this?

---

### Post by an.echte.trilingue on 2006-11-08
When installing, did you follow the instructions [here]("https://help.ubuntu.com/community/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca") or did you use another method?

What are your symptoms (how do you know it isn't working)?

---

### Post by doh224 on 2006-11-09
when I open a browser, where the java plugin should work, it does not. theres no plugin missing, there's just no image? 
i've got the package and installet it ;)

---

### Post by an.echte.trilingue on 2006-11-09
I am not quite sure what you meant but I am going to assume you meant that you downloaed JRE from Sun directly and installed it with the install script included in that package.  That is the hard way of doing things, as you are discovering. I find it is usually less of a headache and more successful to install things from the repositories, as described [here]("https://help.ubuntu.com/community/InstallingSoftware").  Also, for many things such as Java, flash, and mp3, you need to enable all of your repositories, for which you follow the instructions [here]("https://help.ubuntu.com/community/Repositories/Ubuntu").

I sent the wrong link before for installing java: [this]("https://help.ubuntu.com/community/Java") are the instructions for java.  

Also, are you sure java is what you want?  Java is a programming language and installing it usually is only good for using certain web based apps, not displaying images.  Read about it [here]("http://en.wikipedia.org/wiki/Java_%28Sun%29").

It sounds to me like you want [flash]("http://en.wikipedia.org/wiki/Adobe_Flash") (instructions [here]("https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3")), or maybe to play embedded media, for which you need to install mozplugger.  If that is the case, you should read the [multimedia page]("https://help.ubuntu.com/community/Multimedia"), especially the section about restricted formats.

Let me know if this helps you or not!

Take care,
-mat

---

### Post by doh224 on 2006-11-09
no it is the java. so I can play java games on the internet :) 

i've tried it all, and it should be installed. but when I went to a web site called gratis-ting.dk, I could play one game, but I couldn't play all the other games? I don't understand it

---

### Post by emdeem on 2006-11-09
What, exactly, did you install?  You need the plugin package, not just java, for it to work in a browser.

---

### Post by doh224 on 2006-11-09
I have downloaded a package with it, and installed the package with java that follows with the ubuntu system.

---

### Post by an.echte.trilingue on 2006-11-10
What, **exactly**, letter for letter, was the name of the package(s) that you installed?  It makes a big difference.

---

### Post by doh224 on 2006-11-10
> **an.echte.trilingue said:**
> What, **exactly**, letter for letter, was the name of the package(s) that you installed?  It makes a big difference.
jre_1.5.0_09-1_i386.deb 
this one should be installed, but does not work, (I've send a message out not so long a go, and in that message I explains the problem more pricies)
 
i've also tried installing a file called jdk-6-rc-linux-i586.bin, but I never came furter than making it a .jar.

---

### Post by an.echte.trilingue on 2006-11-10
You need to follow the instructions [here]("https://help.ubuntu.com/community/Java#head-f4267cc37a197ccf46397cc58ff0944838741956") to install sun-java5-bin.

---

### Post by doh224 on 2006-11-10
the link is good enorgh , but it seems that I don't have the package. :neutral:  this is getting pretty anoying ;). 
I've also tried install it with the command 
sudo apt-get install sun-java5-bin
but then it says that there is no package of that name. :-k  
it should be there, I have ubuntu 6.06?

---

