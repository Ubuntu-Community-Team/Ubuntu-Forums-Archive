---
title: "Minimum Requirements"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by pak33m on 2006-06-08
Are there any listed?

Trying to install on a Dell Inspirion 5000 Laptop with only 95MB RAM.  Found out that a 256MB RAM module was bad that I had installed and 95MB RAM is all I have at the moment.

Can it be done?

---

### Post by aysiu on 2006-06-08
Xubuntu could work.

You could also try a server install and then ```
sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic
```

Make sure you get the **Alternate Install CD**, not the Desktop CD.

---

### Post by pak33m on 2006-06-08
Hey aysiu,

You pulled through like I've seen you do before.

I ran the alternate CD install using the Text Mode and she worked like a charm.  And not that sluggish at all considering that I was only running on 95MB RAM! 

Ubuntu is such an incredible distro!!

Thank you so much for your help.  Hopefully somebody else will take form this post as I did. [http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

---

### Post by az on 2006-06-08
Is all of your 256 meg module borked or just part of it?

Because you can either use the MEM= bootprompt or compile a kernel with badram and avoid the bad bits.

If, for example, your stick only had bad bits halfway through, or better, at the end, you could still boot and tell the kernel to only use the first half of the ram.  When you run memtest, can you see where the errors start?

Example:  If you remove your other ram and insert the bad module and boot into memtest to find than errors start at 195 megs, you can boot linux with
MEM=194 and it will just not use any ram above 194 megs.  Your safe and you get to use most of your module.

With badram, you can specify just a few bits, if that's all that is borked.  You you would be able to use all of your ram except those few bad bits.

---

### Post by pak33m on 2006-06-11
Hey azz,

It defainely seems tha the module is bad.  I tried to start the laptop with just the 256MB module and it kept trying to restart but never booted.  I ran the memtest several timkes but it filed all the way through.

It's not as fullfilling as it could be running 6.06 on 95MB RAM, but I have to admit that it sure can still perform a TON.  And what's more is that I'm running a desktop...WOW!

Thanks azz for your input.

---

