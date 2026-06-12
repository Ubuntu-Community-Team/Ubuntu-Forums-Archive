---
title: "Ubuntu 6.06 install hangs after 1+ hours, does not hang when running from live-cd"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by crcarlson on 2007-12-09
Hi,

My System:
 AMD 1.1Ghz, 256M Ram, 60 Gig HD

I am trying to run the 6.06 distribution so that I may run the EMC2 packages from [www.linuxcnc.org](www.linuxcnc.org) which at this time only support 6.06.

I started by installing their live-cd.  The system appeared to run great, however would hang after a hour or so.  Even if I just rebooted the machine and let it sit at the login screen.

I had the screen saver turned off.

Memtest ran with no trouble

I increased the ram to 512MB

I swapped power supplies

I have cleaned all the heat sinks on my machine and the fans are all running

I have tried changing my video card driver to versa

The latency test they ship with runs fine, 12000ns max latency

Now I am now running just the 6.06 live-cd install.  When booting from the HD, it still hangs after an hour or so.

For whatever reason, booting from just the 6.06 live-CD runs great for 12+ hours.

Any ideas?

---

### Post by cmnorton on 2007-12-09
It would help to post some logs and look for timestamps before you reboot, dmesg, /var/log/messages, and /var/log/syslog.

I found 6.06 to be very stable and install easily, once I went with safe mode. I installed 6.06 on an older Acer Travelmate 630 laptop.

---

### Post by crcarlson on 2007-12-09
Hi Charles, thanks for the reply.

I am a little unclear on what would be the most helpful thing to post.

Once the machine has frozen, nothing works, not even the caps lock key light.

Do the logs persist over more than one boot?

As a guess, I have attached those three logs in a zip file.

-Chris.

---

