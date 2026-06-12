---
title: "Upgrade java6 to java7"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by timmygman on 2012-04-05
Hi!
Im renting a dedicated server and need to know how to upgrade from java6 to java7. at the moment its running 64bit if that helps.

I tried looking on here but am lost and need help less time down would be good as i have rented out a few minecraft servs on the same box so dont want others upset with long downtime for updating it.

thanks for help!!

---

### Post by darkod on 2012-04-05
Are you talking about sun/oracle java or open java?

For open java from repositories you would need to wait for an update. Not sure if there is separate repository where you can get the latest version yourself.

For oracle, just download the JRE (or JDK) you want, unpack in a folder where you want it, and there was a command to update the java the system will use. So, the downloading and extraction is no downtime at all, and the reconfig should be fast too.

Setting the default java was something like:
sudo update-alternatives --config java

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by recluce on 2012-04-05
Detailed instructions on how to install Sun/Oracle Java can be found here:

[http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU)

In spite of the URL, this contains instructions for 32bit versions of Ubuntu as well. While these instructions are currently for Java 6 Update 31, they should be adaptable to Java 7.

Note 1: are you SURE that you want Java 7 at this point in time? It certainly has issues.

Note 2: if you run Sun/Oracle Java on your machine, you are very likely to have a version older than update 31 on your machine, since Ubuntu has removed Sun/Oracle Java from the repos. Lucid, for example, is stuck at update 26. This means that your machine has security vulnerabilities. Either switch to OpenJDK or follow the manual installation path above to update to version 31!

---

### Post by 2F4U on 2012-04-05
Instructions for both the open version and the Oracle version can also be found here:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by timmygman on 2012-04-07
> **recluce said:**
> Detailed instructions on how to install Sun/Oracle Java can be found here:

[http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU)

In spite of the URL, this contains instructions for 32bit versions of Ubuntu as well. While these instructions are currently for Java 6 Update 31, they should be adaptable to Java 7.

Note 1: are you SURE that you want Java 7 at this point in time? It certainly has issues.

Note 2: if you run Sun/Oracle Java on your machine, you are very likely to have a version older than update 31 on your machine, since Ubuntu has removed Sun/Oracle Java from the repos. Lucid, for example, is stuck at update 26. This means that your machine has security vulnerabilities. Either switch to OpenJDK or follow the manual installation path above to update to version 31!

This is what i did before to get it working from the start but now i need java7 for some mods to run on my server. when i try to download java7 i can't find any links to one that end with a .bin file like this guide does so now im stuck. 
also do you know what issues it has right now
thankyou

---

### Post by darkod on 2012-04-07
Why exactly do you need a .bin file? You can simply unpack where you want, and use the update-alternatives command as in my previous post to tell ubuntu to use that JDK.

In theory it should work.

---

### Post by timmygman on 2012-04-07
Thanks guess i need to sleep more sometimes it worked good thank you everyone

---

