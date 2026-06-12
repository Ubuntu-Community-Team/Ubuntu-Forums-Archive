---
title: "Cant install wine / libc6-i386"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by markcoker on 2011-03-02
Hi,

im trying to install wine1.3 and i need to upgrade libc6-i386 so i let apt-get try to do it, but it hangs at unpacking the deb, normally it has no problem no error occurs just sits there like its a huge deb but its only 3mbs.

ive tryed using synaptic and doing the following.

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
sudo rm /var/cache/apt/archives/lock
sudo apt-get check
sudo apt-get clean
sudo apt-get update
sudo apt-get install -f
sudo apt-get purge remove libc6-i386

anyone got any ideas? 

p.s. on a sidenote i cant get audio working. its muted and hasnt got the modules installed for the sound card.

thanks in advance.

Mark

---

### Post by markcoker on 2011-03-02
let me know if you need anymore info

---

