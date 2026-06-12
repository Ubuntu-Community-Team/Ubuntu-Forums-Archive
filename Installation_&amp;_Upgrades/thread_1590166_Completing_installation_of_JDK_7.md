---
title: "Completing installation of JDK 7"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by Barbellion on 2010-10-07
I'm trying to install the current snapshot of JDK 7, and I've ended following [this]("http://codeslinger.posterous.com/how-to-install-java-7-on-ubuntu") excellent page 
and everything goes apart from the very last command 
sudo update-java-alternatives -s jdk1.7.0  which returns 
[I]
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: alternative /usr/lib/jvm/jdk1.7.0/jre/bin/java for java not registered, not setting.
update-alternatives: error: alternative /usr/lib/jvm/jdk1.7.0/jre/lib/jexec for jexec not registered, not setting.
update-alternatives: error: alternative /usr/lib/jvm/jdk1.7.0/jre/bin/keytool for keytool not registered, not setting.
update-alternatives: error: alternative /usr/lib/jvm/jdk1.7.0/jre/bin/orbd for orbd not registered, not setting.
update-alternatives: error: alternative /usr/lib/jvm/jdk1.7.0/jre/bin/pack200 for pack200 not registered, not setting.
update-alternatives: error: alternative /usr/lib/jvm/jdk1.7.0/jre/bin/rmid for rmid not registered, not setting.
update-alternatives: error: alternative /usr/lib/jvm/jdk1.7.0/jre/bin/rmiregistry for rmiregistry not registered, not setting.
update-alternatives: error: alternative /usr/lib/jvm/jdk1.7.0/jre/bin/servertool for servertool not registered, not setting.
update-alternatives: error: alternative /usr/lib/jvm/jdk1.7.0/jre/bin/tnameserv for tnameserv not registered, not setting.
update-alternatives: error: alternative /usr/lib/jvm/jdk1.7.0/jre/bin/unpack200 for unpack200 not registered, not setting.[/I]

Any help?

I'm new to ubuntu so please be gentle...

---

### Post by Barbellion on 2010-10-10
I'm running 10.04 Lucid Lynx,and my* "java -version*" returns


java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.1) (6b18-1.8.1-0ubuntu1)
OpenJDK 64-Bit Server VM (build 16.0-b13, mixed mode)


I am programming over the JDK7 Library and so want to use the Sun JDK 7 release, (doesn't seem to be an openJDK 7 yet...). I've got it installed and placed correctly I think, I just don't seem to be able to nominate it as the JDK of choice.

"sudo update-java-alternatives --list"  returns

java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun
jdk1.7.0 2 /usr/lib/jvm/jdk1.7.0
jdk1.7.0 2 /usr/lib/jvm/jdk1.7.0

so it's there in the right place, but then trying to set me jdk to the 1.7 returns the errors mentioned before.

Any help? I'm pretty stuck!

---

### Post by lykeion on 2010-10-10
First question: Why do you want to install JDK 7? If you're not a bleeding edge java developer you'll do fine with JDK 6. And if you're not a java deveoper at all you'll probably want JRE instead.

Next I'm gonna try following instructions from the link you gave, and see if I encounter any (similar) errors.

EDIT

And yes I did, the same errors as you were having. Maybe some wrong with the install_java7_alternatives script? I don't know, maybe you should ask the author of the blog, he seems to to have managed.

EDIT 2

Even though the update-java-alternatives command failed you can still develop with JDK 7. In your Java IDE just point to the install dir of JDK 7 as your project SDK.

---

### Post by Barbellion on 2010-10-11
I'm trying to use JDK 7 because I've learnt Java from the Sun tutorials, which uses the 7 library. I know I can use an earlier version and learn the commands, but don't really want to work backwards like that... Plus JDK7 has some really good simplifications, and I'd have to transcript the work I did pre-ubuntu (only switched a fortnight ago.) as I used JDK7 on Windows.

I've changed my SE in Eclipse (my IDE) to 1.7 but it still doesn't seem to be taking it on.

Thanks for you help though!

---

