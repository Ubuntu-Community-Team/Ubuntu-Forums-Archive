---
title: "how to upgrade to jre-6u29-linux-i586-rpm.bin?"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by rks99 on 2011-11-15
So I've downloaded the file: jre-6u29-linux-i586-rpm.bin
[http://www.java.com/en/download/help/linux_install.xml#rpm](http://www.java.com/en/download/help/linux_install.xml#rpm)
^these instructions are like rocket science to me...

I'm trying to update sun java to the latest update: 29. The automatic update in Synaptic only update to 26.

In this situation, I am to manually install this file to update to 29. 

As a new user of Linux, this seems impossible?

Would anyone know how to do this? 


p.s. i'm doing this because i'm trying to make minecraft run better on my system. :guitar:

---

### Post by BillyBoa on 2011-11-15
You can install the Oracle/Sun java 6 through repositories


add this repositry to your system:

```
sudo add-apt-repository ppa:ferramroberto/java
```

then update

```
sudo apt-get update
```

and install java

```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

You can manually install java 7 from here

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

---

### Post by rks99 on 2011-11-15
thank you, i will test it out and let you know how it went :)

---

### Post by sammiev on 2011-11-15
> **rks99 said:**
> So I've downloaded the file: jre-6u29-linux-i586-rpm.bin
[http://www.java.com/en/download/help/linux_install.xml#rpm](http://www.java.com/en/download/help/linux_install.xml#rpm)
^these instructions are like rocket science to me...

I'm trying to update sun java to the latest update: 29. The automatic update in Synaptic only update to 26.

In this situation, I am to manually install this file to update to 29. 

As a new user of Linux, this seems impossible?

Would anyone know how to do this? 


p.s. i'm doing this because i'm trying to make minecraft run better on my system. :guitar:

Ubuntu doesn't use rpm files. You need the other i586 file. :)

---

### Post by rks99 on 2011-11-15
> **sammiev said:**
> Ubuntu doesn't use rpm files. You need the other i586 file. :)

jre-6u29-linux-i586.bin  



that's the one i got now, how do i install it?

---

### Post by rks99 on 2011-11-15
> **BillyBoa said:**
> You can install the Oracle/Sun java 6 through repositories


add this repositry to your system:

```
sudo add-apt-repository ppa:ferramroberto/java
```

then update

```
sudo apt-get update
```

and install java

```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

You can manually install java 7 from here

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)


i've inserted the commands u gave me, it went perfectly but Sun-Java is still Update 26, not the newer update 29, which i'm trying to upgrade to. i've got the other file, since i heard that Ubuntu (i'm using XFCE desktop environment) doesn't use RPM files. 

jre-6u29-linux-i586.bin  



that's the one i got now, how do i install it?

---

### Post by PRC09 on 2011-11-15
I have used this in the past...


[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by rks99 on 2011-11-16
> **PRC09 said:**
> I have used this in the past...


[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

THIS WORKED!!! So awesome, thank you so much, made my day! :guitar:

---

### Post by PRC09 on 2011-11-16
You  are welcome.

---

