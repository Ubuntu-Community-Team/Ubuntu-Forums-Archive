---
title: "Insalled Eclipse before JDK now wont run"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by drubin on 2008-03-09
Hi i installed Eclipse before i installed the JDK (maybe it was silly).  But now when i run eclipse it says. 

I also then installed JDK by this tutorial 
[http://www.evolutionnext.com/blog/2006/06/27/1151429024151.html](http://www.evolutionnext.com/blog/2006/06/27/1151429024151.html) 

I could not find  JDK1.6 in the repositories. (I changed the version, as it is out of beta now) 

```
apps$ eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...not found
  testing /usr/lib/jvm/java-1.5.0-sun...not found
  testing /usr/lib/j2se/1.5...not found
  testing /usr/lib/j2se/1.4...not found
  testing /usr/lib/j2sdk1.5-ibm...not found
  testing /usr/lib/j2sdk1.4-ibm...not found
  testing /usr/lib/j2sdk1.6-sun...not found
  testing /usr/lib/j2sdk1.5-sun...not found
  testing /usr/lib/j2sdk1.4-sun...not found
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch

Any help /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension
rubin@gizmo:~/apps$ sudo eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...not found
  testing /usr/lib/jvm/java-1.5.0-sun...not found
  testing /usr/lib/j2se/1.5...not found
  testing /usr/lib/j2se/1.4...not found
  testing /usr/lib/j2sdk1.5-ibm...not found
  testing /usr/lib/j2sdk1.4-ibm...not found
  testing /usr/lib/j2sdk1.6-sun...not found
  testing /usr/lib/j2sdk1.5-sun...not found
  testing /usr/lib/j2sdk1.4-sun...not found

```

Is there a way to solve this with out re-downloading and re-installing eclipse?

---

