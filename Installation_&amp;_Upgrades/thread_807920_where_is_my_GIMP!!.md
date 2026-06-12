---
title: "where is my GIMP?!!"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by newbreed on 2008-05-26
For some strange reason, or maybe I tripped over my noobness again but my GIMP is gone...ran away:(

It all start with that #*&^%GIMPSHOP!!!.... I never should have touched it, I know that ubuntu is builded in tree like form..so to install a program as you would in windows is totally different. instead of pumping a bunch of files in one location it builds itself by grabbing a little here and a little there...correct me if I'm wrong but I'm pretty sure. So I then tried to install this gimpshop, dam thing never worked, and I deleted something, by mistake, that I must really need to run other stuff like my limewire, it also up and ran out the door this morning.

Can some one help me reinstall gimp from scratch? sudo apt-get remove or install gimp will not be enough I'm sure... I removed gimp with: sudo apt-get remove gimp....seemed to work.... I re-installed with: sudo apt-get install gimp...seemed to work fine...but now it will not completely open, seems to try and start up, I see it in bar, but never fully starts up...same with limewire..


Any help would be much appreciated.

---

### Post by PmDematagoda on 2008-05-26
Try:-
```
sudo apt-get install gimp
```

---

### Post by newbreed on 2008-05-26
tried that, installed just fine, but will not completely open, starts..I can see that on bar, but just goes away and never opens.

---

### Post by PmDematagoda on 2008-05-26
Post the output of:-
```
gimp
```
in a terminal.

---

### Post by newbreed on 2008-05-26
output after install

> miguel@miguel-laptop:~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:20510): LibGimpBase-WARNING **: gimp: wire_read(): error

** (gimp:20510): WARNING **: Invalid borders specified for theme pixmap:
        /home/miguel/.themes/MacOS-X/gtk-2.0/entry2.png,
borders don't fit within the image
miguel@miguel-laptop:~$ 


but with errors...something about MacOS-X...that has to be my theme, well I changed it to see what happens...same results...seems to want to start but doesnt....BUT it did start up after install

---

### Post by newbreed on 2008-05-26
thanks anyways..I guess until I learn a little more, I'll just type gimp into terminal..:popcorn:

---

### Post by newbreed on 2008-06-06
wondering if anyone has any clue...I can start it when typing gimp in terminal but with same resualts....please?


laptop:~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:20212): LibGimpBase-WARNING **: gimp: wire_read(): error

---

### Post by Rallg on 2008-06-06
If all else fails, you can try a radical reinstall. In Synaptic, remove GIMP oompletely. If you must remove any files not specific to GIMP, then you will have to think about the consequences.

Then, manually remove any residual configuration files, wherever they may be. In Terminal:

gksudo nautilus

gives you the file manager with privileges. Make hidden files visible. Then browse around your file system, looking for folder such as .gimp and eliminating them wherever you find them. Try your home folder (by username), /etc, /usr/local, and so forth.

Reboot, then re-install GIMP.

I haven't done this with GIMP, but at one point I had to do it after I had mangled Firefox.

---

### Post by newbreed on 2008-06-06
funnything, I just noticed that my limewire does the very same thing..so I went ahead and luanched all other progrsams and all but gimp and limewire come up...I enter limewire into terminal and this is out put

```
miguel@miguel-laptop:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading LimeWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:62)
	at com.limegroup.gnutella.gui.Main.main(Main.java:40)

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.5+)
The version of Java in your PATH is:
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Server VM (build 1.6.0-b09, mixed mode)

```



could it be something to do with sun java like it state above?

---

### Post by PmDematagoda on 2008-06-06
The Limewire problem may be because you are using OpenJDK instead of Sun Java. But for the GIMP problem, try this:-
1)```
sudo apt-get remove --purge gimp
```
2)```
sudo apt-get install gimp
```

---

### Post by newbreed on 2008-06-06
thank you PmDematagoda but same deal, nothing happens, is see it starting up in nav bar 'the bar at the bottom'.. but never fully loads up..so I type gimp in terminal again and I think its the same error, maybe longer.. thanks for help guys I have a few projects on hold, I crossed over from photoshop'gave it completely up' ..gimp has really grown on me..:guitar::guitar:

```
miguel@miguel-laptop:~$ sudo apt-get remove --purge gimp
[sudo] password for miguel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmpich1.0gf libgfortran2 fftw2 proj pdl lesstif2 libcsiro0 libhdf4g
  libplplot9 libqhull5
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gimp* libgimp-perl*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 11.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 168719 files and directories currently installed.)
Removing libgimp-perl ...
Removing gimp ...
Purging configuration files for gimp ...
miguel@miguel-laptop:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmpich1.0gf libgfortran2 fftw2 proj pdl lesstif2 libcsiro0 libhdf4g
  libplplot9 libqhull5
Use 'apt-get autoremove' to remove them.
Suggested packages:
  gimp-data-extras libgimp-perl
Recommended packages:
  gimp-gnomevfs gimp-libcurl gimp-python
The following NEW packages will be installed:
  gimp
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3929kB of archives.
After this operation, 10.9MB of additional disk space will be used.
Selecting previously deselected package gimp.
(Reading database ... 168388 files and directories currently installed.)
Unpacking gimp (from .../gimp_2.4.5-1ubuntu2_i386.deb) ...
Setting up gimp (2.4.5-1ubuntu2) ...

miguel@miguel-laptop:~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:11370): LibGimpBase-WARNING **: gimp: wire_read(): error

```

---

### Post by luoenzhen on 2008-11-02
The gimp you installed by apt-get is different version as what you typed in terminal. One is 2.4, the terminal one is 2.2.
I have the same problem, although it's 2.6 now by "apt-get install gimp".

---

