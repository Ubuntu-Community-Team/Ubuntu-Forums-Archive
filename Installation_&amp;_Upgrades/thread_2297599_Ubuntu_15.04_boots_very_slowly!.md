---
title: "Ubuntu 15.04 boots very slowly!"
date: 2015-10-05
forum: Installation &amp; Upgrades
---

### Post by TBK on 2015-10-05
I have installed Ubuntu 15.05 32 bit and Ubuntu boots very slowly, about 1m45s. I don't know why?
I installed and used Ubuntu and it booted very fast, now I'm using Window 10, Linux Mint 17.2, OpenSUSE 13.2, Manjaro 15.09 on this computer and all of them boot very fast.
My hardware information:
CPU: Pentium(R) Dual-Core CPU E6500 @ 2.93GHz × 2
Ram: 1 GB
Video Card: Intel® G41 x86/MMX/SSE2.
Is this an error and how to fix this? I don't want to reinstall Ubuntu!

---

### Post by oldfred on 2015-10-05
You would get a huge performance boost by upping RAM to 4GB and using 64 bit Ubuntu. My Core2 Duo was originally 32 bit in 2007, but in 2009 I converted to 64 bit.

Using either log file viewer or directly opening dmesg check dmesg. If using the newer systemd, it writes different logs which I am not familiar with yet.

sudo grep -E -i "error|warning" /var/log/dmesg

Open file and look for any long difference in timestamps.

 gksudo gedit /var/log/dmesg

Post the first & second entry with big differences. Do not post entire dmseg as it is huge.

---

### Post by TBK on 2015-10-07
I used:
sudo grep -E -i "error|warning" /var/log/dmesg
gksudo gedit /var/log/dmesg

And then in gedit: (Nothing has been logged yet.)

---

### Post by oldfred on 2015-10-07
Your 15.04 must be using the new systemd.
I have not used any of this:

[URL="https://wiki.archlinux.org/index.php/Improve_boot_performance"]https://wiki.archlinux.org/index.php/Improve_boot_performance
https://bbs.archlinux.org/viewtopic.php?id=189354[/URL]
systemd-analyze blame
systemd-analyze critical-chain

[http://www.dedoimedo.com/computers/systemd-blame.html](http://www.dedoimedo.com/computers/systemd-blame.html)

---

