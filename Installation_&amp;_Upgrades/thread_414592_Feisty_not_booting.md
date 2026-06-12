---
title: "Feisty not booting"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Alecks02 on 2007-04-20
Hi, this is my first time trying to install a linux distro and I burned the amd64 iso to a CD and booted into the CD. It goes to the initial screen and I select my resolution and language, then I choose to boot/install. After that, I get a loading screen and about 5 minutes later I get errors that start popping up such as

"288.423271 hdc: Error Code: 0x70 sense_key: 0x03 asc: 0x15 ascq: 0x80"
and
"Buffer I/O Error on device HDC, logical block [xxxxxx]"
and finally
"SQUASHFS Error: Unable to read fragment cache block [135DDF9A]"

multiple errors that looked similar to the ones above slowly appeared and scrolled contunually down.

I'm running an AMD X2 3800+ with 3gb of RAM and an ATI X-800 video card. 

Thanks for the help!

---

### Post by bwhite82 on 2007-04-20
Hi, what you have there is a CD problem. Try burning a new disk at a slower speed. BTW, this is DEFINITELY a CD problem, squashfs refers to the compression method for the filesystem so that it will fit on a CD.

---

### Post by Alecks02 on 2007-04-20
thanks, I'll try that

edit: It's installing right now, and works great! Thanks for your help

---

