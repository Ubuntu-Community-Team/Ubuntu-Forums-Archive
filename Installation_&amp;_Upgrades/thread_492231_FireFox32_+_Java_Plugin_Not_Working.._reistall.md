---
title: "FireFox32 + Java Plugin Not Working.. reistall?"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by mbuntu on 2007-07-04
Hi there..

Just made the best decision to switch from Vista to Ubuntu.. I just couldn´t take being told ¨You do not have permission to do that¨ anymore.

Anyway, I am getting stuck on one thing that has led to many..

First, I am using Feisty Fawn 7.04 on an Amd64 Setup.

I use a web-based vpn tool setup by my employer to allow me to work from home. It worked in both IE and FireFox when I had Vista installed... But it doesn´t work in my current Ubuntu with FireFox setup. I know the tool requires Java. I found that the version of FireFox that comes with my installation doesn´t have the java plugin..

After some reasearch I found that I needed to download FireFox32 and did so using the automated script found at [http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

It still didn´t work properly. The vpn page tells me that I still need the java plugin.

I then found the documentation located at [https://help.ubuntu.com/community/FirefoxAMD64FlashJava](https://help.ubuntu.com/community/FirefoxAMD64FlashJava)
. I followed the directions but get told that FireFox32 already exsits..

There is a point at the top of the page that tell me to ¨Execute /usr/local/java32/bin/ControlPanel¨ however there is no java32 folder in the ¨local¨ directory.

So i figure I need to uninstall FireFox32 and re-install it using the guide at the second link above.. But I have no idea how to uninstall it.. or if I even have the right idea. I tried to delete the ¨firefox32¨ directory and got told that I don´t have permission to do that.. which is why I left vista.

I appreciate your help.

Thanks!

---

### Post by mattyrigby00 on 2007-07-04
i had that problem except i just didnt get any sound - i just switched to 32bit.

---

### Post by mbuntu on 2007-07-04
I already have the 32 bit version of FireFox.. but the Java plugin isn´t working..

I guess my question is.. how do I unistall it?

---

### Post by mbuntu on 2007-07-04
Nevermind..! I figured it out..

sudo apt-get --purge firefox32

and

sudo aptitude purge firefox32

seemed to work.

Thanks.. I will now try and manually re-install it.

---

