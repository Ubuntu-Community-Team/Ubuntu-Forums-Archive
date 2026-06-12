---
title: "New update removed Java"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cl333r on 2009-03-30
Yesterday I installed the daily build of Jaunty and today after I checked for updates it proposed to do a partial update and also to remove Java. As it turns out the package sun-java6-jre is no more "installable". Does anyone know what's the matter?

I'm running the 64 bit version.

---

### Post by Reiger on 2009-03-30
Yes. Recently SUN pushed out the Java 6 update 13; and the JRE currently in the repo's is of this same version. However, for some reason none of the JRE dependencies were updated accordingly. So you should 'hold' onto update 12 for the meantime.

---

### Post by go7Ul1ai on 2009-03-30
I don't know, all I do know is that most of the time Partial Updates are bad as during the development phase, can remove important packages.

---

### Post by cl333r on 2009-03-30
Alright, thanks, then waiting for the dependencies to get normalized. I'm pretty sure this is a bold issue and the developers are aware so ain't gonna file a bug report.

---

### Post by uBeer on 2009-03-30
I just let it remove those packages and instead installed openjdk :popcorn:

---

### Post by zika on 2009-03-30
> **uBeer said:**
> I just let it remove those packages and instead installed openjdk :popcorn:
from pure curiosity:
what is the real difference between sun-java6-{bin,jdk,jre} and openjdk...? 

does it use IcedTea?
(I think I had bad experience wth IcedTea but that might be because it was 32-bit then)

is it 64-bit aware...?
(I use sun-java6 solely for JGR (Java GUI for R), for plugin I have newer (developmet) version in different direcory)

---

### Post by DougieFresh4U on 2009-03-30
Just ran updates via terminal and all java updates installed with out a problem.

---

### Post by cl333r on 2009-03-30
It's because all Java updates are already in the repos.

---

### Post by philinux on 2009-03-30
> **cl333r said:**
> Yesterday I installed the daily build of Jaunty and today after I checked for updates it proposed to do a partial update and also to remove Java. As it turns out the package sun-java6-jre is no more "installable". Does anyone know what's the matter?

I'm running the 64 bit version.

In future, never do a partial update, click cancel and update the others. Then check via synaptic.

---

### Post by uBeer on 2009-03-30
> **zika said:**
> from pure curiosity:
what is the real difference between sun-java6-{bin,jdk,jre} and openjdk...? 

does it use IcedTea?
(I think I had bad experience wth IcedTea but that might be because it was 32-bit then)

is it 64-bit aware...?
(I use sun-java6 solely for JGR (Java GUI for R), for plugin I have newer (developmet) version in different direcory)

Yes, I believe it uses IcedTea. It's the open source implementation of the commercial version. And if I'm not mistaken it is 64-bit aware.

Here's some more information: [http://www.sun.com/software/opensource/java/faq.jsp#b](http://www.sun.com/software/opensource/java/faq.jsp#b)

---

### Post by mhenriday on 2009-03-31
When I updated from **Intrepid** to the **Jaunty** beta, the **Java** files were uninstalled, but they remain in the multiverse repositories (now updated to version 6-13-1). A simple way to re-install them is to open **Synaptic**, perform a search for «sun java», and scroll down to the relevant files and install them....

Henri

---

