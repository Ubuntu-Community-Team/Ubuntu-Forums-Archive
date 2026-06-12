---
title: "[SOLVED] Flash player!"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by Redundant Username on 2008-11-17
I having problems installing flash player. I tried **all** of the install methods and I kept getting errors.:(

---

### Post by Pumalite on 2008-11-17
Check this thread:
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by anystupidname on 2008-11-17
When you don't outline what all of these "methods" were or any of the errors your got, it makes it difficult to assist you.

Why don't you follow these directions and tell us exactly what errors you get?

1) Go here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
and download the "deb for Ubuntu" package to /tmp/
(I'm assuming you're running 32bit Ubuntu hardy or intrepid)
(if you're on 64 bit, see what pumalite linked)

2) Open a terminal and run
> cd /tmp
install_flash_player_10_linux.deb

3) Restart your browser

4) If you're running Firefox, you can verify flash 10 was installed by typing "about:plugins" in address bar.

---

### Post by Skripka on 2008-11-17
> **anystupidname said:**
> When you don't outline what all of these "methods" were or any of the errors your got, it makes it difficult to assist you.

Why don't you follow these directions and tell us exactly what errors you get?

1) Go here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
and download the "deb for Ubuntu" package to /tmp/
(I'm assuming you're running 32bit Ubuntu hardy or intrepid)

2) Open a terminal and run


3) Restart your browser

4) If you're running Firefox, you can verify flash 10 was installed by typing "about:plugins" in address bar.

It makes things more difficult when we don't know if he is using 64bit or 32bit, or what version of what linux he is using.....

---

### Post by aysiu on 2008-11-17
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
sudo updatedb
locate flash
uname -m
cat /etc/lsb-release
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
``` Warning: the first command may take a few minutes to execute.

---

### Post by Redundant Username on 2008-11-17
Thanks!

---

