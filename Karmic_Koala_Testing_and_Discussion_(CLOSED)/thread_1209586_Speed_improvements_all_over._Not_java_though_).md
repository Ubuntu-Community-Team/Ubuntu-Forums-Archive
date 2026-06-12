---
title: "Speed improvements all over. Not java though :)"
date: 2009-07-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-07-10
Limewire still loads like a ******* and java uses a whopping 223 megs. Not even ext4 and noatime can help him. It'll get better at some point, i believe...

---

### Post by Joe_Bishop on 2009-07-10
It's java, jit, etc.

---

### Post by wayne_cat on 2009-07-10
A proprietary java application ... :rolleyes:

---

### Post by Regenweald on 2009-07-10
> **wayne_cat said:**
> A proprietary java application ... :rolleyes:

Not only that, but a free app that suits my needs.Show me the best free option, and I'll show you an app that i use :)
The resource hogginess i can live with......Point me too a good FOSS alternative and the Lime is out! :P

---

### Post by Hairy_Palms on 2009-07-10
[http://www.frostwire.com/](http://www.frostwire.com/)

its not exactly light, but it doesnt seem to use 223 megs of ram.

---

### Post by Arup on 2009-07-10
Try and use the latest Java 1.6.0_14

---

### Post by Regenweald on 2009-07-10
> **Hairy_Palms said:**
> [http://www.frostwire.com/](http://www.frostwire.com/)

its not exactly light, but it doesnt seem to use 223 megs of ram.

You know, frostwire always gives me connection problems, posted a howto on it last year when i got it to work.

> **Arup said:**
> Try and use the latest Java 1.6.0_14

I have 6-14-1 from the Karmic repos, same thing ?

---

### Post by wayne_cat on 2009-07-10
> **Regenweald said:**
> 
I have 6-14-1 from the Karmic repos, same thing ?


yes

```
root@macbook:/opt/fs_testing# dpkg -l |grep java
ii  java-common                                    0.30ubuntu5                                Base of all Java packages
ii  sun-java6-bin                                  6-14-1                                     Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-jre                                  6-14-1                                     Sun Java(TM) Runtime Environment (JRE) 6 (ar

``````
root@macbook:/opt/fs_testing# java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)

```

---

### Post by Regenweald on 2009-07-10
> **wayne_cat said:**
> yes



Then I can live with it. may see improvements as the cycle progresses. I have 2 gigs of memory anyway, so my system is not exactly under strain.

---

### Post by wayne_cat on 2009-07-10
you could set lower memory limits (Xmx) in:


/usr/lib/LimeWire/runLime.sh

(almost at the end of the script)

```
${JAVA_PROGRAM_DIR}java -Xms64m -Xmx256m ...

```Not every java application likes that ... not sure if Limwire is still usable and "fast" with less than 256 mb maximum size

---

