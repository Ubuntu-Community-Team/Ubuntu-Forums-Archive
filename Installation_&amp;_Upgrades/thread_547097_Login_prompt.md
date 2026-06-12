---
title: "Login prompt"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by almostalive on 2007-09-09
hello, it's my first time installing ubuntu, so I'm sure this is a very newbish question

I downloaded/burned the live CD iso, put it in, and rebooted my system.
I booted into the CD, I then chose the first option listed on the menu. "install or start Ubuntu"
then it loads for about 3 minutes, bringing me to an Ubuntu login screen

It then asks for a user/pass, but I don't have any...?
I tried typing in default user/passes.. 'root', 'admin', ect.. nothing works.

am I missing something? All I want to do is install Ubuntu on my system!

thanks.

---

### Post by Pumalite on 2007-09-09
You might need Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below 'Start Download'. Post your specs to confirm.

---

### Post by almostalive on 2007-09-09
Dell Dimension 2400
RAM: 766MB
Intel Pentium 4, 2.66Ghz
soundcard: soundmax
graphic card: Radeon 9250

i've also tried the alternate CD already. everything went smoothly until it got to the screen "Choose and install your software"
when it got to that step, it said there was an error, and it asked me to skip that step. so I did.
I finished installing it. but whenever I boot into that partition, it only loads a CLI..
so I guess the step I skipped is kind of mandotory for the installation? 'cause there's no GUI at all..
(or did I accidently use a CLI installation..? don't think I did)

- I guess I will try to burn another Alternate CD.. I guess the last one was corrupt, or burned incorrectly. I'll see how it goes this time.

---

### Post by Pumalite on 2007-09-09
Maybe all you need it to configure xserver. At the CLI, try this:
sudo dpkg-reconfogure xserver-xorg; choose most defaults, choose 'vesa' as the driver. Then:
startx

---

