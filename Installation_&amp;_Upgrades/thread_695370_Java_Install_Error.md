---
title: "Java Install Error"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by igfud on 2008-02-13
When trying to install Java, I went to Add/Remove Applications, searched for "sun java" and tried to install any of the search results.  I receive the following error:

```
Cannot install 'sun-java5-plugin': This application conflicts with other installed software.  To install 'sun-java5-plugin' the conflicting software must be removed first.  Switch to the 'synaptic' package manager to resolve this conflict.
```

I receive this same error when trying to install Java 6.  I tried installing the package sun-java6-jre through the Synaptic Package Manager, but received an error about missing packages unable to be resolved.

I also tried downloading the self-extracting install file for Linux from Java's website.  I created a folder in my home folder named 'java' and tried installing it by entering ./ and the filename.  It *seemed* to install okay: I agreed to the terms of use and it proceeded through the install.  However, when I try to use a Java web applet in Firefox, all I get is the little green puzzle piece and the alert bar telling me to install Java.  When I use Firefox's Plugin Finder Service to try and install either the Java SE 6 or SE 5.0 Plugins, I receive an error:

```
Can not install 'sun-java6-plugin' (E: Unable to correct problems, you have held broken packages.)
```

I'm currently using Ubuntu 7.10.  I know I had Java installed on 7.04 using just the Add/Remove Applications UI.  Any ideas on why I can't seem to get Java to install?  I'm still a n00b as far as the terminal is concerned, so any instructions are appreciated. :)

I also found a similar thread [here]("http://ubuntuforums.org/showthread.php?t=615367").  It didn't seem to be of much help, though.

Thanks!!
igfud

---

### Post by zvacet on 2008-02-13
```
sudo apt-get -f install
```

or in **synaptic>edit>fixbroken packages**

---

### Post by igfud on 2008-02-13
Thanks for the post.  When I run the given command, I receive the following output:

```

igfud@igfud-laptop:~$ sudo apt-get -f install
[sudo] password for igfud:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I also tried the "Fix Broken Packages" in the synaptic manager, but it doesn't seem to do anything....

I still receive all the same errors when trying to install Java.

Thanks,
Igfud

---

### Post by taurus on 2008-02-13
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure you have a check mark for all the lines except the last one, Source code, and the Cdrom in the window below.  Close it and press Refresh.  Now, click the Search option and type in sun-java6-jre and install it from there.

---

### Post by igfud on 2008-02-13
Worked great, thanks!  JRE 6 installed without problem, but it didn't seem to run web based Java Applets.  I went ahead and installed the 5 Plugin using the Add/Remove Applications UI and it installed without error and works great.

Thanks,
Igfud

---

