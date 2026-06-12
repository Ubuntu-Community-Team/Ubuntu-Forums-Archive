---
title: "This java applet is maxing out my cpu. Anyone like to confirm?"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2010-04-19
Got the default icedtea plugin. Doesn't always start either. Have to refresh the page a few times before it will go.

[http://www.thinkbroadband.com/speedtest.html](http://www.thinkbroadband.com/speedtest.html)

Also it fails to load the result page.

I get this page not found instead of the results. Works ok on karmic
[http://www.thinkbroadband.com/speedtestcomplete.html_id=127167936880925821539](http://www.thinkbroadband.com/speedtestcomplete.html_id=127167936880925821539)

Have to end the java process to get cpu back to normal.

I'm wondering if it's a 64 bit issue or the applet or icedtea.

---

### Post by mculbertson on 2010-04-19
Does the same here as yours. CPU maxed out to 100%. I killed java it went back to normal. This is a 32 bit machine so I suspect that rules out the 64 bit. I ran a speed test here from Speakeasy which does not use Java and it was normal. Also I got the page not found as you did from your link. Hope this test helps you.

---

### Post by sdowney717 on 2010-04-19
same thing lucid 32 bit

---

### Post by linden940 on 2010-04-19
running a 64bit here....i could not get the icedtea plugin to work at all! so i had to use the java 

installed java java screen size is off...its much bigger than it should be...but usable...

---

### Post by MacUntu on 2010-04-19
Hm, my Opera is using Java from /usr/lib/jvm/java-1.6.0-openjdk/jre/lib/i386 and after a reload the applet works fine (x86).

---

### Post by linden940 on 2010-04-19
using sun java in firefox...

---

### Post by philinux on 2010-04-19
Thanks guys looks like the icedtea plugin is the culprit then.

I'll raise a bug.

---

### Post by linden940 on 2010-04-19
post it here so me (or others) can tag on it to show its affecting more than just one person

---

### Post by philinux on 2010-04-19
> **linden940 said:**
> post it here so me (or others) can tag on it to show its affecting more than just one person

[https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/551328](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/551328)

Found one already recently raised.

---

### Post by zengeos on 2010-04-19
Hate to me too, but me too!

Disabling the Icedtea applet in Mozilla seems to have corrected my CPU usage issue.

---

### Post by kahumba on 2010-04-19
Boy that applet looks older than .. it even uses the Mozaic L&f.

---

### Post by splicerr on 2010-04-19
No maxing out of the CPU here.  Just this.

> 
You have visited a page that contains an applet written with Java  technology. Please install the Java Runtime Environment before refreshing this page.

[LEFT][IMG]http://java.com/en/img/everywhere/getjava_sm.gif?cid=jdp[/IMG]
[/LEFT]
 Thanks, but no thanks. I can do just fine without Java.

---

### Post by philinux on 2010-04-19
> **kahumba said:**
> Boy that applet looks older than .. it even uses the Mozaic L&f.

I will send a message to the webmaster

---

