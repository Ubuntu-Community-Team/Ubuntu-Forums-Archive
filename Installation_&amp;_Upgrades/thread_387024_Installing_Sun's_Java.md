---
title: "Installing Sun's Java"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by DRGuy on 2007-03-17
Hi,

I'm interested in getting Sun's Java (both JRE and JDK) installed on my ubuntu box.  i bought a book with the intention of brushing up on my Java, and it is expecting one to have that on the machine.  As you probably know, I seem to have some gij version of Java now.

In searching around, it seems this isn't a straightforward task.  I've found a few articles with various approaches, but upon further investigation, these seem to be a bit dated (1.5-2 years old or so).  One talks about fakeroot and some other tool that I gather takes a standard Sun package (in rpm format?) and makes it into a .deb type file.  The other suggests adding some lines to my apt sources.list file, and then doing an apt-get update and then apt-get install sun-java5-jdk.  The lines are:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) daper main restricted

  and

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) daper universe multiverse

So, I'm wondering if this second approach is the better idea, or if perhaps there is some more current way to attack it.  Will this open me up to lots of other more experimental or otherwise unstable code in the rest of my system?  I've been trying to keep this system pretty "by the book".  I had an older version of Debian (from a Knoppix CD) that I opened up to testing/unstable in order to get something that I needed (or probably just wanted at the time) and I ended up with a pretty messed up machine (mostly the Mozilla had a really screwed up font situation, both on screen and when trying to print email or web pages - on screen I seemed to get different sized fonts every time I logged on, and when I printed web pages or email it seemed to want to use some font that looked like hand printing - which was different than what displayed on screen - even though Konquerer would print the same web page just fine).

Anyway, maybe that problem wasn't really due to using testing/unstable branches, but I guess I'm a little gun shy about doing something like that just to get Sun's Java.

Thanks,
--
DRGuy

---

### Post by nyinge on 2007-03-17
It is very unlikely that adding "universe" and "multiverse" to your sources.list will break anything.  It will just give you extra packages that are not officially maintained/supported by Ubuntu dev team.  In this case, Sun's java packages.

If you're using dapper, you can add "multiverse" to the end of the line:
```
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) daper main restricted 
```
in /etc/apt/sources.list.

While you're at it, you can also go ahead and add the "universe" repository.  So you'll end up with
```
   deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) daper main restricted universe multiverse 
```

More details [here]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by phossal on 2007-03-17
I always pull Java directly from Sun. No need to use the packages, they're a waste of time.

---

### Post by DRGuy on 2007-03-18
I thought that the advantage of using the packages was that apt would thereafter monitor and update the packages you have installed (including the Java, once it has been installed), as well as any changes to dependent packages.  Is that not the case with "non-core" packages, such as the Sun Java (as opposed to the gij Java)?

Thanks for the responses!
--
DRGuy

---

### Post by phossal on 2007-03-18
I've been convinced that it's almost always better to use the packages (and the package managers) whenever possible. However, there are key exceptions, one of which is Java. 

Java, installed manually, can be incorporated into update-alternatives, which allows the user to choose a program to handle certain responsibilities even though other capable executables may exist.

The typical user will do just fine using the third-party packages for Java. But, for developers and programmers using Java, it's probably in their interest to download and install using Sun's .bin file directly, if only in addition to installing one of the packages. 

The packages are prepared "third-party" using Sun's .bin file anyway. Common delays in their release prevent users like me from capitalizing on Sun's updates as quickly as we could. There is needless complexity in a package install of Java that makes failed installations difficult to diagnose, and the third-party preparation of the package adds a layer of abstraction (read: security risk) that isn't necessary. There are other reasons for a manual install that are commonly known to Java programmers: multiple JDK's, multiple (older) versions, etc.

---

### Post by nyinge on 2007-03-18
True, but it could sometimes take weeks or, on rare occasions, even months, for a package to be updated in a repository, if the update is considered to be not crucial.  But it shouldn't be the case with java though, hopefully.  :)

---

