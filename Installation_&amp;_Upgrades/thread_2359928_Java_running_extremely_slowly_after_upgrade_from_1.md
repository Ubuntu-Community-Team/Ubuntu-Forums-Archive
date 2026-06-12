---
title: "Java running extremely slowly after upgrade from 16.10"
date: 2017-04-29
forum: Installation &amp; Upgrades
---

### Post by simon332 on 2017-04-29
I have an app running Java that uses nearly all the  CPU. Didn't happen on 16.10. I guess I was a bit trigger happy and I'm  looking for downgrade instructions now.

Doesn't use any more memory or anything. Earlier versions of Ubuntu  (like about 14.04) used to leak memory in Java but it seems this is CPU  related, not memory.

I have two PC both with dual boot. One is a ten year old macbook with  lubuntu 17.04 32 bit, 3gb ram and the lxde desktop. Other is a similar  age desktop (Compaq Presario 5085AN) with ubuntu 17.04 64 bit, 4gb ram  and in both cases the upgrade from 16.10 to 17.04 has been a major  downgrade.

Hope that's a bit more helpful. Non java apps seem fine so far, although all apps seem to be using a lot more "virt" in top.

---

### Post by mörgæs on 2017-04-30
Which version of Java are you using? Please run ```
java -version
``` and post the results.

---

### Post by simon332 on 2017-05-04
openjdk version "1.8.0_121"
OpenJDK Runtime Environment (build 1.8.0_121-8u121-b13-4-b13)
OpenJDK Server VM (build 25.121-b13, mixed mode)


Not convinced it's confined to Java now though. Java's probably just the most hungry process on the system so it makes it the most visible. Perhaps I should have said "System running slowly". Runs ok for a while, then dies and needs a reboot.

---

### Post by mörgæs on 2017-05-05
If you run 17.04 in a live boot does the same happen? 

Java is probably not going to work in a live boot but you can try another heavy process.

---

### Post by simon332 on 2017-05-08
I've tried booting with a 4.8 kernel and it seems to resolve it or at least so far, so good.

---

### Post by mörgæs on 2017-05-09
Good that you at least have a temporary solution. 

When you some day are going for the next release I suggest a fresh install, not another upgrade.

---

