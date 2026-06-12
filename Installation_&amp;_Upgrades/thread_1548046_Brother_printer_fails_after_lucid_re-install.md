---
title: "Brother printer fails after lucid re-install"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by skewray on 2010-08-07
I recently re-installed lucid on a computer which had a working ethernet printer queue, to a Brother MFC-5490cn. I installed the drivers from the ubuntu package archive and set up two printer queues, one for "dnssd://<ip-address>" and the other "lpd://<ip-address>/BINARY_P1".  The first appears to recognize that the printer color ink is low, so perhaps there is some communication, but nothing ever comes out of the printer.  The second queue appears to fail completely.

I vaguely recall that for my previous installation I used the package supplied by Brother, but that it was very difficult, since the package no longer matched the Ubuntu file layout and locations.

Any suggestions?

Brian

---

### Post by skewray on 2010-09-08
bump

---

### Post by wojox on 2010-09-08
I installed mine by using this tutorial starting at **Step 4:**

---

### Post by plucky on 2010-09-08
> **wojox said:**
> I installed mine by using this tutorial starting at **Step 4:**

What Tutorial?

> I installed the drivers from the ubuntu package archive

As far as I can see the drivers are not packaged in synaptic,so you should download the Cups wrapper and lpr drivers from the [Brother Website](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) and follow the online install instructions.

Good Luck

---

### Post by wojox on 2010-09-08
> **plucky said:**
> What Tutorial?

Doht  :oops:  [This tutorial]("http://ubuntuforums.org/showthread.php?t=590793&highlight=Brother+printer")

---

