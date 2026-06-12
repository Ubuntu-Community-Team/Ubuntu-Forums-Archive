---
title: "Verry Slow synaptic on Lucid Lynx"
date: 2010-01-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gheorghe_pop on 2010-01-16
Hello all!

When I use the update manager or Synaptic package manager to retrieve files I am getting very slow transfer speeds. Typical speed is 40-60 K Bytes per second and sometime as slow as 4 K Bytes per second.

I can go the same site with firefox and can get over 700 K Bytes per second.

On the ubuntu system, if I use ftp from the command line or use ftp protocol in synaptic, to the same site I get > 700K per second.

Can someone tell me why this happens?

---

### Post by k64 on 2010-01-16
Try the Ubuntu Software Center instead of Synaptic. How you access it:

Invoke the Applications menu, and click on Ubuntu Software Center.

---

### Post by VMC on 2010-01-16
> **gheorghe_pop said:**
> Hello all!

When I use the update manager or Synaptic package manager to retrieve files I am getting very slow transfer speeds. Typical speed is 40-60 K Bytes per second and sometime as slow as 4 K Bytes per second.

I can go the same site with firefox and can get over 700 K Bytes per second.

On the ubuntu system, if I use ftp from the command line or use ftp protocol in synaptic, to the same site I get > 700K per second.

Can someone tell me why this happens?

Anything under synaptic>preferences>network>proxy server. Is it set for default?
Maybe try clean cache. I use aptitude for most of my updates/downloads.

---

### Post by gheorghe_pop on 2010-01-16
In Ubuntu Software Center everything is working OK, normal speed, but unfortunately is very hard to distinguish packages in it. 

In synaptic network preferences is put direct connection to Internet due to the fact that i don't have any proxy.

I have to mention that also aptitude and apt have the same behavior.

Is there a way to see how synaptic is getting on the Internet, maybe the connection is limited from the computer?

---

### Post by ranch hand on 2010-01-16
It may be a problem with your mirror.  Have you tried it on another one to check?

---

### Post by gheorghe_pop on 2010-01-16
No it's not a problem with the mirrors. I'll give you an example.

If I download this file [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/x/xulrunner-1.9.3/xulrunner-1.9.3-dbg_1.9.3~a1~hg20100113r37131+nobinonly-0ubuntu1~umd1_amd64.deb]("http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/x/xulrunner-1.9.3/xulrunner-1.9.3-dbg_1.9.3~a1~hg20100113r37131+nobinonly-0ubuntu1~umd1_amd64.deb") in firefox i getit with >600KB/s but if i download the same file with synaptic or apt I get it with < 13KB/s

---

### Post by ranch hand on 2010-01-16
That is a bit of a difference.  Beats me.

My speeds in synaptic and apt are about the equal to each other and running great.  I chroot to other partitions here on the test drive to do updates and such and generally run 2 of the buggers at once and get about 175 to 220kb.  One at a time runs about 330kb which is right for my connection.

---

### Post by Ibidem on 2010-01-16
Well, use FTP in Synaptic!  No clue what the issue is, though I seem to vaguely recall seeing something like that once.

---

