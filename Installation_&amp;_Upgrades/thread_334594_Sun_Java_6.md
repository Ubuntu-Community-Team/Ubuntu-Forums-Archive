---
title: "Sun Java 6"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by areks on 2007-01-09
I'm wondering why Sun GPL Java 6 is not in Ubuntu repository? 
It looks like Ubuntu support non-free Sun Java 5 but not free version. Very strange.

Yes I know how to install it myself, but actually I would like to compliantly remove GCJ from my system. For not advanced users it may look like there is choice to use free or not free Java. This is not really true. The choice is between two free versions of Java:
- Java 4 (GCJ)
- Java 6 (Sun)
The version number (of specification) should make it clear which one to choose.

---

### Post by Ryba on 2007-01-09
I would guess that the main reason is cause it is totally buggy as hell.

Try using eclipse (edit the /etc/eclipse/java_home to point to the java 6 before the other versions) or azerus with java 6.

Make damn sure to NOT run anything else on the computer at all with java 5 (known problems with running both java 5 and 6 together).

See how long it takes various things to work in eclipse sometimes under heavy load. See how many times you run out of memory or how many little glitches that never used to happen start happening.

Java 6 is fantastic don't get me wrong but it isn't quite fine tuned enough to be the default vm in my experience.

I've also had lots of various little issues with software of my own running on java 6 as well. But nothing makes for a cleaner example then running any SWT application under java6.

A lot of code needs to be updated (especially SWT based code) before java 6 should be the default.


Oh and for the record, Java 7 is GPL. I don't remember seeing the article stating that Java 6 was.

---

### Post by areks on 2007-01-09
I'm using Java 6 without problems for a year now (snapshot builds, beta, RC, and finale).
I'm also running programs on both Sun J5 and Sun J6 at a same time. No problem.
I also made stress test of our program with heavy load and I don't have problem with J5 or J6.

If Eclipse projects has some bugs related to Java 6, fine let them fix it, but I don't care. It is not the only Java IDE on earth.
In Eclipse page I was trying to find out if it runs with default JVM form Ubuntu (GCJ). Does not look like. Look yourself: [http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945//java-runtimes.html](http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945//java-runtimes.html)

Why Eclipse choose to use JDK 1.4 I have no idea. Maybe because IBM is also 2 version behind specification :)

