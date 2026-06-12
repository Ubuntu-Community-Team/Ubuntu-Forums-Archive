---
title: "Java package installed via Synaptic not recognized"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by dimechen on 2010-02-25
[SIZE=2]I installed libjson-java and everything listed as dependencies via Synaptic and naively thought that I can now do
[/SIZE]import net.sf.json.*;
[SIZE=2]and it will simply work.  (This is not an eclipse but a general question; simple editor and running javac in the shell.)
It doesn't. I get this error message:[/SIZE]
The package net.sf.json does not exist.[SIZE=2]
I checked what was installed and found json-lib-2.2.3.jar in /usr/share/java.
There are some other .jar-files in there that I also can't seem to use. 
Restarting the computer (a netbook running the ubuntu netbook remix) or putting /usr/share/java on the classpath does not help. 
What can I do to let my java know where to find those packages?
Thanks for any advice.[/SIZE]

---

### Post by n0dix on 2010-02-25
```
export CLASSPATH=/usr/share/java/json-lib-2.2.3.jar:.
```
This is a temporary solution.

---

### Post by Mighty_Joe on 2010-02-25
> **dimechen said:**
> [SIZE=2] putting /usr/share/java on the classpath does not help. 
[/SIZE]

You have to specify the actual JAR file on the classpath, as n0dix indicates.
Personally, I either use [Ant]("http://ant.apache.org/") to build my Java projects or, for smaller projects, write a Bash script to set the CLASSPATH and run javac.  
Using the system-wide CLASSPATH for multiple projects gets real tedious real quick.

---

### Post by dimechen on 2010-02-25
Thank you, that works. But as you said, temporarily. 
Does anyone have an idea for a long-term solution?
Also, is this what is supposed to happen when I install a java package via synaptic - that it is shoved into some folder and I still have to add it to the classpath manually?

---

### Post by Mighty_Joe on 2010-02-26
> **dimechen said:**
> Does anyone have an idea for a long-term solution?

I gave you mine in my previous post

> **dimechen said:**
> 
Also, is this what is supposed to happen when I install a java package via synaptic - that it is shoved into some folder and I still have to add it to the classpath manually?
I don't know about Synaptic because I develop Java primarily on Windows and Solaris, but that is how it is done on those platforms.

---

### Post by dimechen on 2010-02-27
Hi Joe!
I did see your previous message, but only after I posted my own. Sorry for the confusion.
Thanks also for the second message. I'm a bit less confused about downloading Java packages now. : )
- dimechen

---

