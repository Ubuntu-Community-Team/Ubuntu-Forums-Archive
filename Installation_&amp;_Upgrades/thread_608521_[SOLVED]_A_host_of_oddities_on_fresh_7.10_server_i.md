---
title: "[SOLVED] A host of oddities on fresh 7.10 server install"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by lalldrin on 2007-11-10
I just installed 7.10 server and it locks after "Running local boot scripts (/etc/rc.local)". I've read that this is likely a video card problem, so I'm trying the advice of a previous post.

I got into the terminal and tried to type a sudo command. Linux said my account was not in the sudoers file. So I used recovery to change the admin password and added my regular account to the sudoers file. I shouldn't have to do all this, but so far so good.

Now, I try to type "sudo dpkg-reconfigure xserver-xorg" and am told that the xserver-xorg package is not installed!

My iso checksum was fine. The CD integrity checked out. The install went fine (text mode). When I boot to the CD, the interface is graphical (VGA working OK).

Any ideas what's going on? It's almost like I don't have a full install with a gui.

Thanks a bunch!

---

### Post by forestpixie on 2007-11-10
if you've installed the server version it doesn't have a gui ( I believe) if you want one you need to run ```
sudo aptitude install ubuntu-desktop
``` or obviously kubuntu-desktop or xubuntu-desktop if you're running either of those

---

### Post by lalldrin on 2007-11-10
OK, so I'm on my first Ubuntu install, my first snag and my first guru reply. I'm tickled with everything but the 11 minutes I had to wait for help. Geesh--where's that brisk open-source community support I've heard so much about? ;-)

Seriously, major thanks for the quick response.

---

### Post by forestpixie on 2007-11-10
I wouldn't be calling me a guru - I've only been here since May - generally if you do need a quick response, I just happened to be passing through - I'd post in the abs beg forum - it can be a bit quicker. If you're completely new to this linux thing - make some timew to have a browse through the forums - you'll pick up bits quickly.

Glad I could help - here's you're next new thing - click the link in my sig and it'll tell you how to mark threads solved, makes it easier for everyone else.

And welcome :D

---

