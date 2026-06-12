---
title: "Network Install Broken??! (Local mirror &amp; netboot)"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by feld on 2007-12-02
I can successfully netboot and run the installer. I have the i386 Gutsy DVD mounted and symlinked into /var/www/ubuntu so you can access it at my server @ 192.168.1.144/ubuntu.

This works just great; no issues. The problem is when I go through the installation. I can complete the BASE install -- kernel, base packages, etc... and then it asks me what else I want to do -- DNS server, OpenSSH server, Ubuntu Desktop -- THIS is where it fails. I choose ANY of them and it fails. There are no error messages and nothing I can find. It simply says Installation Step Failed after installing "discover1" and "xresprobe".

The DVD ISO is not flawed; I have checksummed it several times. There are no issues there. There are no issues with permissions and downloading the packages -- the webserver logs are clean.

Why does this happen? can anyone explain?

---

### Post by feld on 2007-12-02
OK after finding that there are install logs and doing some quick testing I figured part of this out, but there is still a bug here!


BUG: You can't select OpenSSH Server. It says that it doesnt know what that is in the logs and it bails.

You CAN select Ubuntu Desktop and successfully install. The catch? You need to use APACHE as your webserver. I was using Lighttpd. The logs show this error:


Dec  2 11:58:28 in-target: E: Method http has died unexpectedly!

It appears Lighttpd is stopping the ENORMOUS amount of requests and the install dies..... I'm reporting a bug to Lighttpd

---

### Post by feld on 2007-12-02
for anyone that cares, this is likely just a lighttpd 1.4 bug and will probably work fine with the much-revamped 1.5 branch.

---

