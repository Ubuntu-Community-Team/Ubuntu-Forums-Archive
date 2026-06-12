---
title: "Ubuntu crashes during install"
date: 2015-07-18
forum: Installation &amp; Upgrades
---

### Post by Bas_Odekerken on 2015-07-18
So I have been trying to install Ubuntu on my old laptop (HP pavilion dv6).
But the problem I'm getting is that during the installation it crashes and restarts to windows 7 when I choose the "Install inside windows 7" option.
I have tried it with Ubuntu 14.04 LTS, 15.04 and GNOME 15.04.
Hopefully someone can halp me with this problem.

---

### Post by yancek on 2015-07-18
How old is your "old HP Pavilion"?  Post some info on your hardware.  Did you select the option to install Alongside?  I've never seen install "Inside" but maybe that's a WUBI install?

---

### Post by Bucky Ball on 2015-07-18
Welcome. You are trying to install Wubi. Don't go there. It is dead and, although still available, not supported by Canonical or these forums. We can't give a lot of help as not used. In other words, do not choose the 'install inside Windows' option. If you do, you will be pretty much on your own. 

Please try a dual-boot with Windows. Ask any questions you need to to achieve this. Start with downloading the 14.04 LTS .iso from [here]("http://www.ubuntu.com/download/desktop"). Good luck.

PS: See also [here]("http://ubuntuforums.org/showthread.php?t=2229766"). :)

---

### Post by v3.xx on 2015-07-18
```
the "Install inside windows 7" option
```
Thats called WUBI.
Something that I have not used, but I understand the project is no longer maintained.

I would suggest installing on a partition.  Ask questions here to be sure your ready

First run the live session.  Ubuntu & u/Gnome both require a faster computer and more ram.

Edit..
I should of refreshed before posting..ninja by BB&y

---

### Post by Bucky Ball on 2015-07-18
> **v3.xx said:**
> 

Edit..
I should of refreshed before posting..ninja by BB&y

It happens. Now I'm going to jump backwards on to a roof. :)

---

### Post by Bas_Odekerken on 2015-07-18
My laptop is about 4 years old.
CPU: Intel core I3 m370 @2.4Ghz
RAM: 4GB
GPU: Mobility radeon hd 5650
HDD: 500gb

64-bit Windows 7 Home premium

---

### Post by Bas_Odekerken on 2015-07-18
There seems to have been a small misunderstanding I think.
I have created a 64gb unused partition in windows and I can see it when I click 'something else'.
After [this]("https://drive.google.com/file/d/0B9fNyTAGVsDxVUpHZUtrdm50QXM/view") step the installer crashes and restarts to Windows.

---

### Post by Bas_Odekerken on 2015-07-18
I am trying to install it for dual boot. There's a link to an image of the step in the last reply I made.

---

### Post by yancek on 2015-07-18
I've never seen the "install inside windows" option so I guess as others have said, it might be a WUBI install which is no longer supported.  Your best option to have control over the install is to select the "Something Else" option.  Might be a good idea to read a how to install Ubuntu tutorial before proceeding if you have not done so.

---

### Post by Bucky Ball on 2015-07-18
You are not attempting to install in dual-your are attempting a Wubi install. As mentioned, don't go there. Use 'Something Else'. See [here]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352").

---

