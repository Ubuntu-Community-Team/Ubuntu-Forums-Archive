---
title: "How to change default eclipse compiler"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by najdorfchess on 2011-07-07
Hi all. I have been having consistent problems with my eclipse IDE as many of the packages are not recognized. Notably the java.util.Scanner isnt working at all. I later found the reason for the problem that my eclipse takes openjdk compiler as default even though I have changed my default system jdk to be sun. Also I have gone Windows -> Preferences -> Java -> Installed JREs and have added the path of my sun-6 jdk (which is /usr/lib/jvm/) and have made it the default one in eclipse by checking on the box against it. But it is really frustrating to see the compiler not recognize my code. Can anyone kindly temme how to change the default compiler? I'm not an expert in this, so well explained help will be deeply appreciated. 

Kindly see below for my java and its compiler versions:


```
najdorf@mynatty:~$ java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode)

```


```
najdorf@mynatty:~$ javac -version
javac 1.6.0_24

```


Also when I compiler the message in status bar just before comsole in eclipse window is attached below

[[img]http://www.freeimagehosting.net/uploads/0089c1f98b.png[/img]](http://www.freeimagehosting.net/)

---

### Post by najdorfchess on 2011-07-09
^Bounce! Someone kindly help

---

### Post by kanishkdudeja on 2011-07-10
are you sure this is the case of your default compiler being openjdk and not something else?

---

### Post by najdorfchess on 2011-07-10
> **kanishkdudeja said:**
> are you sure this is the case of your default compiler being openjdk and not something else?

I'm sorry I don't get your question. My default Java is Sun JDK as shown below 

```
najdorf@mynatty:~$ java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode)

```

But eclipse compiles my program with Openjdk even though I changed it's settings in Windows -> Preferences -> Java -> Installed JREs

When I searched for this online I learnt that the possible cause could be the version of javac compiler that the system has. I wanna know how you could change the default javac in Ubuntu. My current one is as shown below

```
najdorf@mynatty:~$ javac -version
javac 1.6.0_24

```

---

### Post by kanishkdudeja on 2011-07-10
okay..

Right click on the project..click on build path..click on configure..then select the sun java one there..

if it still doesnt work i have an idea..

you can remove openjdk from your system..
then eclipse will be forced to use sunjdk as the default jdk..

---

### Post by najdorfchess on 2011-07-10
> **kanishkdudeja said:**
> okay..

Right click on the project..click on build path..click on configure..then select the sun java one there..


U mean where? I didn't get it.

When I right click on a project (a simple java project) then goto Build path -> Configure Build Path, I don't see a way to change my compiler option to Sun java. Can u explain?

---

### Post by kanishkdudeja on 2011-07-10
Check the image ive attached below..

You will see a similar image when you click on Configure Build Path..

Now click on libraries..

If you see any open jdk entries there, remove it..

If you don't see the JRE SYSTEM LIBRARY [ JavaSE 1.6 ] like it is shown for me, click on the Add libraries option.

Then Click on JRE System Library option..Then click on Alternate JRE..After clicking of Installed JRE's click on the sun java jre one..open jdk entries if you you find them there..this will not uninstall open jdk from your system just will remove them from the eclipse configuration..you can add it later if you want to..

After selecting the Sun jre from the list(you can check the second screenshot)..click on ok..

then click on finish..and then click on okay..

i think that should work..and then recompile your project

---

### Post by kanishkdudeja on 2011-07-10
were you able to solve it?

---

### Post by najdorfchess on 2011-07-10
It didn't solve my basic problem of compiling the code without indicating 'Scanner' as an error but it did change my installed JRE and I was able to remove openjdk from the list. See attachment (screenshot of Windows -> Preferences -> Java (Installed JREs). 
I was wondering if making sun java the default automatically sets the system to look for its updates? I mean when u do 

```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by kanishkdudeja on 2011-07-10
Does your code work normally with the command line? With javac and java commands?

If it doesnt work, we can be sure its a problem with the jre and not eclipse.

---

### Post by najdorfchess on 2011-07-10
Yes it runs fine on command line. I did a little mistake. Nevermind. Thanks a lot man =)

---

### Post by kanishkdudeja on 2011-07-10
What mistake?

Mistake in the code?

---

### Post by najdorfchess on 2011-07-10
Yes. I had created a class through eclipse and I overwrote that code with a simple hello world program to test if that runs, and it didn't. 

Check the screenshot below. It fails to find the class helloworld. I have no idea why I get this error.

---

### Post by najdorfchess on 2011-07-10
> **najdorfchess said:**
> Yes. I had created a class through eclipse and I overwrote that code with a simple hello world program to test if that runs, and it didn't. 

Check the screenshot below. It fails to find the class helloworld. I have no idea why I get this error.

Its a lame error. Nevermind. I'm getting used to eclipse IDE as I haven't used it much before.

---

### Post by kanishkdudeja on 2011-07-11
S has to be capital in String.

By the way, is scanner getting detected now?

---

### Post by najdorfchess on 2011-07-11
Yeah it should be. But the error is due to absense of a class that I named while creating the source. So eclipse was unable to build the code. Since the command prompt compiling doesn't have any of these restrictions, it was able to compile the code. Once I fix this, no error was shown.

---

### Post by kanishkdudeja on 2011-07-11
but scanner is working now na?

---

### Post by najdorfchess on 2011-07-11
Yeah it is working now. Will sun java gets updated via "update manager" ?

---

### Post by kanishkdudeja on 2011-07-11
yes if you downloaded it through the repositories or some ppa.

---

