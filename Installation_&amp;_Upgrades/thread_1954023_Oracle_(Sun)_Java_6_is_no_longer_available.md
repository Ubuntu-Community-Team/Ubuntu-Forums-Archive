---
title: "Oracle (Sun) Java 6 is no longer available"
date: 2012-04-07
forum: Installation &amp; Upgrades
---

### Post by webusr1 on 2012-04-07
I understand Oracle (Sun) Java 6 is no longer available to be distributed by Ubuntu, because of license issues.  


However, I'm taking classes at the University using Ubuntu 10.04 with Open JDK and Open JDK is not doing the job. I've reported the problem to the University, but they really don't care about this problem and I've been told to use Oracle (Sun) Java 6... :_(


Is there a PPA that I can use to load Oracle (Sun) Java 6, and does that mean I have to remove Open JDK? And, does Ubuntu have the procedure documented somewhere for configuring Oracle (Sun) Java 6?


Thanks!

---

### Post by Cheesemill on 2012-04-07
[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

---

### Post by lykeion on 2012-04-07
[https://help.ubuntu.com/community/Java#JDK_or_JRE](https://help.ubuntu.com/community/Java#JDK_or_JRE)

---

### Post by sammiev on 2012-04-07
This is the way I keep the latest version of [Oracle Java]("http://sites.google.com/site/easylinuxtipsproject/java") on my OS.

---

### Post by webusr1 on 2012-04-07
Got it. I'll try one tonight and mark the thread solved when it works.

Thanks everyone!

This forum rocks!:guitar:

---

### Post by rpaco on 2012-04-07
> **sammiev said:**
> This is the way I keep the latest version of [Oracle Java]("http://sites.google.com/site/easylinuxtipsproject/java") on my OS.

Unfortunately using that stopped Libre Office Base from working.

---

### Post by sammiev on 2012-04-07
> **rpaco said:**
> Unfortunately using that stopped Libre Office Base from working.


Just tried it here and I have no issues running Libre Office Base.

---

### Post by webusr1 on 2012-04-14
Done, I'm good. Java 6 WebBrowser JRE Plugin now works in Ubuntu 10.04.

Reviewed two web sites:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
[http://www.duinsoft.nl/packages.php?t=en#hand](http://www.duinsoft.nl/packages.php?t=en#hand)


[SIZE=3][COLOR=#000000]Removed  the [COLOR=#0000FF]IcedTea Java-plug-in[/COLOR] using Synaptic and ran the following:
[/COLOR][/SIZE]
[LIST]
[*]EDIT sources.lists put the line
deb [http://www.duinsoft.nl/pkg](http://www.duinsoft.nl/pkg) debs all
in the file /etc/apt/sources.list, either using Software Sources from  your System Menu or by editing the file in an editor (as root)
or:
put this line in a file named (e.g.) duinsoft.list in the directory /etc/apt/sources.list.d
[*]import the gpg key with the command (all on one line)
sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 5CB26B26
[*]enter the commands (two lines)
sudo apt-get update
sudo apt-get install update-sun-jre
[/LIST]

---

