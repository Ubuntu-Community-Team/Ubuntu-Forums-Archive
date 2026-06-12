---
title: "UNetBootin installed no-GUI Ubuntu"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by xjgnsdof on 2008-05-09
I installed Hardy 32-bit with the linux generic kernel and Kubuntu desktop using UNetBootin. When I reboot into the new OS, I get a command-line; there is no login screen or GUI. I entered the default options during most of the installation process and have installed Ubuntu a bunch of times using a text installer. Am I missing something here?

---

### Post by logos34 on 2008-05-09
could it be an X server problem?

try

ctrl+alt+F1

or

sudo /etc/init.d/gdm start

or 

startx

if it says X failed to load, run sudo dpkg-reconfigure xserver-xorg

Them again, maybe the kubuntu-desktop didn't install after all

---

### Post by xjgnsdof on 2008-05-09
I think you're right; UNB didn't install the desktop. So UNetBootin basically sucks. I knew that installing from CD was best...

Any ideas are still welcome.

---

### Post by dstew on 2008-05-09
To install the desktop, from the command line do```
sudo apt-get install ubuntu-desktop
```I do this all the time when I install over the network, because the entire net install looks like it sticks at 6%. But if you install the server-base install first, then do the apt-get command to install the desktop, you can watch all the packages come in. It's kind of fun (yeah, I should get a life...)

---

### Post by xjgnsdof on 2008-05-09
I assumed that UNetBootin installed the specified desktop. Turns out I had to install a desktop. I now have Ubuntu Hardy Heron on my CD-drive-less VAIO. Thanks.

---

