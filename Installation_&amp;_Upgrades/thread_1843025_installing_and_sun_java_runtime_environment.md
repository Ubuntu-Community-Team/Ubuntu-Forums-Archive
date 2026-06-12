---
title: "installing and sun java runtime environment"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by laurieturpin on 2011-09-12
Hello 

I'm running unbuntu 11.04 and I'm trying to install the sun java runtime enviroment.

What I have done so far is:

I have gone into the Ubuntu Software Centre and
Then selected other software
Then added ppa:ferramroberto/java
This then gave me an option to install the java runtime enviroment
Acccording to the Ubuntu Software Centre it all installed ok

The problem is though when I try to use a java application in my web browser(Chrome) it tells me the java pluggin is missing!!!

How can I get java jre to run in Chrome?

Thanking you in anticipation.:)

---

### Post by Toz on 2011-09-12
Make sure that you've also installed the sun-java6-plugin package.

Reference Link: [http://www.webupd8.org/2011/03/install-java-in-ubuntu-1104-natty.html]("http://www.webupd8.org/2011/03/install-java-in-ubuntu-1104-natty.html")

---

### Post by laurieturpin on 2011-09-13
Thank you Toz

A message came back that not all of it is there, but it seems to run browser.:)

---

### Post by TBABill on 2011-09-13
That was a very old article. The proper way would be to enable the partner repo in your software sources list and then mark sun java for installation, then apply. I believe if you just mark the plugin it'll pull in the rest as dependencies.

---

### Post by laurieturpin on 2011-10-02
The problem seemed to resolve itself after I updated.
Java runtime now works fine.
Thanks for you help everyone:P

---

