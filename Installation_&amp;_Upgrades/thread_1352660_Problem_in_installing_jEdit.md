---
title: "Problem in installing jEdit"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by blueprats on 2009-12-11
Hi
I am new to this forums. For few months I used a different flavor of linux, but now I have switched to ubuntu. Two days back I installed ubuntu 9.10. It is a cool operating system. I do programming in java, so I downloaded java-6 from the sun's official site. I installed it manually, that is, it was a .bin file. I did not used apt-get to install sun java. After extracting the file I moved the java folder to /usr/lib/java. Then for running java programs the PATH and CLASSPATH was set in user's .bashrc profile and root's .bashrc profile. 
I like Eclipse IDE, but I would like to install jedit. Now the problem is, when I try to install jedit as
> sudo apt-get install jedit 
//the repositories have been correctly set to the sources file
Now, apt-get reads all the data and says that you have to install java (for dependency) for installing jedit. That is correct, jedit needs java. As I said, I have installed java and I run even programs and they work fine. I am not that experienced in linux, the problem might be that apt-get does not reads java, that is already installed. Is there a file or something like that where apt-get searches for the installed programs. May be I have not provided the link to the necessary location. Any help no this. Thanks in advance

---

### Post by pricetech on 2009-12-11
I'm running Hardy.

I use JEdit on a regular basis.  I installed Jave via Synaptic, but I don't recall how I installed JEdit, but I probably used Synaptic for that as well.

I'd try installing Java again via the Package Manager to see if that helps.

---

### Post by jamesstansell on 2009-12-15
> **blueprats said:**
> Hi
I am new to this forums. ... As I said, I have installed java and I run even programs and they work fine. I am not that experienced in linux, the problem might be that apt-get does not reads java, that is already installed. Is there a file or something like that where apt-get searches for the installed programs. May be I have not provided the link to the necessary location. Any help no this. Thanks in advance

Welcome!

I think you have at least 3 options:

1) satisfy the java dependency for the jedit package, possibly by installing the openjdk-6-jre (you would still be able to use the manually installed java if you wanted)

2) override the java dependency, but I haven't tried that for a long time and don't know exactly how; we used to do it on debian but it's probably almost never done on ubuntu

3) just install jEdit from jedit.org; if their .deb file doesn't work you should be able to use the java-based installer

Regards,

-james.

---

