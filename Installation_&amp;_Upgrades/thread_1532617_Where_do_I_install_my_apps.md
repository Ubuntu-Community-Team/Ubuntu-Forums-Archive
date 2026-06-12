---
title: "Where do I install my apps?"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by elmasry.ayman on 2010-07-16
Now I understand that when installing software I should install in the /usr folder, but there are about 10 folders inside. Can anybody explain which ones are good for what?

---

### Post by davidmohammed on 2010-07-16
similar thread [here]("http://ubuntuforums.org/showthread.php?t=1527769")... hope that helps.

---

### Post by Penguin Guy on 2010-07-16
What program do you have in mind? It's usually a good idea to use apt (e.g. Software Center, Synaptic Package Manager, apt-get) to install software. If you must install anything manually, however, it should go in [FONT="Courier New"]/usr/local[/FONT].

---

### Post by Rubi1200 on 2010-07-16
This is from the official documentation:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by elmasry.ayman on 2010-07-16
> **Penguin Guy said:**
> What program do you have in mind? It's usually a good idea to use apt (e.g. Software Center, Synaptic Package Manager, apt-get) to install software. If you must install anything manually, however, it should go in [FONT="Courier New"]/usr/local[/FONT].
Well I intend to install Java Development Kit and NetBeans... where would they go?

---

### Post by elmasry.ayman on 2010-07-16
This is very confusing; there are so many folders, although the names are not unique (I can see bin, sbin, games...etc. in more than one place) but still I cant understand where to put my software, even inside the /usr/local/ folder there are 7 or 8 folders. Oh and by the way how do I uninstall a manually installed binary file?

---

### Post by oldfred on 2010-07-16
If you go into synaptic you can install from there and not have to worry about anything.
Search on:
netbeans
jdk

---

### Post by elmasry.ayman on 2010-07-16
I have to make a point clear that I DO know how to install using synaptic or apt-get, but this is not the case; I don't have any problems installing software using packages, all I need to know is what to do when installing from a binary or even compiling from source code. You know I once installed JDK and when I wanted to install Netbeans it couldn't see JDK on the system, that's why i need to know where to install software.

Is this question that hard to answer? Somebody out there must've installed from binaries before and knew where to put it!

---

### Post by oldos2er on 2010-07-16
If by binaries you mean *.bin files, the ones I've dealt with "know where to go," so to speak, same as *.deb files. Usually in /opt.

 I run "sudo make install" to install compiled code, which puts apps in /usr/local/bin.

---

### Post by elmasry.ayman on 2010-07-17
> **oldos2er said:**
> If by binaries you mean *.bin files, the ones I've dealt with "know where to go," so to speak, same as *.deb files. Usually in /opt.

 I run "sudo make install" to install compiled code, which puts apps in /usr/local/bin.
When I tried to install from a binary via the terminal, it placed the installation folder where the .bin file was, so obviously that one didn't know where to go...

---

### Post by oldos2er on 2010-07-17
If running the *.bin just extracts it, then yes you'll need to put it somewhere in your $PATH. It would help to know what program it is.

---

### Post by elmasry.ayman on 2010-07-17
I beg you to presume any list of categories and state their appropriate destination... this thread is becoming frustratingly long and off point.

---

### Post by digitalcitizenx on 2010-07-17
Merely installing any application or program should, in any modern operating system, install itself in the appropriate places within the system.

I do not recall Java needing to be manually installed.

If you just need Java to run some type of online application or service then

```
sudo apt-get install ubuntu-restricted-extras
```

should do it.

a simply Google search revealed this solution to installing Net Beans:

[http://linuxhub.net/2010/06/install-netbeans-on-ubuntu-10-04/](http://linuxhub.net/2010/06/install-netbeans-on-ubuntu-10-04/)

Remember - Google is your friend.

---

### Post by oldos2er on 2010-07-17
It's usually preferred to install programs from the repositories. To install sun-java6-jdk, you'll need to enable the partner repository first (System, Administration, Software Sources).

---

### Post by elmasry.ayman on 2010-09-01
Well I've been away for quite a while... I'm marking this thread as solved because I found out that the problem was simply that I did NOT type 'sudo' before installing the binary and therefore the proper installation location was locked (read only) and that's why the installer did not determine the appropriate location.

---

