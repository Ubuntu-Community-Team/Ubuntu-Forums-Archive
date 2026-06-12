---
title: "Installation stalls at 76% on &quot;Configuring wvdial&quot;"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by cougar_lt on 2006-09-10
Hello. I've used Suse Linux 10.0 and I really liked it very much, but it seemed a little too big for me, so I decided to try Ubuntu 6.06. At first I downloaded Ubuntu desktop CD, it worked fine, but installer crashed on detecting partitions. Tried some more times, but always got the same problem. Then I downloaded Ubuntu 6.06.1 Alternate Install CD. At the beginning everything was fine, I partitioned my HDD without problems, the base system installed, but the installation stopped at 76% showing me "Configuring wvdial" on the screen. I've been waiting for about half an hour, but nothing has happened. Then I had a hard reboot, tried two more times, but always got the same problem. I tried installing in simple mode and later in expert mode, but everytime was the same. How can I deal with this problem? My PC is Athlon 1,3 GHz, 256 MB RAM, 80 GB HDD, GeForce 4 MX4000 PCI, Chaintech 7AIVL mainboard, PCI network adapter, if it says anything to you. Also I tried installing Kubuntu 6.06, but got the same problem. Suse and Windows XP installs without problems.

---

### Post by cougar_lt on 2006-09-10
Hey, doesn't anyone know how to deal with this problem?

---

### Post by cougar_lt on 2006-09-12
I'm completely disappointed with Ubuntu 6.06. 5.04 installs just perfectly, but it's too old.

---

### Post by billyboy_oh_boy on 2006-09-24
Hi cougar_It:

I had the same problem. I tried to install Ubuntu 6.06 using the Alternate Installation disk. I tried 2 different iso-burns and check both CDs with CD-check feature on the first menu of the installation. Have you solved this problem?

Maybe this has something to do with the modem. I am conected to the web with a DSL modem.

Billyboy.

---

### Post by caf0696 on 2006-11-06
I have the same problem, my solution is :
1. press ALT-F2
2. press "Enter", enter command-line mode
3. type "ps", you can see the PID of the wvdial
   like below example:

12345 root 2552 S wvdialconf /etc/wvdial.conf

then we know the PID of wvdial is "12345"

5. Kill the PID of wvdial

just execute 

kill 12345

12345 is the PID of wvdial we just find.

6. The installation will continute.:D 

Try it!

---

### Post by neocorate on 2007-09-25
=D>
Thank you from the bottom of my heart.  My computer doesn't have an internal modem.  If that's why the Alternate Install of Xubuntu Feisty freezes there, the great ones who assemble the distribution should be made aware of it.

---

