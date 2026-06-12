---
title: "[SOLVED] SCIM and sun-Java6"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by apamatos on 2008-07-16
Hello

I have a nasty problem that I need to fix
I had to activate SCIM to get deadkeys (portuguese) working inside VirtualBox in Hardy and used the method described in
[http://www.ubuntugeek.com/fix-for-scim-errors-in-ubuntu-gutsy-and-hardy.html](http://www.ubuntugeek.com/fix-for-scim-errors-in-ubuntu-gutsy-and-hardy.html)
This fixed virtualbox, but now deadkeys stoped working in java software (freemind, compendium).

I am unable to find relevant information about this. Tryed both XIM and scim-bridge as described in the above link, but its the same.

Can anyone help please?

AP Alves de Matos

---

### Post by jamesstansell on 2008-07-16
How did you install java, and how are you running freemind?

---

### Post by apamatos on 2008-07-16
Hello

Thanks for your help

Java was installed from the repositories with synaptic - no aditional configuration. Just checked that sun-java6-bin, sun-java6-fonts and sun-java6-jre are installed.

Freemind and Compendium - I use mainly compendium, but freemind is more widespread and has the same problem - are being launched from the command line terminal, that responds normally to the deadkeys.


Cheers

---

### Post by jamesstansell on 2008-07-16
Is the command line running in virtual box?

What does "java -version" show?

---

### Post by apamatos on 2008-07-17
Usually virtualbox is run from the menu - no command line.
Today I run it from the command line - terminal remains open, but otherwise no change in virtualbox and in compendium


java -version result:

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

Cheers
AP

---

### Post by jamesstansell on 2008-07-17
You might try some of these, but I'm honestly not sure if they'll help.

 * 32bit virtualbox instead of the 64bit you appear to be using
 * java -client vs java -server when starting compendium
 * newer version of java (see below)

I don't think any of these are packaged for hardy yet, but the ones from Sun can be installed without apt, and the Intrepid packages can likely be installed on hardy by downloading the packages manually.

 * Java 6 u7 has been released
 * Java 6 u10 is in beta, with a release candidate expected very soon
 * OpenJDK6 has newer versions with changes incorporated from both of those

I'm not sure that the changes fix any SCIM bugs (I don't use SCIM myself) but I think there were some fixes that might be related.

---

### Post by apamatos on 2008-07-17
Thanks

Just on or two questions about this:

1. Can dead keys be enabled in VirtualBox without SCIM? I use SCIM just because of VirtualBox. I was unable to find any other solution but earlier Ubuntu versions did not used SCIM for this!

2. Can the 32 bit VirtualBox be installed as you suggest in a machine runing the AMD64 version of Hardy??? May be this version does note use SCIM. Also, may be debian versions do not need SCIM and I will be able to remove it. 
Any suggestion? If you don't know I'll just try (but I will be destroying part of my working system)

If these fail I'll try the new versions of java in the hope that someone has noticed and cared to fix SCIM incompatibilities

---

### Post by jamesstansell on 2008-07-17
Does this help any?

[http://ubuntuforums.org/showthread.php?t=828631](http://ubuntuforums.org/showthread.php?t=828631)

---

### Post by apamatos on 2008-07-17
YES 

it worked !!!

Many many many thanks.

I still have an unsolved strugle with Hardy AMD64 (probably a QT4 bug), but I will post another thread.


Forever grateful

AP Alves de Matos

---