Coming to license, in official Sun announcement about opening Java I found:
"Sun will release all unencumbered source-code modules of JDK 6 and JDK 7, along with full build scripts (...).
The code will be available under the GPL v2 license plus the ClassPath Exception." 
([http://www.sun.com/software/opensource/java/project_overview.jsp](http://www.sun.com/software/opensource/java/project_overview.jsp))

So I don't know how you come to your conclusion about license?

---

### Post by Ryba on 2007-01-11
> **areks said:**
> I'm using Java 6 without problems for a year now (snapshot builds, beta, RC, and finale).
I'm also running programs on both Sun J5 and Sun J6 at a same time. No problem.
Great for you. I have also except every once in a blue moon, especially when a server or two has been running for a few weeks or so you find these odd issues crop up and/or resource problems come up and things go unstable.

> **areks said:**
>  I also made stress test of our program with heavy load and I don't have problem with J5 or J6.
Look, I don't want to get into a debate. Like i said java 6 is fantastic but it does have some enterprise level flaws with it. I seriously doubt your stress test took into account the know "known" bugs that sun themselves admit and are fixing.

They are not your everyday problems mind you and a lot of people will not find them but when you start doing things like sending out 60 megabits/sec worth of data across multiple servers, serializing data to/from other java processes, make rmi calls, and sending out millions of emails per day, you find that these various little flaws in the system (known defects that sun is actively working on patching up mind you but currently are still out there in the latest release of java 6).

> **areks said:**
>  If Eclipse projects has some bugs related to Java 6, fine let them fix it, but I don't care. It is not the only Java IDE on earth.
In Eclipse page I was trying to find out if it runs with default JVM form Ubuntu (GCJ). Does not look like. Look yourself: [http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945//java-runtimes.html](http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945//java-runtimes.html)

Actually eclipse 3.2.x isn't going to work with java 6. Java 6 changed a lot of underlying things around in the jvm that the SWT 3.2 api does not fully support. Eclipse 3.2.x is built on top of SWT 3.2. Eclipse 3.3 (built on top of SWT 3.3) works great with Java 6 but it is the problems in Java 6 (which sun microsystems themselves admits is a bug in java6 and are fixing with a patched version expected in early march).

> **areks said:**
>  Why Eclipse choose to use JDK 1.4 I have no idea. Maybe because IBM is also 2 version behind specification :)
Why not. Just because they compile the code using 1.4 api only doesn't mean that they don't benefit from java 5/6 engines running the system.

Don't mistake the java language api for the java virtual machine. The api is coded in 1.4 so that people who run java 1.4 virtual machine can use it (and there are a lot of companies out there who still have not migrated to java 5 yet).

However, anyone running java 5/6 gets all of the benefits of 5/6 still. It is only the developers themselves who do not enjoy the benefits of coding in 5/6.

> **areks said:**
>   Coming to license, in official Sun announcement about opening Java I found:
"Sun will release all unencumbered source-code modules of JDK 6 and JDK 7, along with full build scripts (...).
The code will be available under the GPL v2 license plus the ClassPath Exception." 
([http://www.sun.com/software/opensource/java/project_overview.jsp](http://www.sun.com/software/opensource/java/project_overview.jsp))

So I don't know how you come to your conclusion about license?
Well, I got my information from [https://openjdk.dev.java.net/](https://openjdk.dev.java.net/) and within there,they had a lot of conversations that java 7 (which is the released version of java 6 GPL'd) is what was GPL'd and *NOT* java 6 itself.

Oh and I suppose the backup defense would be that I actually hava Java 6 installed and have READ the license and it is still the sun license where as Java 7 (which I also have installed) is the GPL 2 license.

---

### Post by Ryba on 2007-01-11
> **areks said:**
> In Eclipse page I was trying to find out if it runs with default JVM form Ubuntu (GCJ). Does not look like. Look yourself: [http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945//java-runtimes.html](http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945//java-runtimes.html)

Oh btw, eclipse DOES work with the default gcj jvm that comes with ubuntu.

Why anyone would use gcj I don't have a clue but if you want to use it with gcj just

"apt-get install eclipse" from the command line. It will install the gcj if you did not already install the sun-java packages and when you start the eclipse you just installed from the package manager, it will default to using gcj as well.

Personally I think it was slow an clunky but your mileage may vary.

---

### Post by areks on 2007-01-11
My original question was:
"I'm wondering why Sun GPL Java 6 is not in Ubuntu repository?"

And your first answer was:
"I would guess that the main reason is cause it is totally buggy as hell."

I just don't agree. 

Anyway this is not a point. Sun Java 5 is in Ubuntu repository, Java 6 is not. 
If I install Sun Java (5 from repository or 6 manualy) this will not be default Java anyway.

This is not about some servers, or development tools. This is about giving choice for normal user who would like to run some Java desktop applications. 
I strongly believe GCJ is not the best for it but of course it can be one of the options. Users should have full freedom to choose any JVM.

---

### Post by Ryba on 2007-01-11
> **areks said:**
> If I install Sun Java (5 from repository or 6 manualy) this will not be default Java anyway.

This is not about some servers, or development tools. This is about giving choice for normal user who would like to run some Java desktop applications. 
I strongly believe GCJ is not the best for it but of course it can be one of the options. Users should have full freedom to choose any JVM.

With dapper you are correct. That is because Java 5 just got into the dapper installation like 1 or 2 days before they froze. Bad timing mostly.

With edgy, you have to uninstall the gcj stuff to make java 5 the default. Otherwise, just like with most all java apps, you just have to set your JAVA_HOME to point to the correct jvm and start up the program using $JAVA_HOME/bin (which means putting that in your path before the normal path stuff).

With fiesty I can't say for certain but I heard that the debian folks are working on letting the admin set the default similarly to how they allow you to pick between the gdm and kdm and xdm stuff. No clue how far along that is but I would presume that fiesty will incorporate that once debian is finished seeing as they are pretty tightly nit group of nice guys :)

---

### Post by GSMD on 2007-01-13
A good explanation with in-depth details on JDK6 installation is [here]("http://trac.centricware.org/wiki/2007/01/28/21.58").

*updated*

---

### Post by phossal on 2007-01-16
You may regret installing the 64Bit packages. I recommend: [Install JDK6, eclipse and Tomcat]("http://ubuntuforums.org/showthread.php?t=332674")

---

### Post by FyreBrand on 2007-01-27
I'm curious what /etc/jvm needs to point to.  There isn't any /usr/lib/j2skd-1.6-sun like there was with sun-java5.  I have successfully installed Java6 via the repositories and used update-java-alternatives -s java-6-sun and it updated successfully. The output of update-alternatives --display java is as follows:
```
user@kubuntu-box:~$ sudo update-alternatives --display java
java - status is manual.
 link currently points to /usr/lib/jvm/java-6-sun/jre/bin/java
/usr/bin/gij-wrapper-4.1 - priority 41
 slave java.1.gz: /usr/share/man/man1/gij-wrapper-4.1.1.gz
/usr/lib/jvm/java-6-sun/jre/bin/java - priority 63
 slave java.1.gz: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/man/man1/java.1.gz
Current `best' version is /usr/lib/jvm/java-6-sun/jre/bin/java.
```
Has this version changed the way programs point to the compiler?  I'm no java expert but it looks like there are only pointers to the virtual machine and not the compiler.  I mean that I don't see a link to the jdk. I'm used to manually editing the /etc/jvm file and inserting a line that points to /usr/lib/j2sdk-<ver>.  Am I missing something here?  I hope my question isn't too noobly.  Thanks.

---

### Post by phossal on 2007-01-28
> **FyreBrand said:**
> I'm curious what /etc/jvm needs to point to.  ... I mean that I don't see a link to the jdk. 

Why would it *need* to point to the "JDK"? Do you run javac from the command line?

---

### Post by FyreBrand on 2007-01-28
Well it is my understanding (or misunderstanding) from the Ubuntu help page that applications like eclipse and others use the /etc/jvm file to select the java compiler.  Isn't that what that file is for?

To answer your question no I don't do much java compiling from the command line.  It is more for application functionality.

Here is the article I'm referring to: [**Java - Ubuntu Community Documentation**]("https://help.ubuntu.com/community/Java").

---

### Post by phossal on 2007-01-28
> **FyreBrand said:**
> Well it is my understanding (or misunderstanding) from the Ubuntu help page that applications like eclipse and others use the /etc/jvm file to select the java compiler.  Isn't that what that file is for.

I've deleted /etc/jvm as test. All of my programs still run, including eclipse. It's true that the programs will look there, but, per usual, it isn't necessary.

---

### Post by FyreBrand on 2007-01-28
> **phossal said:**
> I've deleted /etc/jvm as test. All of my programs still run, including eclipse. It's true that the programs will look there, but, per usual, it isn't necessary.I'll just reply in this thread since we're having a redundant conversation.  I found nearly the same thing.  I deleted all but one entry (to gcj) from /etc/jvm and my programs still seem to be using sun-java6.

To answer your question in the other thread about /usr/bin/java.  I also think that is where programs look for it.  It is where I point programs like Opera that need to be told.  When I execute a ```
which java
``` I also get /usr/bin/java.

So I did a bit of poking around since you brought all this up and I found that /usr/bin/java just points to /etc/alternatives/java which in turn points to /usr/lib/jvm/java-6-sun/bin/java.  So I'm not sure what, if anything, needs /etc/jvm.  Like you point out it appears not to be necessary but maybe a redundancy or for some programs which might look for it by default.

If everything is working then I'm not going to worry about it.  Thanks for the discussion.  I learned more interesting stuff.   I love how powerful unix/linux pointers (links) are even if they get a bit convoluted sometimes.

---

### Post by phossal on 2007-01-28
> **FyreBrand said:**
> Thanks for the discussion.  I learned more interesting stuff.   **[SIZE="1"]I love how powerful unix/linux pointers (links) are even if they get a bit convoluted sometimes.[/SIZE]**

Yeah, thank you, too. I always learn when I participate in these kinds of discussions. Unix is definitely a building block-style OS. I was shocked when I first learned update-alternatives was just a *perl* script that managed the symbolic links. lol Similar thing for the much-loved, much-used ndiswrapper. Just perl. 

Off topic, I occasionally get bashed for suggesting that new programmers make the effort to learn Perl. The many underlying OS maintenance scripts make it a worthwhile endeavor. 

Anyway, on to new things. Take care!

---

### Post by Ramses de Norre on 2007-01-28
Are these the links you're expecting?
```
sudo update-alternatives --display javac
```

---

### Post by FyreBrand on 2007-01-28
I was just expecting a similar file layout as Java5 had.  I was looking for a java5-sdk library in /usr/lib that /etc/jvm would point to.  So far most everything is working okay so I'm kind of just ignoring /etc/jvm until I find an application that uses it and is stumped.

---

