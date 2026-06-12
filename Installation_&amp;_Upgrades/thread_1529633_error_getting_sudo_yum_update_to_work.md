---
title: "error getting sudo yum update to work"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by bbuy2k on 2010-07-12
I'm having a problem with this command: sudo yum update
I get the error: "Loaded plugins: presto refresh - packagekit
error:no such table: packages.

I created a group using vi /etc/sudoers
saved it using :wq!

but can't get it to work, please help.


Thanks in advance
-bbuy2k

---

### Post by duanedesign on 2010-07-14
You can install the red hat package manager and yum on ubuntu to use RPM-repositories. This will bypass the debian packaging system, i would recommend not doing this.
When in need of RPM's on Ubuntu use alien ([https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)).

That being said here is a thread on the Fedora forums that discusses your issue.
[http://fedoraforum.org/forum/showthread.php?p=1343905]("http://fedoraforum.org/forum/showthread.php?p=1343905")

thank you,
duanedesign

---

### Post by thahir1986 on 2010-07-14
for my knowledge i had used the yum 

```
sudo yum update
```

in fedora rpm linux..for debian, ubuntu linux

```
sudo apt-get update
```


i don't know is it possible to use yum within ubuntu....may be!!!!:-({|=

---

### Post by bbuy2k on 2010-07-18
Thank you very much to thahir1986 and [[COLOR=#D40000]**duanedesign **[/COLOR]]("http://ubuntuforums.org/member.php?u=686748")
I'll check it out and post back once I get it to work based on you guys recommendation.

Thank you again
-bbuy2k
[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=686748")

---

