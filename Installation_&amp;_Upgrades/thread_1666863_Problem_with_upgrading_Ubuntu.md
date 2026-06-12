---
title: "Problem with upgrading Ubuntu"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by orestision on 2011-01-14
Hello,

I am new in linux and i have a problem with the installation of Ubuntu.I used a cd version of ubuntu 10.4 but my laptop wouldn't boot.I thought of installing the previous version of ubuntu and then upgrade it.I used ubuntu 9 and it worked perfectly. But when the upgrade finished and my pc restarted it showed this message

[1.007098] Disabling IRQ#4

and it stuck.
What does it mean?

---

### Post by dino99 on 2011-01-14
look at your bios settings about irq

if nothing can help or be done inside the bios settings, then on the boot line (F6), add irqpoll

---

### Post by Rubi1200 on 2011-01-14
> **orestision said:**
> Hello,

I am new in linux and i have a problem with the installation of Ubuntu.I used a cd version of ubuntu 10.4 but my laptop wouldn't boot.I thought of installing the previous version of ubuntu and then upgrade it.I used ubuntu 9 and it worked perfectly. But when the upgrade finished and my pc restarted it showed this message

[1.007098] Disabling IRQ#4

and it stuck.
What does it mean?
Hi and welcome to the forums :)

What graphics card do you have installed?

---

### Post by orestision on 2011-01-14
I have an NVIDIA GeForce 9300M

The same message appeared when i tried to install mint 10.

---

### Post by orestision on 2011-01-14
I can not find anything about irq in the BIOS and the only thing that appears on my screen after the start up is the disabling message.

---

### Post by Rubi1200 on 2011-01-14
You can try using the nomodeset option when booting.

Press "e" to edit the entry and remove quiet splash. Type nomodeset and "Ctrl" + "x" to boot.

---

### Post by orestision on 2011-01-14
Thank you,that was very helpful.

---

### Post by Rubi1200 on 2011-01-14
If you have booted Ubuntu you can check to see if the drivers are properly installed.

[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

