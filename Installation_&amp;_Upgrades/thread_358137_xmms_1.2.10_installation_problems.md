---
title: "xmms 1.2.10 installation problems"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by pedrok on 2007-02-10
Hi,

I installed ubuntu 5.10, and i would like to install xmms. Ive searched the net
and found some people with the same problem, but the advices are not working + im basically
new in linux.

Ive downloaded: glib-1.2.2.tar and xmms-1.2.10.tar

So i followed this procedure:

1. logged as root

2. in the command-line i typed: apt-get install build-essential(success)

3. then unzipped the glib-1.2.2

4. then followed the instructions in the "install" file
4.1 ./configure
4.2 make
4.3 make install

5. from there, not knowing if it was successful or not, unzipped the xmms-1.2.10

6. then followed the instructions in the "readme" file
6.1 ./configure
6.2 which led to: GLIB >= 1.2.2 not installed - please install first

Then i tried, glib-1.2.9, and gives the same error.

Please help

---

### Post by Eazy© on 2007-02-10
sudo apt-get install xmms is not an option?

---

### Post by pedrok on 2007-02-12
Hi, no doesnt work. Even reinstalled ubuntu. But thx!

---

