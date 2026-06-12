---
title: "Java problem (i can't play runescape or like this games)"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by ihvan on 2008-03-19
i searched on this forum. and i tried all things. however they dont solve my problem.

firstlyi i installed iced tea. it work on [http://www.java.com/tr/download/help/testvm.xml](http://www.java.com/tr/download/help/testvm.xml). 
however i cant play runescape. i just saw a gray screen. than a message (applet couldnt loaded).

secondly i installed java 1.6 using synaptic again. but i saw a gray screen again.

and i tried to install from java.com. this time i didnt see a gray screen. because i saw "you have to install plugins" message.

i was able to play runescape on fedora 8 . (before the ubuntu). 

is there anyone have an idea what must i do?

---

### Post by AntoC on 2008-03-19
HI Ihvan,
I would suggest you to uninstall the Java installed with Synaptic (with complete removal..)
and retry with the add/remove, if that does not work either try downloading it from the java site and once you have the script double click on it and open in terminal follow the instructions and there you go...
AntoC

---

### Post by mk1w86 on 2008-03-19
Have you tried installing the sun-java6-jre package which I think is the latest version available through the Ubuntu repositories - you may have to enable universe or multiverse repositories to install the package.

You may have to install the sun-java6-plugin (which allows java to run in firefox or other web browsers) package separately as I can't remember whether marking the sun-java6-jre for installation in Synaptic marks this one automatically for installation.

I installed the sun-java6-jre package and everything else that installs with it on my system and java seems to work fine.

Also I assume you are running Ubuntu 7.10.

If you need any further help with this just ask and I will see what I can do.

---

### Post by ihvan on 2008-03-20
i have a x86 64-bit  intel card. and i cant find sun-java6-plugin. 
it cant support applets. or i couldt do it. 
i tried to install sun-java6-jre. but firefox didnt accept it. (because i cant find sun-java6-plugin for 64 bit)
i installed sun-java5 instead of 6. then i saw a grey screen.

(im using ubuntu 7.10)

---

### Post by bigrob301 on 2008-06-21
try running low res instead of high and update to sun java 6 restart firefox thats how i got it to wrk thanks

---

