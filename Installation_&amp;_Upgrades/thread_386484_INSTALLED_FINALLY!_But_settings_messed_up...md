---
title: "INSTALLED FINALLY! But settings messed up.."
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by mmilitia9 on 2007-03-17
I finally got Ubuntu to install after reading this great post:
[http://ubuntuforums.org/showthread.php?t=380790](http://ubuntuforums.org/showthread.php?t=380790)

Now, Everything was GREAT.  I was able to use my Nvidia FX 5500 flawlessly for a little bit.  I noticed a update button on the top right and decided to update..
It told me I needed to reboot.  Everything was fine until It couldn't load ubuntu

I got this blue screen saying something about how X isnt configured right.  All the settings the reference said to add in are still their and listed.  

What exactly should I do from this point?

Thanks,

Dominick

---

### Post by Kateikyoushi on 2007-03-17
Try to reconfigure X, copy the following line to the terminal, Applications > system tool s > terminal.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by confused57 on 2007-03-17
You might be experiencing this problem with the kernel update:
[http://www.ubuntuforums.org/showthread.php?t=359752](http://www.ubuntuforums.org/showthread.php?t=359752)

See if your older kernel will boot.

---

### Post by mmilitia9 on 2007-03-17
Sigh.. nothing works.  Can't roll back.  

Wish I never updated....

---

### Post by benson444 on 2007-03-17
This is mentioned a few times in confused57's link but maybe you haven't tried this exact command.

sudo apt-get install linux-restricted-modules-`uname -r`

I have to do this on feisty after every kernel update.

---

