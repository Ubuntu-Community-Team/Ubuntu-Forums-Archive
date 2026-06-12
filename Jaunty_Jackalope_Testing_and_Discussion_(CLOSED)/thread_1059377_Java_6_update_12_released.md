---
title: "Java 6 update 12 released"
date: 2009-02-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cl333r on 2009-02-03
I wonder whether this update makes it into Jaunty.
For the first time there's an official plugin for x64, however it's windows-only.
More details here:
[http://java.sun.com/javase/6/webnotes/6u12.html](http://java.sun.com/javase/6/webnotes/6u12.html)

however a lot of features a missing from x64..

UPDATE: This update also ships with a Linux plugin, so we're in, Sun probably forgot to mention that.

---

### Post by JohnJackson on 2009-02-03
Odd, the pre-release version for u12 supported 64-bit Linux browsers, I'm using it right now.

---

### Post by Cloud79 on 2009-02-04
The plugin is for linux 64bit also, not only windows. Running it now!

---

### Post by cl333r on 2009-02-04
> **Cloud79 said:**
> The plugin is for linux 64bit also, not only windows. Running it now!

That's odd, are they so sloppy that they forgot about Linux (and perhaps Solaris)? Even despite Linux being used seldom listing all supported OSes makes the product seem more mature, besides, people have been waiting for this for like 5 years.
I think there could be some bugs or regressions for Linux (or the quality doesn't meet their standards yet) so they decided to include the plugin into the Linux installer but not to support it officially (yet).

---

### Post by cl333r on 2009-02-04
Besides, Jaunty could be the first version of Ubuntu to support out of the box the Flash and Java plugins on x64, so those who say they don't use x64 desktop Linux (including me) because many things are not supported yet - it's time to recheck the facts.

---

### Post by jespdj on 2009-02-06
> **cl333r said:**
> For the first time there's an official plugin for x64, however it's windows-only.
As far as I know, the 64-bit browser plugin is available for Windows as well as Linux.

I know that the page you linked to says "This release supports the New Java Plugin and Java Webstart on AMD64 architecture, on Windows platforms", but [here it says](http://java.sun.com/javase/6/webnotes/install/system-configurations.html#deployment-footnotes):
> Deployment Footnotes

For Java Plug-in and Java Web Start on 64-bit Solaris systems, use the 32-bit JRE.
**For Java Plug-in and Java Web Start on 64-bit Windows and Linux systems, the 64-bit JRE is supported as of Java SE 6, Update 12.**

I've downloaded JDK 6u12 and there's indeed a libnpjp2.so included, which is the browser plug-in. I could not get it working myself on 64-bit Hardy, but several people are [saying](http://ubuntuforums.org/showthread.php?t=1058539) that they have it working successfully.

---

### Post by cl333r on 2009-02-06
> **jespdj said:**
> As far as I know, the 64-bit browser plugin is available for Windows as well as Linux.

I know that the page you linked to says "This release supports the New Java Plugin and Java Webstart on AMD64 architecture, on Windows platforms", but [here it says](http://java.sun.com/javase/6/webnotes/install/system-configurations.html#deployment-footnotes):


I've downloaded JDK 6u12 and there's indeed a libnpjp2.so included, which is the browser plug-in. I could not get it working myself on 64-bit Hardy, but several people are [saying](http://ubuntuforums.org/showthread.php?t=1058539) that they have it working successfully.

The later posts on this thread discussed the availability for Linux.
Perhaps I should edit my first post.

---

### Post by taavikko on 2009-02-06
From the changes-list 

> sun-java6 (6-12-0ubuntu1) jaunty; urgency=low

 * New upstream release. Closes: #508195, #507979.
   Release notes at [http://java.sun.com/javase/6/webnotes/ReleaseNotes.html](http://java.sun.com/javase/6/webnotes/ReleaseNotes.html).
 * Build the -plugin package on amd64. Closes: #508871.
 * Install desktop files for javaws and the plugin control panel on amd64.
 * Find the correct doc zip when installing the -doc package. LP: #85969.
   LP: #321863.

---

### Post by 123Mike on 2009-02-06
I'm not sure if this is new to update 12, but I've noticed that when I play with the java2d demo that comes with the jdk, and when I pick one of the animated tabs, and raise the animation speed, I'm seeing that both my cpu's are being loaded up pretty much equally. This might mean Java has got pretty good at utilizing multiple cpu's even though the demo code wasn't specifically written to use multiple cpu's....

Java rocks.

---

