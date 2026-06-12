---
title: "Azureus + JDK"
date: 2005-09-25
forum: Installation &amp; Upgrades
---

### Post by hdude on 2005-09-25
Hi fellow Ubuntians,

I'm having trouble installing azureus  :cry:  .  Can a good samaritan help out this dude?  Here's the error that I get:
```
$ sudo aptitude install azureus
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  azureus: Depends: sun-j2sdk1.5 which is a virtual package. or
                    java2-runtime which is a virtual package.

```

I've installed jdk-1_5_0_05-linux-i586.bin from sun's site to /usr/local and created symbolic links of java and javac like shown:
```
$ ls -l /usr/bin/java*
lrwxrwxrwx  1 root root 31 2005-09-24 15:35 /usr/bin/java -> /usr/local/jdk1.5.0_05/bin/java
lrwxrwxrwx  1 root root 32 2005-09-24 15:36 /usr/bin/javac -> /usr/local/jdk1.5.0_05/bin/javac

```

I'd like to continue using the jdk and not install a separate jre...can anyone help me pls?

Thank in advance  :grin:

---

### Post by hdude on 2005-09-25
whoops messed up...here's the symlinks...

```
$ ls -l /usr/bin/java*
lrwxrwxrwx  1 root root 31 2005-09-24 15:35 /usr/bin/java -> /usr/local/jdk1.5.0_05/bin/java
lrwxrwxrwx  1 root root 32 2005-09-24 15:36 /usr/bin/javac -> /usr/local/jdk1.5.0_05/bin/javac

```

---

### Post by Leif on 2005-09-25
There are three solutions I can think of :

1) Download and install azureus yourself. It can update itself etc., so it's not such a big pain to maintain

2) Redo your java installation, packaging it so apt will recognize it 

3) Redo your java installation, using the packages here :
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java

---

### Post by hdude on 2005-09-26
Thank you oh so very much for the solution and the quick response  :mrgreen: .  I chose to take the second choice.  I have two question regarding what I just did.  I haven't removed the old copy.
Does this mean I have 2 copies of Java running on my machine now or did it just "update" the apt with a dummy package?
Where would the dpkg select for the target path of the installation (I'm kind of confused on this one since the jdk bin file just chose to install in the current directory)?

---

### Post by sig_UVa on 2005-09-26
I installed Azureus on Friday and it was a MAJOR pain...

The things that tripped me up:

1)  Get Java running first, like the previous poster said.  Get it from the main site (note** don't get the RPM package).
I had to create the virtual link from where Java was installed to where Firefox is looking for it, twice.  I had to delete the first link (said it was 0 Kb in size) and relink.  Java worked.

2)  Install Azureus via the package provided on the Azureus website.

3)  Create a link/shortcut on your desktop that fires up the Azureus app....  It would not get itself into the KDE menu automatically for some reason.

4) edit the KDE menu accordingly if you want Azureus to appear there.


I am a noob so I know I am not giving a ton a detail....  Post back if you have problems with any of these steps.

---

### Post by Leif on 2005-09-26
[QUOTE=hdude]Thank you oh so very much for the solution and the quick response  :mrgreen: .  I chose to take the second choice.  I have two question regarding what I just did.  I haven't removed the old copy.
Does this mean I have 2 copies of Java running on my machine now or did it just "update" the apt with a dummy package?
Where would the dpkg select for the target path of the installation (I'm kind of confused on this one since the jdk bin file just chose to install in the current directory)?[/QUOTE]

do a locate java and look through the results to see if it's installed in two different locations. if you installed the sdk, searching for javac will be quicker.

---

