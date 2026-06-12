---
title: "Updating Java in Dapper Drake"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by jibril on 2006-11-18
Hi guys,
   I have been trying to update the version of java in Dapper from 1.4 to 5.0      
   from some time but it simply does not. 

   Could someone please tell me how to do that ?

   Thanks a Lot

   jibril

---

### Post by mgmiller on 2006-11-18
The easiest way would be to use easyubuntu [http://easyubuntu.freecontrib.org/]("http://easyubuntu.freecontrib.org/")      

or automatix2  [http://www.getautomatix.com/]("http://www.getautomatix.com/")  



Just select the sun java install and it does the rest.

There is one other possibility.  You may have managed to install the version you want, but are simply not using it.  Enter the following code in a terminal:
```
sudo update-alternatives --config java
```

This will run a little app that will list all the different java's installed on your system and allow you to select the one you want to use.  It's pretty intuitive once you run it.

---

### Post by jibril on 2006-11-18
This is what I get when I do the update-alternatives.

```

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
      2        /usr/lib/jvm/java-gcj/jre/bin/java
 +    3        /usr/lib/j2se/1.4/bin/java
*     4        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

```

I choose 4 and then I type 
```

$java -version

java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

```

But still it is not working. I am not sure how to prove it but I was writing java code which uses things like JCF's which wont work at home but does at uni where I <em>know</em> that java 1.5/5.0 is installed.

jibril

---

### Post by jibril on 2006-11-18
Anyone?

---

### Post by peebly on 2006-11-18
Not sure about dapper drake, but sun java version 5 shows up in Ubuntu's own add/remove applications in edgy.

Just tick the box and apply.

---

