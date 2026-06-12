---
title: "java is installed, but insn't here!?! plz help"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by lorderico on 2007-08-25
I have installed jre 6.2 and it works, I also installed the jdk 6.02 and the java sdk.  I need to execute a jar file.  I know to do this you type

java -jar *filename*

When I type java or java -version, it gives me this:

The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found

It is like it isn't even installed.  I need to know if I need a different java file, or if I just installed one of the things wrong.  I used this [[COLOR="Red"]webpage[/COLOR]]("http://java.com/en/download/help/5000010500.xml") to install the jre and it works.  All the rest I just make executable, went into where I wanted to installed it, and ran it.  If you know anything that will help, please do.  note: I am using Ubuntu 7.04

Thanks,
Eric

---

### Post by Pumalite on 2007-08-25
It's always better and safer to install through Synaptic.

---

### Post by lorderico on 2007-08-25
All right, but which packages are right to install java from.  I'm not sure which to get.

Thanks again,
Eric

---

### Post by Pumalite on 2007-08-25
SYnaptic>Search>java>java-common

---

### Post by Treebeard on 2007-08-25
> **lorderico said:**
> All right, but which packages are right to install java from.  I'm not sure which to get.

Thanks again,
Eric

If you are looking for java from Sun, there is a package in the multiverse repository (for feisty) [sun-java6-jdk]("http://packages.ubuntu.com/feisty/devel/sun-java6-jdk") or [sun-java6-jre]("http://packages.ubuntu.com/feisty/libs/sun-java6-jre").

In /etc/jvm you can edit the default paths for java. The first line is the default.
If you install sun java, then the path is something like /usr/lib/jvm/sun-java6/bin or something.

See also: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by lorderico on 2007-08-25
I had all three packages that were suggested already installed, but I reinstalled them; It still couldn't find java.  When   I looked at /etc/jvm, I got this (without the header):

/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

I'm not exactly sure what that means, and could it be causing this?  The jre and jdk on my system are installed in /usr/java

---

### Post by Treebeard on 2007-08-25
If you already have installed the package sun-java6-jre, then there should be a java executable in /usr/lib/jvm/java-6-sun/bin.

Try to run this in a console first :
```

$ /usr/lib/jvm/java-6-sun/bin/java --version

```If this works, then you can alter the file /etc/jvm like this :

```

# header ...

/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr
..

```You should also run :
```

sudo update-java-alternatives -s java-6-sun

```This should change the default java to sun and set the correct path.

---

### Post by lorderico on 2007-08-25
SOLVED IT!

first I used thissorce:
[I]
You need to add the following lines to /etc/apt/sources.list file

gedit /etc/apt/sources.list

enter these two lines and save your file

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse

Now you need to run the following command to update the source list

sudo apt-get update
[/I]

I am not sure that did anything, though.  What really helped me was this:

sudo update-alternatives --config java

I needed to configure I so my default java was the sun java option and not the "free java" option.  Note: You probably want to do the same with jar, javac, javadoc, javah, javap and javaws:   sudo update-alternatives --config jar

Thanks for the help,
Eric

---

