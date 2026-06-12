---
title: "Automated Ubuntu Installs"
date: 2004-11-15
forum: Installation &amp; Upgrades
---

### Post by randy on 2004-11-15
I was looking around and I can't seem to find a way to do a fully automated installation of Ubuntu (or Debian).  The only tool that I could find that may have a chance would be fai but that doesn't support bootable cds according to the manual.  Does anyone have any solutions to this problem?

---

### Post by FLeiXiuS on 2004-11-15
[QUOTE=randy]I was looking around and I can't seem to find a way to do a fully automated installation of Ubuntu (or Debian).  The only tool that I could find that may have a chance would be fai but that doesn't support bootable cds according to the manual.  Does anyone have any solutions to this problem?[/QUOTE]


I don't have any solutions, not sure why you would want to do an automated install.  If your looking for doing some mirroring of hard drives for multiple installtions and you don't want to go through the prompts duringh the installation, then I would say to mirror your drive to serveral cd's.


**partimage**
This was a very sweet open source program which MadAdmin had handed down to me over at MadPenguin.org.  I found it to great use maybe you could also?

---

### Post by randy on 2004-11-15
That program looks a little inflexible, we need a solution that can do heterogenous systems.  Thanks for the link though.  It looked pretty interesting.

---

### Post by FLeiXiuS on 2004-11-16
I believe they have altiris for linux now.

[http://www.altiris.com/](http://www.altiris.com/)


Not free, but it'll get the job done in a quick manner.

---

### Post by randy on 2004-11-16
I'm looking into seeding the installs, the Sarge installer supports it.  That or else I might roll my own installer using anaconda. Were a bit short on funding for any non free solution.

---

### Post by foolswisdom on 2004-11-22
On The Ubuntu-devel mailing list in a subject titled "Ubuntu derivatives : howto ?" "Michael McCabe" suggested FAI (Fully Automatic Installation) for Debian GNU/Linux <http://www.informatik.uni-koeln.de/fai/>

---

### Post by calvinpriest on 2004-11-22
Here's something about using FAI with bootable cds:
[http://members.iinet.net.au/~niall/fai/](http://members.iinet.net.au/~niall/fai/)

It looks like this package is still being tested, but could get the job done for you.

---

