---
title: "problem in installing j2re(java) using sudo apt-get"
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by engkeboy on 2005-09-24
I've already installed Limewire but it won't run.. maybe because i don't have java.. so i refer to ubuntuguide.. i just copy this code from ubuntuguide.. but it doesnt work.. 

[B]sudo apt-get install sun-j2re1.5
java -version
[/B]

it says that.. 
[B]
"E: Couldn't find package sun-j2re1.5"[/B]

need help.. ](*,)

---

### Post by phex on 2005-09-24
install it manually. downlaod the jre from [https://sdlcweb3a.sun.com/ECom/EComActionServlet;jsessionid=1FB7191C92E1733B2ACE8A12EB2B2A6F](https://sdlcweb3a.sun.com/ECom/EComActionServlet;jsessionid=1FB7191C92E1733B2ACE8A12EB2B2A6F). download the    	jre-1_5_0_05-linux-i586.bin file and then follow the instructions i have written in this thread:
[http://ubuntuforums.org/showthread.php?t=68198](http://ubuntuforums.org/showthread.php?t=68198)

if you later want to program with java, you should download the SDK (Standard Devolpement Kit) instead of the JRE version.

good luck. ;)

---

### Post by phex on 2005-09-24
but try to search in the forum. somewhere I cannot exactly remember, there was a post from which repository you can download the java version. you have to specify it in synaptic or in the /etc/apt/sources.list.
You can also download the rpm package
jre-1_5_0_05-linux-i586-rpm.bin from [https://sdlcweb3a.sun.com/ECom/EComActionServlet;jsessionid=1FB7191C92E1733B2ACE8A12EB2B2A6F](https://sdlcweb3a.sun.com/ECom/EComActionServlet;jsessionid=1FB7191C92E1733B2ACE8A12EB2B2A6F)
and try to use "alien -d jre-1_5_0_05-linux-i586.rpm" after you have accepted the license agreement. following with dpkg -i jre-1_5_0_05-linux-i586.deb.

---

### Post by phex on 2005-09-24
I did the search for you:
[http://ubuntuforums.org/showthread.php?t=65229&highlight=j2re1.5](http://ubuntuforums.org/showthread.php?t=65229&highlight=j2re1.5)

---

### Post by imagine on 2005-09-24
Nvm, mistake by me.

---

