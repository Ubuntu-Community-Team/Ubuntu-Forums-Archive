---
title: "Installing Sun Java 7"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by rogerfgay on 2011-09-25
I tried installing the sun java 7 jdk rpm by following instructions for converting it to a deb and then installing. I then tried to set the alternative config to the java 7 installation. Java 7 did not appear on the list. 

Now I'd like to follow sun's instructions. As a first step, it wants me to uninstall the other versions of java. I don't know how to do that. Can't even find them. (I guess I don't have to say that I'm relatively new to Linux now.)


By the end of this discussion, I'm hoping to have sun java 7 (jdk / jre) properly installed and operating as the default. - Thank you.

---

### Post by ibutho on 2011-09-25
It's not normal to install rpms on Ubuntu (its a debian based distro so uses deb packages). Try the instructions [here]("http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html").

---

### Post by rogerfgay on 2011-09-25
Brilliant. Thank you. I've confirmed installations with java(c) -version and am now running the app built with java 7.

In addition to the instructions on the page, I also had to rerun

sudo update-alternatives --config java

When I did that, I noticed that I have two 1.7.0 installations listed.

---

### Post by rogerfgay on 2011-09-25
So, I'd still be interested in learning how to uninstall. The second 1.7 doesn't need to be there. Neither do the 1.6s.

---

### Post by raja.genupula on 2011-09-25
you can uninstall it from synaptic package manager.type java in the search box and select the jdk version which you wanna remove.

All the best.

---

