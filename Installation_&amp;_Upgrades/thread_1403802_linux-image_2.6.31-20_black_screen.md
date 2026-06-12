---
title: "linux-image 2.6.31-20 black screen"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by Cathhsmom on 2010-02-10
I am getting a black screen on the latest kernel upgrade [I]2.6.31-20.  My computer completely boots up, but goes black after a minute or two. For now, I am booting up with the previous kernel. 

Heads up, I am an amateur on linux, so help with laymen terms would be nice. Thanks!
[/I]

---

### Post by raygj on 2010-02-10
looks like you may not be running your 3D video driver ,but have your 3D effects enabled for your desktop.
after booting up ubuntu ,on the desktops  panel
goto and open "main menu-->System-->Administration-->Hardware Drivers"
 and activate the  accelerated 3D video driver.

---

### Post by Kir_B on 2010-02-10
Try o0ne of the following command, depending on which grub you're using, and then please post the results for us all to see. Try the first on first.

For grub legacy {comes with jaunty and must be upgraded to grub2, so you may still have grub legacy if this is the case.}:

```
sudo update-grub
```this one seems to work for both grubs, so try it first.

for grub2 {comes installed automatically with karmic}:

```
 sudo grub-mkconfig -o /boot/grub/grub.cfg
```

peace kir_b

---

### Post by Cathhsmom on 2010-02-12
I tried the first one and so far it is working.  I tried to duplicating what I was doing the day it kept giving me a black screen.  I was doing a simple email with Thunderbird.   Thank you Kir_b.

---

