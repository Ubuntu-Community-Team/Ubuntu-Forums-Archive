---
title: "Can not shutdown or restart laptop after installing Ubuntu 16.04"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by nikhilbhalwankar on 2016-04-25
Hi,
 
I can not restart or shutdown my laptop after installing Ubuntu 16.04. Anybody please help? I tried using below commands but laptop freezes and does not shutdown.
[B]
sudo halt
sudo shutdown -h now
sudo shutdown -h 0
sudo poweroff&#65279;[/B]


Kindly help. I can not force stop laptop everytime by long pressing power button.

---

### Post by RobGoss on 2016-04-25
Hello and welcome to the forum

You might want to post the specs for your machine right now all we can do is guess what may be causing your issues.

---

### Post by nikhilbhalwankar on 2016-04-25
Hi,

Laptop:- Lenovo 3000G Series
Ubuntu:- 16.04 LTS 32 Bit

I was not facing this problem on Ubuntu 14.04 LTS

---

### Post by RobGoss on 2016-04-25
> **nikhilbhalwankar said:**
> Hi,

Laptop:- Lenovo 3000G Series
Ubuntu:- 16.04 LTS 32 Bit

I was not facing this problem on Ubuntu 14.04 LTS


Have you try to do another clean installation it may correct it self.

Question, Have you made any changes to your login screen?

---

### Post by nikhilbhalwankar on 2016-04-26
Hi,

The issue is resolved. I again did a clean install but selected below options

1) Do not select third party drivers
2) Enabled LVM partitioning support


Now laptop can start/stop without any issues.

---

### Post by RobGoss on 2016-04-26
Great glad you found a fix, if you are happy with the out come of this post can you mark this thread as solved, you can use the** Thread Tool** at the top of this post. Thank you

---

