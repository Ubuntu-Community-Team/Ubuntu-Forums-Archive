---
title: "Ubuntu 6.06.1-server-No X Window starts `"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by blinton25 on 2007-06-28
I installed Ubuntu 6.06.1-server but when it boots no X window system is launched and I can't start it using StartX ot xTerm. 

I followed the installation instructions at: 

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06) 

and I tried the troubleshooting suggestions at: 

[http://ubuntuforums.org/archive/index.php/t-3784.html](http://ubuntuforums.org/archive/index.php/t-3784.html)

Running the command: dpkg-reconfigure xserver-xfree86 

gives me an error: 

'xserver-xfree86' isn't installed. 

I tried the install twice and got this result.

---

### Post by tgm4883 on 2007-06-28
Server edition doesn't install an X window system (and a quick lookover suggests that neither does that guide)  If you want to install an window system you could do a apt-get install gnome (or kde)

---

