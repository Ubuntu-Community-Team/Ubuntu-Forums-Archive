---
title: "Java problems"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by Duroon on 2007-11-04
Ok I need to install Java 6 in order to get an app to run. I have downloaded the SUN Java 6 from their site. Now what do I do with it? I have it in a nice little folder in my home directory now but no clue what to do next.

---

### Post by taurus on 2007-11-04
You can install Sun's java from synaptic.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by pismikrop on 2007-11-04
you may install java-6 by using:

aptitude install sun-java6-jre

for a complete java6 system:

aptitude install sun-java6-jdk

---

### Post by rockballad on 2007-11-05
My network here is too slow to install online. Thus, I downloaded the JRE package to install offline. But after that, I don't know how to add java path to PATH environment. I do search a lot, but no answers for my question. I wanna use the latest Java from terminal. Could you help me? Thanks

---

### Post by pismikrop on 2007-11-05
you may add to /etc/bash.bashrc file

sudo gedit /etc/bash.bashrc

and you may add this line at the end of the file:
export PATH=$PATH:/your_path_to_java_bins

then reboot system.

---

### Post by gertvs on 2007-11-05
I imagine you must edit the permissions of the file to 'executable' and then run it in a terminal.
Right click the file in Nautilus, select properties, then go to the permisions tab.
After enabling execute you should be able to run the file by double clicking it.

---

### Post by linaxe on 2007-11-05
ya im having java problems as well try ummmm try going to add and remove applications and put in java that might work  :)

---

### Post by rockballad on 2007-11-05
Don't know why exactly, but when I type "java -version" in Terminal, it gives me the original java of Ubuntu 7.10  , then someone told me that:

- $ cd usr/local/lib
- $ sudo sh '/path/to/jre-6u3-linux-amd64.bin
- $ cd /usr/local/bin
- $ sudo ln -sf ../lib/jre1.6.0_03/bin/* .

(note the dot at end of line)

Then reboot. It works now. Many ways have been tried, but this way may work (not very sure :P).

Cheers,

---

### Post by pismikrop on 2007-11-06
try:
update-alternatives --config java
and
update-alternatives --config javac

---

### Post by Duroon on 2007-11-07
> **pismikrop said:**
> try:
update-alternatives --config java
and
update-alternatives --config javac

Thank you! That finally did the trick for me.

---

