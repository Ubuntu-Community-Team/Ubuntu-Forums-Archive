---
title: "strange gdm behaviour"
date: 2009-07-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wayne_cat on 2009-07-27
started today ... I log out ... gdm appears with a background image ... I switch to a tty and then back to tty 7 (gdm) ... and the background images is gone.

[[IMG]http://ubuntu-pics.de/thumb/20128/gdm_screenshot_buzQpR.png[/IMG]]("http://ubuntu-pics.de/bild/20128/gdm_screenshot_buzQpR.png")

edit: Bug Report:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/405392](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/405392)

---

### Post by budluva04 on 2009-07-27
yeah i can confirm this, you should file a bug

billybigrigger@cabo:~$ uname -a
Linux cabo 2.6.31-rc4-billybigrigger0726 #1 SMP Sun Jul 26 15:53:11 MDT 2009 x86_64 GNU/Linux

billybigrigger@cabo:~$ apt-cache policy gdm
gdm:
  Installed: 2.27.4-0ubuntu6
  Candidate: 2.27.4-0ubuntu6
  Version table:
 *** 2.27.4-0ubuntu6 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status

post the bug url here so others can subscribe to it

---

### Post by wayne_cat on 2009-07-27
Thank you for confirming this problem. 

Here is the bug report:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/405392](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/405392)

---

