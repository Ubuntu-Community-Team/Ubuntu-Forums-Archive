---
title: "How To Update Java openjdk-6-jre ?"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Legionz on 2010-05-02
Hello all !  :)

I would like to install SqlDeveloper , but when i install it , it tells me that my  version of  Java openjdk-6-jre is   just 1.6.0_0 and must be at least 1.6.0_04.

I looked for this problem at Google and other forums but i didn't found anything ...:(

I re-installed Java open-jdk but it's the same version : 1.6.0_0

My Ubuntu version is 9.10 Karmic Koala 

Java -version : 

> java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu3)
OpenJDK Server VM (build 14.0-b16, mixed modethx for your help

---

### Post by Legionz on 2010-05-02
up plz ):P

---

### Post by brawd on 2010-05-02
You need to enable the partner repositories.

Go to System
Admin
Software sources
Other software

Here enable the partners, because they are the ones that look after these files now.

Let it update and then get it from Synaptic.

regards,

brawd

---

### Post by Legionz on 2010-05-02
thx for your reply brawd

I enabled Partners repositories , then i reinstall openjdk .

This is what give a java -version command : 

> java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu3)
OpenJDK Server VM (build 14.0-b16, mixed mode                      So it's always the same version ...:/

Here is what i installed : 

[U][[IMG]http://img695.imageshack.us/img695/4602/capturegh.th.png[/IMG]](http://img695.imageshack.us/i/capturegh.png/)

[/U]

Uploaded with [ImageShack.us]("http://imageshack.us")

what can i do to have openjdk  1.6.0_04. ?

---

### Post by brawd on 2010-05-03
I'm so sorry legionz I miread the java package, I was thinking sun java. I can't help you with the open version. It does seem to be a problem and google-ing  doesn't help.

Maybe removing what you have already installed followed by a re-install might do it.

There is an (old) article here which might help

[http://dashb-build.cern.ch/build/nightly/doc/guides/common/html/dev/sqldeveloperAppendix.html](http://dashb-build.cern.ch/build/nightly/doc/guides/common/html/dev/sqldeveloperAppendix.html)

Once again sorry.

regards,

brawd.

---

### Post by Legionz on 2010-05-03
Don't be sorry man , this is great to help me :)

Article you linked seems to be usefull , i 'm gonna work this tonight 

thx for your help  :D

cya

---

### Post by abra1 on 2010-05-03
[SIZE=3]Maybe these could help:[/SIZE]

  	 	 	 	 	 	  [SIZE=3]**[http://sites.google.com/site/easylinuxtipsproject/java#TOC-Get-JRE](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Get-JRE)**[/SIZE]
                              [SIZE=3][/SIZE]
[SIZE=3]** [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)**[/SIZE]

---

