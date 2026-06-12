---
title: "trying to install kazam... Broken :("
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by Reduced_Oxygen on 2011-04-27
```
gilligan@Gilligan-Desktop:~$ sudo apt-get install kazamReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kazam : Depends: libx264-85 but it is not installable or
                  libx264-98 but it is not installable
         Depends: libmatroska0 but it is not installable or
                  libmatroska2 but it is not installable
E: Broken packages

```

---

### Post by sanguinoso on 2011-04-27
I'm not familiar with that particular piece of software but the error means that it depends on the packages that are listed but apt-get cannot find them in the repositories. This is a problem with whatever repository you were attempting to install kazam from.

---

### Post by Reduced_Oxygen on 2011-04-27
im using the repository recommended by launchpad

---

### Post by dino99 on 2011-04-27
this might help:

[http://www.flopex.org/?p=143](http://www.flopex.org/?p=143)

---

### Post by Reduced_Oxygen on 2011-04-27
> **dino99 said:**
> this might help:

[http://www.flopex.org/?p=143](http://www.flopex.org/?p=143)
thanks heaps this worked

---

