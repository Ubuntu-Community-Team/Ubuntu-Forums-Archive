---
title: "Updating to Java 6 release 21"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by xtiano77 on 2010-07-27
I am trying to update my version of Java to version 6 update 21 (hope got the version right), but I seem to have a hitch on my get along. The reason for the update is because my Bank's web page needs to have at the very least version 6 update 10 in order for me to send some documents through their web site. I tried: [http://ubuntuforums.org/showthread.php?p=9167020](http://ubuntuforums.org/showthread.php?p=9167020), specifically, sudo update-alternatives --all, but it gave me a whole lot of options. I didn't know which to choose so I chose all the ones with the "*" mark which also had "auto" on the right side. Afterwards I tried rebooting the system and going back to the web site but when I clicked on the button, the browser shows "Applet started" at the bottom and nothing happens. Shortly after a pop-up window comes up with the following message:



A script on this page may be busy, or it may have stopped responding. You can stop the script now, or you can continue to see if the script will complete.

Script: [https://content.usaa.com/mcontent/static_assets/WSR_MASTER/javascript/yui/yahoo-dom-event/yahoo-dom-event-min.js?cacheid=3349818120:1](https://content.usaa.com/mcontent/static_assets/WSR_MASTER/javascript/yui/yahoo-dom-event/yahoo-dom-event-min.js?cacheid=3349818120:1)



After clicking on "continue" and waiting a few moments, the following message comes up:


Script: chrome://global/content/bindings/general.xml:0


I hope not to have messed up the Java version in my system. Thanks in advance for your help. Below are my computer specs:

HP Laptop
Release 10.04 (lucid)
Kernel Linux 2.6.32-24-generic
GNOME 2.30.2
Memory: 993.0 MiB
Processor 0: Intel(R) Core(TM) Duo CPU T2450 @ 2.00GHz
Processor 1: Intel(R) Core(TM) Duo CPU T2450 @ 2.00GHz

---

### Post by y0diggity on 2010-07-28
I'm getting the same thing, basically.
I can run a java-enable page once just fine, but if I try to re-run the same page, I get the errors. Same version of Linux, but my Java is 6 - 20. Browser is FF.

Any help?

---

### Post by lykeion on 2010-07-29
> **xtiano77 said:**
> I am trying to update my version of Java to version 6 update 21 (hope got the version right), but I seem to have a hitch on my get along. The reason for the update is because my Bank's web page needs to have at the very least version 6 update 10 in order for me to send some documents through their web site. I tried: [http://ubuntuforums.org/showthread.php?p=9167020](http://ubuntuforums.org/showthread.php?p=9167020), specifically, sudo update-alternatives --all, but it gave me a whole lot of options. I didn't know which to choose so I chose all the ones with the "*" mark which also had "auto" on the right side. Afterwards I tried rebooting the system and going back to the web site but when I clicked on the button, the browser shows "Applet started" at the bottom and nothing happens.

I wonder did you really install sun java? What is the output of this command:```
java -version
```
It should be something like:```
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)
```

Here are the steps to install sun java 6 jre and the plugin:
1. add the partner repository ```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid  partner"
```
2. refresh sources list```
sudo apt-get update
```
3. install packages```
sudo apt-get install sun-java6-jre sun-java6-plugin
```
4. set sun java as default```
sudo update-java-alternatives -s java-6-sun
```
5. check java version```
java -version
```

Steps 1-3 could also be done in gui (may be simpler if you've no experience with the terminal)
1-2. Applications > Ubuntu Software Center > Edit > Software Sources... > Other Software tab
If you don't this line already: **[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner**
Click Add and enter **deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner** in the APT line field
click Reload
3. In top-right search field enter: sun java 6
Select and install 
* Sun Java 6.0 Plugin
* Sun Java(TM) Runtime Environment (JRE) 6 (Architecture independant files)

---

### Post by xtiano77 on 2010-07-31
Lykeion,

Your instructions worked like a charm. You Sir are a gentleman and a scholar. Thanks.

---

