---
title: "What am I supposed to do with a Tar.GZ file?"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by athealwashington on 2008-08-07
I am new to linux and I downloaded this game which is in Tar.GZ format can some body give step by instructions on what I am supposed to do with it?



The game is called: Tux a quest for herring

---

### Post by spiderbatdad on 2008-08-07
First, it is advisable to search the synaptic package manager for the program, then google for a .deb package of the program. If installing from source is your only option, you will, at the very least need "build -essential"```
sudo apt-get install build-essential
```

Next right click on the package and extract it. Then browse into the program folder and look for a readme and/or install file, containing instructions for installing the package.

If your package uses ./configure. make, sudo make install, you might want to take a look at "checkinstall" as an alternative to make install.
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

Not all source packages come with an uninstaller, and can be difficult to remove, occasionally. Checkinstall will add the package to your package manager, for easy removal. Checkinstall is not 100% guaranteed to work, but is still a good first option.

---

### Post by CameO73 on 2008-08-07
A .tar.gz file is a compressed collection of files (comparable with the (more popular in Windows) .zip extension). The easiest way to extract the files is to use the Archive Manager (available in the default Ubuntu installation). Just double-click on the file and Archive Manager should open, then Extract to the folder of your choice.

What you should do afterwards depends on the contents. Usually there is a README or INSTALL file that gives you instructions on what to do. Sometimes it's as easy as running a .sh file (script file). 

One word of advice: only run/install software from locations you trust!

---

### Post by Pumalite on 2008-08-07
Check this too:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by tuxxy on 2008-08-07
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

