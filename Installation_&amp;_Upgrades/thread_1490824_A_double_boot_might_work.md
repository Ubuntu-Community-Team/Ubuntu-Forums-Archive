---
title: "A double boot might work?"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by pitroadrush on 2010-05-22
Hello, I'm running a second HD with Windows. Planning to install the other part around 120 g of the HD with ubuntu. 
Now when I choose in my bios my second HD to boot.
I will have the option for windows or ubuntu?
previous experiences suggestions.:popcorn: 
thanks,
Mk

---

### Post by Gyanos422 on 2010-05-22
> **pitroadrush said:**
> Hello, I'm running a second HD with Windows. Planning to install the other part around 120 g of the HD with ubuntu. 
Now when I choose in my bios my second HD to boot.
I will have the option for windows or ubuntu?
previous experiences suggestions.:popcorn: 
thanks,
Mk


Ok i'm by far no ubuntu expert, but if i understand you, you want to run Ubuntu on one hard drive and Windows on another, and have the option to boot from either one, correct?

If so, this is what i did.

1. since i already had windows installed i just unhooked the windows hard drive, and hooked up a hard drive to install Ubuntu onto.

2. I installed Lucid to the new drive.  after installing, i shut down my pc and hooked the windows drive up as the slave drive.

3. booted up, and i started a thread and eventually got this answer from [carl4926]("http://ubuntuforums.org/member.php?u=809261") [Thanks to him again for the help before]

All you need to do is run this from Ubuntu console (this is with both HD's  connected)

```
sudo update-grub
```

then 

```
sudo grub-install /dev/sda
```


Try to restart and see if it shows up with a boot menu.

note: i have XP installed, so if anyone knows if this is different between xp and vista/7

---

