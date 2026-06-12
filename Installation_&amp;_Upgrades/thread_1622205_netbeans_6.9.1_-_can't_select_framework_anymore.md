---
title: "netbeans 6.9.1 - can't select framework anymore"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by dgoosens on 2010-11-15
hi Ubunteros !!

I have been using Ubuntu and Netbeans for quite a while now... and never had any real issues...
But since a couple of days, I encounter this very strange bug...

It has become impossible for me to select a Framework when creating a new project. Everything works, I just can not check the checkbox...

This checkbox issue happens in other parts of Netbeans as well...

I am pretty sure this is due to some updated Java package... but it seems rather difficult to me to figure out where to start looking.

Using Ubuntu 10.04 (64-bit)
Netbeans 6.9.1
JDK openjdk-6-jdk

So I wondered if any of you are encountering the same trouble... and if so, if you figured out a way to make it work as it used to.

By the way, it seems the same issue occurs on Ubuntu 10.10 as stated here:
[http://forums.netbeans.org/topic32876.html](http://forums.netbeans.org/topic32876.html)

Other interesting readings:
[http://stackoverflow.com/questions/4089036/cannot-select-framework-to-use-in-new-web-application-using-netbeans-on-ubuntu/4184669#4184669](http://stackoverflow.com/questions/4089036/cannot-select-framework-to-use-in-new-web-application-using-netbeans-on-ubuntu/4184669#4184669)

[http://netbeans.org/bugzilla/show_bug.cgi?id=191959](http://netbeans.org/bugzilla/show_bug.cgi?id=191959)

Thanks a lot in advance,

---

### Post by dgoosens on 2010-11-15
I found a solution...
if others have this same problem...
I wrote down the solution here:
[http://netbeans.org/bugzilla/show_bug.cgi?id=191959](http://netbeans.org/bugzilla/show_bug.cgi?id=191959)

1. install sun-java
      sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
      sudo apt-get update
      sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

2. gksudo gedit /usr/local/netbeans-6.9.1/etc/netbeans.conf
      set netbeans_jdkhome="/usr/lib/jvm/java-6-sun"
      (check your paths !)

3. save, close and start Netbeans...

---

### Post by s.v.z on 2010-12-08
About check paths.. I`ve just spent a lot of time, trying to figure out that NetBeans needs tools.jar and dt.jar to start all the modules. Just copied the lib folder from default-jdk to sun-6-jdk. 
Maybe this will save someone`s time..

---

### Post by atti84it on 2010-12-19
Is there any way to solve the problem **without** using Sun Java??

---

### Post by amogh.talpallikar on 2011-01-07
Thanks man... that really worked!

---

