---
title: "Can't get Eclipse Process Framwork (EPF) to run"
date: 2012-06-30
forum: Installation &amp; Upgrades
---

### Post by fballem on 2012-06-30
Hi,

I am trying to get the Eclipse Process Framework (EPF) to run on my ubuntu system.

Information about EPF is found here: [http://www.eclipse.org/epf/](http://www.eclipse.org/epf/)

There are files that are identified for Linux, but they appear to be 32-bit and need 32-bit Java. I am running 64-bit ubuntu (12.04) and 64-bit oracle java 1.7. I prefer Linux, but I might have to go back to Windows if I can't get this to work.

I went back to Windows - briefly - and I was able to install the Windows version and get it to execute. In Windows, I am running Windows 7 Professional, but using 32-bit Oracle Java 7.

When I start the application in ubuntu, I get a java error 13, which seems to indicate the wrong Java version.

If anyone has managed to get EPF working in Ubuntu, I would be very grateful if they could share how.

Thanks,

Any suggestions would be very much appreciated.

---

### Post by johnesmiller on 2012-11-21
Did you ever manage to get EPF to run on Ubuntu!?  I am having the same problem!

---

### Post by zuernBernhard on 2012-12-17
same problem here on 12.10 64 bit

---

### Post by fballem on 2013-05-25
Just an update to this post. As far as I know, there are 32-bit specific requirements, primarily in how EPF handles windows. When installing on Windows 7 64-bit, 32-bit Java and 32-bit browser are used, which is why EPF will work in that environment. In Ubuntu 64-bit, 64-bit Java and 64-bit browser is used, so EPF will not work there. The code would have to be ported, which is way beyond my capability.

I would love to have a solution, but at the moment, there does not appear to be one.

---

