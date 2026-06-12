---
title: "Java.."
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by Hickler on 2007-08-03
I downloaded Frostwire and tried to run it from Terminal but it said that I needed Java 1.5.X . I went to the Java website but I'm a bit confused as to how to install it, I tried following the [instructions]("http://java.com/en/download/help/5000010500.xml#selfextracting") but when I enter "su" and type my password it says ```
seth@seth-laptop:~$ su
Password: 
su: Authentication failure
Sorry.

```
Does this mean I have the wrong password, also, will that version of Java work with Ubuntu? I didn't see Ubuntu on the platforms it works on... Thank you.

---

### Post by Damiel on 2007-08-03
Assuming you have Feisty... it should be easier to install Java [this way]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Java_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox").

Then run in a terminal
```

sudo update-java-alternatives -s java-6-sun

```

---

### Post by Hickler on 2007-08-03
Well it's working so far but it showed the end-user license agreement in Terminal and I have no idea how to agree... can anybody help?

---

### Post by ericesque on 2007-08-03
the easiest way to install the JRE is to search for Java in Add/Remove...

---

### Post by Hickler on 2007-08-03
When I tried to install it in Add/Remove an error occurs and it says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Hmm...

---

### Post by Seisen on 2007-08-03
> **Hickler said:**
> Well it's working so far but it showed the end-user license agreement in Terminal and I have no idea how to agree... can anybody help?

When the agreement comes up all you have to is hit the tab key and it should highlight Yes and hit enter. 

> When I tried to install it in Add/Remove an error occurs and it says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

Hmm...

Just run ```
sudo dpkg --configure -a 
``` in the terminal you probably killed the package manager when it was installing Java. If you do that sometimes you get that error.

---

### Post by Hickler on 2007-08-03
> **Damiel said:**
> Assuming you have Feisty... it should be easier to install Java [this way]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Java_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox").

Then run in a terminal
```

sudo update-java-alternatives -s java-6-sun

```

Thank you very much, this worked! Thanks to everyone else as well.

---

