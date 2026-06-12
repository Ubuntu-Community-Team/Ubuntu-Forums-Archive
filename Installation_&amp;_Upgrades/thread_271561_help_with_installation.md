---
title: "help with installation"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by troubl3dmind on 2006-10-04
I need some help with something.  I'm really new to linux, and i'm trying to install frostwire and java so i can run it.  I have no idea how to do this.  I messed around for a while trying to figure out how to do it, but when i go to the package manager trying to install java it says Error: Dependency is not satisfiable.  Did i download the wrong package?  The one i'm trying to install is sun-java5-jre_15.0-06-1_all.deb.  To tell you the truth i don't know if i've installed frostwire and can't install java, or if i've installed java and can't install frostwire... but when i type frostwire into the terminal it says:

bobby@bobby-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
bobby@bobby-desktop:~$



I'm not completely computer retarded, i know mostly windows though, and getting the linux basics down is hard.  Any help would be greatly appreciated... ](*,)

---

### Post by K.Mandla on 2006-10-04
This is a good place to start, if you haven't seen it already.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Usually, just *sudo aptitude install sun-java5-bin* will download, install and set it up. If you haven't tried that, give it a shot and then restart Frostwire.

You could also try *sun-java5-jre* and *sun-java5-plugin* ... the latter installs the plugin for Firefox.

---

