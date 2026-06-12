---
title: "broken dependencies"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by Tikhon03 on 2010-03-29
I was trying to setup gogui to work on kubuntu, using instructions found on an ubuntu forum: [http://ubuntuforums.org/showthread.php?t=749811](http://ubuntuforums.org/showthread.php?t=749811).  I did not even have Java installed yet, so I first tried installing some of the sun-java6 packages.  Usually kpackage is good at picking dependent packages and installing them also, but apparently not this time.  Next time I tried using kpackage, I was not able to do anything.  It gave me a message saying I had broken dependencies, and should use synaptic or aptitude.  I do not even have these installed!  I think that un-installing the Java software and starting over should do the trick, but I'm not sure how to do this from the command line.  Also the instructions in the link above never worked for me.

---

### Post by zvacet on 2010-03-30
You can try with 

```
sudo apt-get -f install
```

---

### Post by Tikhon03 on 2010-04-03
thank you zvacet.  Actually I did a little more than that.  I found the sun-java6 package that was installed using
```
sudo dpkg -l
```
uninstalled it with
```
sudo apt-get uninstall [package]
```
then reinstalled the appropriate sun-java6 packages with apt-get rather than kpackage.  This is proprietary software, and there is a user agreement that has to be "signed" by clicking ok. Apparently kpackage can't handle this, which  is why it has to be done with apt-get instead.  Once the java packages were correctly installed, the instructions for setting up gogui worked! Now I am a happy camper :D.

---

