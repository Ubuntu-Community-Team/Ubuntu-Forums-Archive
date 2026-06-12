---
title: "glx error after update to feisty fawn"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by Dark Lord Peaches on 2007-03-20
i had updated my kubuntu distro to fiesty fawn the other day, and ever since then i have been having problems with the GL screen savers and now i just installed Blender and it wouldnt work so i decided to run it through terminal and i get this error 

```
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.4.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: Unable to open Blender window

``` 

so does it have something to do with the graphics or are they two different problems ive been blessed with

---

### Post by shawnrgr on 2007-04-05
either you don't have proper nvidia driver installed or your card was recently dropped to legacy by nvidia, there is supposed to be an updated nvidia-glx-legacy driver with the final release.

[https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/83147]("https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/83147")
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/96430]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/96430")

---

### Post by duffman.c.d on 2007-04-23
I had exactly the same Problem. I have a nvidia TNT but I presume the same is true for the non-legacy driver.

I fixed it by enabling the driver in Applications>System>Restricted Drivers Manager.
After a reboot it worked fine.

Good Luck :) 
Duffman

---

### Post by arijarot on 2007-05-24
I get this error when I type blender into the terminal 
```
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.4.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: Unable to open Blender window

```
My nvidia is enabled and is a legacy driver version. any solutions known?

---

