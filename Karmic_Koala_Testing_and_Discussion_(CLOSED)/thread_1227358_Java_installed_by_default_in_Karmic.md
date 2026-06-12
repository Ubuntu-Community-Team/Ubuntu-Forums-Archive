---
title: "Java installed by default in Karmic?"
date: 2009-07-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-07-30
Folks can you confirm that or have I installed it without having noticed as a dependency to other app?

ps: to check type "java -version" in terminal.

---

### Post by wayne_cat on 2009-07-30
> **froggyswamp said:**
> Folks can you confirm that or have I installed it without having noticed as a dependency to other app?

ps: to check type "java -version" in terminal.

not sure if it is a default application in Alpha 3. 

Alpha 1 & 2 came without java ... I had to install it:

```
oot@macbook:~# dpkg -l |grep java
ii  java-common                                    0.30ubuntu5                               Base of all Java packages
ii  sun-java6-bin                                  6-14-1                                    Sun Java(TM) Runtime Environment (JRE) 6 (architecture 
ii  sun-java6-jre                                  6-14-1                                    Sun Java(TM) Runtime Environment (JRE) 6 (architecture 
root@macbook:~# 
```
```
root@macbook:~# java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)
root@macbook:~# 
```

---

### Post by dinxter on 2009-07-30
no java on cd alpha 3 as far as i can see. i would have been a little surprised to be honest
[http://cdimage.ubuntu.com/releases/karmic/alpha-3/source/karmic-src-1.list](http://cdimage.ubuntu.com/releases/karmic/alpha-3/source/karmic-src-1.list)

---

