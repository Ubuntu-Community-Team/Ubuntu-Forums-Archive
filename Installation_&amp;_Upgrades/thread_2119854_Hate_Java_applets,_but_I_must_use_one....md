---
title: "Hate Java applets, but I must use one..."
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by ladasky on 2013-02-25
Java browser applets used to be all the rage.  But over the past few years, Java applets appear to be falling into disuse.  That's just as well, if you ask me.  Applets were always clumsy and crudely rendered in my experience.  I've gotten by without enabling Java in my various browsers for years, and I've even stopped looking for the Java option in the browser settings. 

Wouldn't you know it, I need data from a web site ([https://flowrepository.org/public_experiment_representations](https://flowrepository.org/public_experiment_representations)) which makes you perform the downloads through a Java applet.  I don't know why they set up the site that way.

My Ubuntu system has both Chromium and Firefox installed.  I've been looking through all the settings on both browsers and... I can't find the way to enable Java?  In either browser?

Am I missing something here?  I don't know whether to feel stupid.  This used to be an easy task.

Thanks for any help you can offer!

---

### Post by QIII on 2013-02-25
Do you have Java installed?

Please post the results of 

```
java -version
```

---

### Post by ladasky on 2013-02-25
> **QIII said:**
> Do you have Java installed?

Whoops!  Yes, I should have mentioned that I do have Java installed.  Here's the output of "java -version":

```

java version "1.6.0_27"
OpenJDK Runtime Environment (IcedTea6 1.12.3) (6b27-1.12.3-0ubuntu1~12.04)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)

```

I run a few local Java apps, just not applets.

---

### Post by QIII on 2013-02-25
There are a few considerations here.

Your OpenJDK is out of date and Version 6 is due to reach EOL soon.  So does Oracle Java 6.  You should upgrade to OpenJDK 7 or Oracle Java 7.

Some websites do not recognize OpenJDK as "Java".  For Oracle Java 7, OpenJDK 7 is the open source reference implementation.  That is, Oracle (a prime mover in OpenJDK) says that all implementations of Java 7 must comply with OpenJDK 7 -- including Oracle Java 7.  However, some developers do not understand this and when they check for Java they don't accept OpenJDK 7.  Or it may simply be that version 6 is not acceptable for security reasons.

OpenJDK 7 should work in most cases and I recommend that as the preferred package.  That would be your first try.  In that case, the web browser plugin is called "Iced Tea".

If the website does not recognize OpenJDK 7, then go to the Jave wiki in my signature, find "Oracle Java 7", "Command line methods" and "Using webupdate.org's strikingly simple method" to install Oracle Java 7.  That PPA is trustworthy and has the benefit of updating Oracle Java 7 automatically during your normal updates when Oracle issues new updates.

Also, whichever you choose, there are some serious security issues with the plugins.  Even though Firefox has made the browser plugins "Click to Play" as a precaution, you should still be careful.  I would disable the plugin most of the time and enable it only when you need to and only on trusted sites.

---

### Post by ladasky on 2013-02-25
Thanks for the leads, QIII, I will follow up.

> **QIII said:**
> Also, whichever you choose, there are some serious security issues with the plugins.  Even though Firefox has made the browser plugins "Click to Play" as a precaution, you should still be careful.  I would disable the plugin most of the time and enable it only when you need to and only on trusted sites.

I am aware of the recent news stories about Java applet security issues, and about the Oracle emergency patch.  At the time, I had no need for Java applets, so I merely watched.

I use Chromium 99% of the time.  Occasionally, I come across a site which is incompatible with Chromium (e.g., [http://mars.jpl.nasa.gov/explore/curiosity/](http://mars.jpl.nasa.gov/explore/curiosity/)).  On those rare occasions, I switch back to Firefox.  I'm thinking I'll enable Java applets in Firefox only, and keep them disabled in Chromium.

---

