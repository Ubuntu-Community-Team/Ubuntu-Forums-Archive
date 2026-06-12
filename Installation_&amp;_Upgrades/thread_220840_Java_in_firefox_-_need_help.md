---
title: "Java in firefox - need help"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by martinielsen on 2006-07-22
Hi there.

I'm a Linux and Ubuntu newbe and trying to get Firefox fully functional. I have just installed Flash support (that was easy) but Java installation must be for higher level users - well over my level though :)

I'm looking at the guide here:
[http://plugindoc.mozdev.org/linux.html#Java](http://plugindoc.mozdev.org/linux.html#Java)

But the "2. Make a symbolic link to libjavaplugin_oji.so in your Mozilla Plugins directory....." does not make any sense for me.

Do any of you know about some kind of setup guide for dummies with point to point explanation?

I know about "Automatrix", but i don't think i will learn anything if i use automated setup.

Martin

---

### Post by hw-tph on 2006-07-22
The easiest way to get Java working in Firefox (and in Ubuntu in general) is by grabbing the package in Multiverse called sun-java5-bin. This should generate the same result as if you downloaded the Java .bin package from Sun, packaged it using java-package and then installed the resulting .deb package...but installing sun-java5-bin should be a lot quicker. :)


Håkan

---

### Post by Wyrm_1972 on 2006-07-22
Never forget to check the  Wiki :)

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by ::Lagro on 2006-07-22
If you follow the instructions from here:
[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
you will instal very simple. You have there also the last java edition.

---

### Post by martinielsen on 2006-07-22
Thanks guys! I will try your suggestions! "hw-tph" where do you grab the package? What/where is "Multiverse"? I looked for a package in Synaptic Package Manager, but none there...

Martin

---

### Post by martinielsen on 2006-07-22
Ah - sorry "hw-tph". I found the answer in the Wiki ](*,)

---

### Post by martinielsen on 2006-07-22
I have installed the sun-java5-bin from Multiverse but the plugin will not run in Firefox. The Wiki guide just say "Install Java5" in the "Java on Mozilla Firefox" section. The path in System -> Preferences -> Sun Java 5.0 Plugin Control Panel -> Advanced -> Command to launch default browser is set to "/usr/bin/mozilla" as default. Could that be the problem? As this path does not exist. What would be the correct path/file?

---

### Post by martinielsen on 2006-07-22
Java is up and running smooth! I just grabbed the sun-java5-plugin along with the sun-java5-bin package.

Thanks for your help!!

---

### Post by hw-tph on 2006-07-24
martinielsen, glad to hear you got it going. I must admit I have never used the sun-java5-bin package so I did not know about the sun-java5-plugin package.

> **::Lagro said:**
> If you follow the instructions from here:
[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
you will instal very simple. You have there also the last java edition.

Yes, but it will not be identified by the package management system (other applications may require or suggest Java). Using java-package (make-jpkg) you create a .deb from the .bin file that Sun provides, giving you the latest available version of the Sun JRE/SDK and the package management system will know about it. You can also use the update-alternatives system to switch between various Java suppliers (gcj, blackdown, Sun, etc) and the plugin will be automatically installed. 


Håkan

---

### Post by martinielsen on 2006-07-24
Yes - i'm very grateful, Linux is becoming more interesting to use when things are working :mrgreen:

---

