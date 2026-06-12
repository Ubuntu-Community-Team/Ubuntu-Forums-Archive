---
title: "Ubuntu offline updates"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by samarsingla on 2010-06-23
Hello
I have 7 computers with Ubuntu 10.04 without internet at work and one computer with internet at home. Is it possible to upgrade the 7 computers via a external hard drive using by making a local repository on the computer with internet? If yes, what is the best way to do so?

Cheers
Samar
gadha.org

---

### Post by davidmohammed on 2010-06-23
yes its possible - see [this link]("http://techspalace.blogspot.com/2009/04/offline-update-ubuntu.html") for a step by step guide

---

### Post by eltonw on 2010-06-23
> **samarsingla said:**
> Hello
I have 7 computers with Ubuntu 10.04 without internet at work and one computer with internet at home. Is it possible to upgrade the 7 computers via a external hard drive using by making a local repository on the computer with internet? If yes, what is the best way to do so?

Cheers
Samar
gadha.org

1) Run the Upgrade Manager (on the Internet connected machine), select 'Download packages only', rather than "install". 
2) Just copy them to a DVD or external HD. Thereafter the upgrades will be available for offline installation to the other machines.

HTH....

---

### Post by mac9416 on 2010-06-26
> **davidmohammed said:**
> yes its possible - see [this link]("http://techspalace.blogspot.com/2009/04/offline-update-ubuntu.html") for a step by step guide

The trouble with that method is this: the lists of available packages  resides on the Internet; if your offline computer has never been online, Synaptic will not know what packages are available.

A better solution would be to make an [APTOnCD]("http://aptoncd.sourceforge.net") on the online computer, and install the software from it on your seven offline computers,

---

### Post by afro.ganteng on 2011-03-25
> **mac9416 said:**
> The trouble with that method is this: the lists of available packages  resides on the Internet; if your offline computer has never been online, Synaptic will not know what packages are available.

A better solution would be to make an [APTOnCD]("http://aptoncd.sourceforge.net") on the online computer, and install the software from it on your seven offline computers,

Any Tutorial to use APTOnCD for this case ??

and which one better APTOnCD and Keryx for this case ??

I am using ubuntu 10.10 now

---

### Post by EthioJOB on 2011-03-28
There seems to be no APTonCD on the sourceforge website. What's the problem?

---

