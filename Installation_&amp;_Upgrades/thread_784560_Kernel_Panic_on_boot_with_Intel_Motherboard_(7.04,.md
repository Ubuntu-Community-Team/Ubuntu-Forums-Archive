---
title: "Kernel Panic on boot with Intel Motherboard (7.04, 7.10, 6.04)"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by tardomatic on 2008-05-06
Hello,

I am hoping that someone can help me with my problem. It seems that my Intel-based motherboard hates the thoughts of something other than Windows controlling it so much, that it will not allow me to install the glorious Ubuntu on it. 

Basically what happens is that I try and boot off the Live CD. It Kernel Panics loudly. The messages vary from obscure to obscurer, and fly across at the screen at a velocity designed explicitly to stop humans from reading or understanding any of it. I tried booting off the alternate CD's, only to be thwarted again and again. Suspecting a hardware issue, i proceeded to remove hardware items one at a time to see what the culprit was. It turns out it is my graphics card. Or rather, the combination of my graphics card and the excuse for a graphics card Intel deemed necessary to solder to the motherboard. The (non-integrated) graphics card is an Nvidia 7300 which has two DVI outs which connect to my two LCD monitors. My (integrated) graphics card has one measly VGA output, which does not cut the mustard. When the Nvidia card is plugged in, the Kernel Panics. When the Nvidia card is removed, the kernel doesn't Panic, and I am able to install Ubuntu without a hitch. Which is great, except I now have only one screen. 

I fruitlessly tried to disable the integrated graphics card in the BIOS. It seems that it has one setting, which is unfortunately set to on permanently. I also thought that maybe, just maybe, that once Ubuntu was installed and running, I could sneak the NVidia card in, but that takes me right back to the Kernel Panic. I thought that perhaps it was the NVidia card itself, so I plugged it into another machine of mine, and Ubuntu worked like a charm. So, I can only assume the problem lies with the fact that there are two graphics cards in the machine, and the Kernel Panics because of this. 

Any advice out there? Is there some way I can tell the Kernel to use my NVidia card only? To ignore the Intel POS? 

Please Help,

Thanks

---

### Post by tamoneya on 2008-05-06
what exactly is your motherboard model.  It will help us better figure out if there is some way to override your internal graphics.

---

### Post by tardomatic on 2008-05-06
Hi,

Just an update... I searched a little further on the forum, and found this post: [http://ubuntuforums.org/showthread.php?t=406205](http://ubuntuforums.org/showthread.php?t=406205)

I'm going to try this tomorrow. I hope it works.

Thanks

---

