---
title: "Easy Way to Locate Programs?"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by JMorg on 2008-08-26
I have been searching the forums and can't seem to find a thread that discusses methods to locate installed programs/files. I am curious if there is a terminal command that will print out the directory of a previously installed program or if there is an easy way to hunt down a program that was installed via Synaptic Package Manager because I am currently running into an issue where I installed a program but cannot find the the physical program to load it.

---

### Post by finer recliner on 2008-08-26
if you want to know where a program is, like pidgin for example, just type:

```
which pidgin
```

and you'll be told where that application is stored.


most applications are stored in one of the folders in your PATH
the folders in your PATH are:
```
echo $PATH
```

---

### Post by JMorg on 2008-08-26
ah perfect, thank you very much. I figured it would have been an easy question lol. That which command could come in handy.

---

### Post by JMorg on 2008-08-26
Now is there also a way to use terminal to manually force the program to load? Seeing that I found the directory where the program installed but am unable to load any of the files within the folder? In particular I am trying to load "Kismet". 

Scratch that, my issue was based within the .conf file, Thanks again for the help!

---

### Post by oldos2er on 2008-08-26
In Synaptic Package Manager, click 'Status' in the lower left corner, then 'Installed.' Right-click on a package, choose 'Properties,' then 'Installed Files.' This will show the directories where each file in a package has been installed. Most executables are in /usr/bin .

---

