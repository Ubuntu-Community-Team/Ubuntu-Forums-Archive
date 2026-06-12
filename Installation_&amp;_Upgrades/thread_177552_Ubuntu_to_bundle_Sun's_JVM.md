---
title: "Ubuntu to bundle Sun's JVM?"
date: 2006-05-16
forum: Installation &amp; Upgrades
---

### Post by dirkoneill on 2006-05-16
According to this cnet article, 
[http://news.com.com/Sun+to+make+Java+more+Linux-friendly/2100-7344_3-6068852.html?tag=nl]("http://news.com.com/Sun+to+make+Java+more+Linux-friendly/2100-7344_3-6068852.html?tag=nl"), Sun is changing the java licensing to be more friendly to linux. If I am reading this correctly, then this means that Ubuntu can come with the Sun JVM pre-installed. I certainly hope that this is true. If they make the announcement next week or whenever JavaOne takes place, how long do you think we will have to wait until we are an apt-get away from a proper java install?

---

### Post by dabear on 2006-05-16
[QUOTE=dirkoneill]According to this cnet article, 
[http://news.com.com/Sun+to+make+Java+more+Linux-friendly/2100-7344_3-6068852.html?tag=nl]("http://news.com.com/Sun+to+make+Java+more+Linux-friendly/2100-7344_3-6068852.html?tag=nl"), Sun is changing the java licensing to be more friendly to linux. If I am reading this correctly, then this means that Ubuntu can come with the Sun JVM pre-installed. I certainly hope that this is true. If they make the announcement next week or whenever JavaOne takes place, how long do you think we will have to wait until we are an apt-get away from a proper java install?[/QUOTE]
Not preinstalled, but java recently hit the multiverse repositories. If you have those installed, you could just use synaptic/aptitude install sun-java

edit; at least if you have dapper drake

---

### Post by thirdmusketeer on 2006-05-16
Could anybody tell me how to get sun-java5. I am a 3 day old Ubuntu user, so bear with.

I have been trying to use the regular method of using java-package and fakeroot to convert but that wasn't successful, so this is great news for me.

I checked through Synaptic Package Manager > Development (Multiverse) > and could only find jdk1.4 and jre1.4, and I tried doing
sudo apt-get install sun-java5 but that didn't work either.

How do I make sure my multiverse is activated, I did the steps required in the Help but am not sure if it is activated or not.

Thanks

(I am using Ubuntu 5.10 , I presume this is known as Dapper Drake)

---

### Post by thirdmusketeer on 2006-05-16
Could anybody tell me how to get sun-java5. I am a 3 day old Ubuntu user, so bear with.

I have been trying to use the regular method of using java-package and fakeroot to convert but that wasn't successful, so this is great news for me.

I checked through Synaptic Package Manager > Development (Multiverse) > and could only find jdk1.4 and jre1.4, and I tried doing
sudo apt-get install sun-java5 but that didn't work either.

How do I make sure my multiverse is activated, I did the steps required in the Help but am not sure if it is activated or not.

Thanks

(I am using Ubuntu 5.10 , I presume this is known as Dapper Drake)

---

### Post by thirdmusketeer on 2006-05-16
Could anybody tell me how to get sun-java5. I am a 3 day old Ubuntu user, so bear with.

I have been trying to use the regular method of using java-package and fakeroot to convert but that wasn't successful, so this is great news for me.

I checked through Synaptic Package Manager > Development (Multiverse) > and could only find jdk1.4 and jre1.4, and I tried doing
sudo apt-get install sun-java5 but that didn't work either.

How do I make sure my multiverse is activated, I did the steps required in the Help but am not sure if it is activated or not.

Thanks

(I just installed Ubuntu 5.10, I think that is known as Dapper Drake)

---

### Post by NoUse on 2006-05-16
5.10 is Breezy.  Dapper will be released in June and has the version number of 6.06.

sun-java5 is in the Dapper repos not in Breezy.

---

