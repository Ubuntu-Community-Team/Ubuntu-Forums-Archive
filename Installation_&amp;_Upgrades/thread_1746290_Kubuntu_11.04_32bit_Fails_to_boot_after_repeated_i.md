---
title: "Kubuntu 11.04 32bit Fails to boot after repeated installs."
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by homer6 on 2011-05-01
I made a post in [http://ubuntuforums.org/showthread.php?p=10753227](http://ubuntuforums.org/showthread.php?p=10753227) but I guess it's closed.

I'm having the same issue. I've installed Kubuntu 11.04 32bit twice now. Both times it doesn't do anything when it reboots. No output to the screen.

When I boot to the LiveCD and chroot or simply mount the /dev/sda device and run 

sudo grub-install --root-directory=/mnt /dev/sda

It says grub installs successfully, but it doesn't fix the problem. Any ideas? Here's my bootinfo RESULTS.TXT

[http://pastebin.com/PF0bF7x5](http://pastebin.com/PF0bF7x5)

Thanks in advance.

---

### Post by homer6 on 2011-05-01
Nevermind. I ditched 11.04 for 10.04.02 LTS. It works fine.

---

