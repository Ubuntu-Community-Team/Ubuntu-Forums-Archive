---
title: "NetBeans isn't opening on Ubuntu 18.04"
date: 2018-10-06
forum: Installation &amp; Upgrades
---

### Post by loknath-dhar on 2018-10-06
I'm totally a new Ubuntu Linux user and I thought to start learning java with this new environment. I started to install java and NetBeans by searching google, java installed but not NetBeans. I searched more but none work for me.

 Before posting this, I also searched in ask ubuntu and found some solutions about this but sorry to say, none work for me. Netbeans 8.2 just doesn't start on ubuntu 18.04. I installed java version 1.8.0_181. with this, I also tried installing java 10 but also failed here as NetBeans 8.2 doesn't support 10. So what can I do?


  And I want another suggestion, that is, java is updated and it's current version is jdk10; which version I should go for learning? 8 or 10? What should I do, I am totally confused.

---

### Post by Holger_Gehrke on 2018-10-06
The differences between Java 8 and 10 are mostly in advanced features which you probably won't care about while learning the language, although there are supposedly some performance improvements in Java 10 involving better / faster garbage collection.

The easiest way to install netbeans would be to use the version from the repositories, so unless you've got your heart set on the latest and greatest, a simple 'sudo apt-get netbeans' should get you netbeans 8.1 installed and ready to roll.

Unless you've programmed before and used an IDE for that, I would not use an IDE while learning a programming language. Modern IDEs are big and complicated things, learning to use them and to find the features you need from all the capabilities they offer is a learning process of it's own. They also tend to hide (mis-)features of the underlying tools that you might need to know about and expose features that you might not need (yet). They also offer assistance for producing 'boilerplate' code - which is nice, but while learning to use a language you should write that stuff yourself so you know what it does. When learning a new programming language - even one which can be used in my IDE of choice (eclipse, which can be used with many languages thanks to a plugin architecture) - I go back to a simple editor and the command line for calling the compiler or interpreter.

Holger

---

