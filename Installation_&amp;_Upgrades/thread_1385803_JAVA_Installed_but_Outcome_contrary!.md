---
title: "JAVA Installed but Outcome contrary!"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2010-01-20
Hi Folks!:popcorn:

Please refer to the attached Screenshots & help me decipher on **WHY the JAVA is still not getting detected on my System?**

Pingtest.net claims contrary(for both Firefox & Chrome Browsers) whereas **"Installed Packages"(Synaptic Manager) points as JAVA & plugins being definitely installed!?**

Where's the Catch in all this????;)

---

### Post by user1397 on 2010-01-20
have you tried simply reinstalling it and restarting firefox?

---

### Post by kostkon on 2010-01-20
If have also installed the package
```
sun-java6-plugin
```
then, in order to make Firefox (and Chrome, I assume) use the Sun Java, you'll need to give this command in the terminal
```
sudo update-java-alternatives -s java-6-sun
```
(you'll need to restart your browsers after giving this command)

This command will also set the Sun Java as the default JVM in your system.

Hope that helps.

---

### Post by Saurabhdua on 2010-01-20
Thanks Kostkon!

In fact, I never installed sun-java6-"plugin"(as the same was never told to me!).Now that I have installed, both Chrome & FF are not posing any issue!

**_One Thing:::_**Refer to the 2nd Screenshot again, please...I couldn't find "UBUNTU" Icon besides -bin & -jre enteries? Same is there with java-common.What does the "Ubuntu" icon besides indicates? & were these all required to be installed to rectify the issue posted in this Forum?

---

