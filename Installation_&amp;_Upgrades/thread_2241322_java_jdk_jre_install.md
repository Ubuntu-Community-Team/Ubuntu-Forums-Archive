---
title: "java jdk jre install"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by maclenin on 2014-08-25
With primary reference to this [well-worn guide]("http://askubuntu.com/questions/56104/how-can-i-install-sun-oracles-proprietary-java-jdk-6-7-8-or-jre") and the intention of using the jre piece of the jdk package, most extensively, my recent clean install of oracle's **jdk** (1.8.0_20) in xubuntu (14.04.1 / 64-bit) **seems** to have gone without a **[COLOR="#008000"]hitch[/COLOR]**?

1. I downloaded [jdk-8u20-linux-x64.tar.gz]("http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html") to a convenient folder ("downloads").

2. I then unpacked the tar (without sudo) inside "downloads"
```
**tar -xvf jdk-8u20-linux-x64.tar.gz**
``` 
3. Created the install target directory
```
**sudo mkdir /usr/bin/jvm**
```
4. Moved the relevant files from within "downloads" to the install target directory
```
**sudo mv ./jdk1.8.0_10 /usr/lib/jvm/jdk1.8.0_20**
```
5. Ran the prescribed --install routines with priorties (1) assigned 
```
[B]sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.8.0/bin/java" 1
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.8.0/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jdk1.8.0/bin/javaws" 1
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.8.0**[COLOR="#FF9933"]/jre[/COLOR]**/bin/java" 1[/B] <----- this **[COLOR="#FF9933"]/jre[/COLOR]** alternative was suggested, [here, in its step 10]("http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux").

```

6. Verified the proper --config java status 
```
**sudo update-alternatives --config java**
[sudo] password: 
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                             Priority   Status
--------------------------------------------------------------
  0            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java    1071      auto mode
  1            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java    1071      manual mode
  2            /usr/lib/jvm/jdk1.8.0_20/bin/java                 1         manual mode
* 3            /usr/lib/jvm/jdk1.8.0_20/jre/bin/java             1         manual mode

Press enter to keep the current choice
[*], or type selection number:
```

7. Confirmed the (correct) java version
```
**java -version **
java version "1.8.0_20"
Java(TM) SE Runtime Environment (build 1.8.0_20-b26)
Java HotSpot(TM) 64-bit Server VM (build 25.20-b23, mixed mode)
```

The **[COLOR="#008000"]hitch[/COLOR]**?

8. After installing oracle jdk (as the first and only java installation on my computer), I installed libreoffice, which seemed to also install openjdk - without prompting - as one of its dependencies?

9. After installing libreoffice and when I try to open .jar files using right-click, openjdk is the only (java-related) "Open With" option offered (I did not try to open .jars in this manner before I installed libreoffice).

10. However, I am able to open .jar files with the oracle version - using the command line (or desktop launcher) - as shown in this snippet:
```
**java -jar cookie.jar**
...
[18:30:10 INFO]: Current time is Aug 25, 2014 6:30:10 PM
[18:30:10 INFO]: System.getProperty('os.name') == 'Linux'
[18:30:10 INFO]: System.getProperty('os.version') == '3.13.0-34-generic'
[18:30:10 INFO]: System.getProperty('os.arch') == 'amd64'
[18:30:10 INFO]: System.getProperty('java.version') == '1.8.0_20'
[18:30:10 INFO]: System.getProperty('java.vendor') == 'Oracle Corporation'
[18:30:10 INFO]: System.getProperty('sun.arch.data.model') == '64'
[18:30:10 INFO]: JFX is already initialized
[18:30:10 INFO]: Refreshing local version list...
[18:30:11 INFO]: Refreshing remote version list...
[18:30:11 INFO]: Refresh complete.

```

11. There is no "graphical" evidence that the oracle version of java is installed - within the application menu structure - and it cannot be accessed "graphically" - i.e. via right-clicking on a .jar.... Though oracle jdk / jre seems to be the primary java implementation on my system as borne out through the verifications and confirmations I show above - and is deployed when called using "java" - though only via the command line.... Curious?

Any thoughts? Does the method of install look sound? Anything I should check / fix?

Thanks for any guidance!

---

### Post by ajgreeny on 2014-08-25
The majority of java packages are not dependencies of LO as far as I can see but only either recommended or suggested packages.  The only java dependency is libreoffice-java-common, so you should be able now to remove the openjdk packages that you don't want.

I suspect your apt preferences are set to install recommended packages by default, hence the installation of the openjdk packages (the oracle packages could not be installed as they are no longer in the repos, of course).

Depending on how you install packages you can choose not to add recommended packages as the default if you wish; I use synaptic generally and it is an option in the preferences for synaptic. If you use apt-get in command line you need the option **--no-install-recommends**.  I have no idea about software-centre as I never use it but it must be there somewhere, I'm sure.

---