### Post by DRGuy on 2007-03-18
OK, this is probably a trivial problem now, but I'm still having a bit of trouble here.

I went to Phossal's link in his signature ("Install Java SDK the smart way"), and all seems to have gone well, except that the /etc/alternatives/java file insists on pointing to the old GNU java rather than the newly installed (according to the directions) SUN java.  The javac seems fine (though I don't know if that link had existed before).  I did not get any errors when running any of the update-alternatives commands.

I went back in my shell history to verify the commands I typed, and they looked fine to me.  I re-ran the commands (--install and --auto) for the java steps, but it still doesn't seem to have taken.

The Firefox installation seems fine as well, I can go to [www.java.com](www.java.com) and hit their "verify installation" and get contratulated that I have the latest Java installed.  That did not happen before.

So, any suggestions about how to resolve the java link issue?  Should I perhaps just remove /etc/alternatives/java, and then re-create it with the command from Phossal's instructions?

Here is some cut/paste from my shell window:

greg@Gilmour:~$ ls -l /etc/alternatives/javac
lrwxrwxrwx 1 root root 24 2007-03-18 13:48 /etc/alternatives/javac -> /usr/lib/java6/bin/javac
greg@Gilmour:~$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 34 2007-03-18 14:22 /etc/alternatives/java -> /usr/lib/jvm/java-gcj/jre/bin/java
greg@Gilmour:~$ sudo update-alternatives --install /usr/bin/java java /usr/lib/java6/bin/java 300
Password:
greg@Gilmour:~$ sudo update-alternatives --auto java
greg@Gilmour:~$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 34 2007-03-18 14:49 /etc/alternatives/java -> /usr/lib/jvm/java-gcj/jre/bin/java
greg@Gilmour:~$ ls -l /usr/lib/java6/bin/java
-rwxr-xr-x 1 root root 47116 2006-11-29 03:49 /usr/lib/java6/bin/java


Thanks for any suggestions,
--
DRGuy

---

### Post by phossal on 2007-03-18
You can try this:
```
sudo update-alternatives --config java
```

That presents all options for Java and allows you to select one. If you find your output doesn't have the option for Java6, you've missed a step somewhere.

Here is what my output looks like:
```
bash 3.1:sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/Java6/bin/java

Press enter to keep the default[*], or type selection number: 
```

---

### Post by DRGuy on 2007-03-18
Well, that seems to have done the trick...

greg@Gilmour:~$ sudo update-alternatives --config java
Password:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-gcj/jre/bin/java
      3        /usr/lib/java6/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/java6/bin/java' to provide `java'.
greg@Gilmour:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
greg@Gilmour:~$ javac -version
javac 1.6.0


So.. Thanks for all the guidance!!  I wonder why the other command wasn't taking?  Anyway, looks like I'm good to go for now.

--
DRGuy

---

### Post by phossal on 2007-03-18
> **DRGuy said:**
> Well, that seems to have done the trick...  (...) So.. Thanks for all the guidance!!  I wonder why the other command wasn't taking?

You're welcome. Glad you're up and running.

---

### Post by Splinterhood on 2007-09-17
I installed through Synaptic (Java6) then it would not work. Then I found this link: [https://jdk-distros.dev.java.net/ubuntu.html](https://jdk-distros.dev.java.net/ubuntu.html)
and typed:  sudo apt-get install sun-java6-plugin
and for some reason it worked.
This place told me the version: [http://www.javatester.org/version.html](http://www.javatester.org/version.html)
and I played this game to further verify if it worked: [http://www.xnet.se/javaTest/jPong/jPong.html](http://www.xnet.se/javaTest/jPong/jPong.html)
I am a noob, so can anyone tell me why it worked?
Is it because i installed the plugin with apt-get? because I though I installed the plugin through Synaptic (along with the binaries, fonts, jre).  did it only partly install or was it a granted permission for some repositories? How can i find out? :confused:
{if I posted this in the wrong spot let me know where it was moved please}

---

### Post by Gremlinzzz on 2007-09-17
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
too see the java your using type java -version  in terminal

---

