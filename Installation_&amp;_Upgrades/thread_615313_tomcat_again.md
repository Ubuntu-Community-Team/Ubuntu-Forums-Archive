---
title: "tomcat again"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by zabi_ulla on 2007-11-16
pls pls help me install tomcat on feisty...iam new to ubuntu..........

---

### Post by sgordon on 2007-11-18
I've put an answer in your main thread post,

[http://ubuntuforums.org/showthread.php?p=3794424](http://ubuntuforums.org/showthread.php?p=3794424)

  Si

---

### Post by Kadrus on 2007-11-18
Open terminal and type this:
```
sudo apt-get install tomcat5.5

```
and for  Java Servlet engine -- admin & manager web interfaces
type this in terminal 
```
sudo apt-get install tomcat5.5-admin

```
For  documentations and example web applications type this:
```
sudo apt-get install tomcat5.5-webapps

```

Hope that helped :)

---

### Post by sgordon on 2007-11-21
The short version from Kadrus. I like it :)

  Si

---

### Post by james_bandido on 2007-12-04
i have this error :
 
E: tomcat5.5: subprocess post-installation script returned error exit status 1
E: tomcat5.5-admin: dependency problems - leaving unconfigured
E: tomcat5.5-webapps: dependecny problems - leaving unconfigured
 
can someone please tell me what i did wrong and what i must do to correct this ? i'm just new and learning the ropes as i go along.
 
thank you in advance.

---

### Post by Kzin on 2007-12-28
> **james_bandido said:**
> i have this error :
 
E: tomcat5.5: subprocess post-installation script returned error exit status 1
E: tomcat5.5-admin: dependency problems - leaving unconfigured
E: tomcat5.5-webapps: dependecny problems - leaving unconfigured
 
can someone please tell me what i did wrong and what i must do to correct this ? i'm just new and learning the ropes as i go along.
 
thank you in advance.

Do you have more error detail?

---

