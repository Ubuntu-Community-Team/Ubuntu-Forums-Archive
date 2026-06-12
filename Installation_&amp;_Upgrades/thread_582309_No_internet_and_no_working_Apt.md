---
title: "No internet and no working Apt"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by gaylapdancer on 2007-10-19
Hey Guys.

After making a fresh install of 32 bit Gutsy where my old 64 bit Feisty used to be (Hated 64...) I can no longer get to the internet, nor contact any mirrors with apt. The install, upon reaching 92%, froze for 30 minutes before popping up and stating that it couldn't find any mirrors/repositories. When I reached the desktop I went into sources.list and uncommented all the repositories and ran
 ```
sudo apt-get update
```
It failed on every single one of them.

I can see the outside world via ping, and occasionally firefox will connect to google, but then will refuse to go anywhere.

Anyone know a solution for this?

Any help is -greatly- appreciated.

---

### Post by steviemc on 2007-10-20
Sounds similar to the issue I had...try this...

3.2.7.&#8195;IPv6 Not Supported

   1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
   2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
   3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
   4. Reboot Ubuntu.

---

