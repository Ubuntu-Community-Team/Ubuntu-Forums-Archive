---
title: "Ubuntu installls on laptop but not PC"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by nchutchind on 2007-02-21
Hey, guys,

     Sorry for the length of this post. I've looked at many different posts regarding the problems I'm having and much of this post is just saying the things I've tried that haven't worked.

     I'm not a linux geek, but I'm comfortable getting around in it. Anyway, here's my problem:

     I've got a laptop for work (Intel 2.4GHz, 60GB HDD, 1GB RAM, Radeon ATI x300) and I installed Ubuntu onto a 10GB partition that I created. Everything worked flawlessly; not a single problem anywhere along the line (I even got Beryl installed with no problems).

     Being happy with Ubuntu, I decided to install it at home on my PC. That's when the trouble started. My home PC has Intel P4 3.2GHz CPU, 250GB HDD, 1.5GB RAM (1024MB and 512MB), and a Radeon ATI x700. I can't get the Ubuntu images to actually run. I tried Ubuntu, Kubuntu and the Alternative Install CD. I did not try Xubuntu because I think my system is good enough to not need it. 

     I get the menu. I have run the memory test (everything is fine with the mem). When I select the first option of viewing the live version (or installing) I get the Ubuntu logo with a neverending progress bar. If I choose the "Safe" graphics version, I get the same thing.

     When I get rid of quick splash, I get lots of Buffer I/O errors where it's looking for some logical partition or something on my CD drive. If I wait long enough, I get a Kernel Panic interrupt error.

     When I get rid of quick splash and type in break=bottom so I can get a terminal to edit /etc/X11/xorg.conf to change the Driver "ati" to Driver "vesa", I still get Buffer I/O errors and a Kernel Panic.

     When I get rid of quick splash and use irqpoll, I get the same thing. If I use irqpoll AND break=bottom, I get no terminal, just Buffer I/O errors and a Kernel Panic.

     I tried removing one stick of RAM per instructions in another post. Nothing changed. I swapped it out for the other stick of RAM (still one stick in system). Nothing changed. Buffer I/O errors and Kernal Panic.

     I burned the ISO at 4x. The same disc worked on my laptop without error. My CD-RW/DVD drives are updated. My memory is good (Corsair, tested fine).

     Does anyone have any ideas as to what I could do to get Kubuntu or Ubuntu onto my PC? I really like how it works and feels on my laptop, and would prefer to have it on my PC. If I can't get it working, though, I reckon I'll have to try a different distro. :( 

     I really appreciate any help you all can give.

---

### Post by nchutchind on 2007-02-21
I checked the laptop again, and it has the same problem with the Buffer I/O (albeit they occur much, much faster and the install gets on with it quicker), so they don't seem to be a big deal.

Another thing that makes me think it's graphics related is that, when I select the option to view the live cd when the CD menu comes up, on the laptop, when it begin to open vmlinuz and the casper stuff, the lines of text show up normally one under the other. On my PC when it does that part, the lines of text overlap each other by half.

I need help!

---

### Post by nchutchind on 2007-02-28
I guess nobody else knew the answer either.

I ended up installing Dapper (which installed without a hitch, by the way). When I tried to upgrade it to Edgy using the "official" method, it updated everything, but I can't load the new kernel. I can still get in with the Dapper kernel, but the Edgy kernel hangs up with that same Kernel Panic sync issue.

So, I reinstalled Dapper and am not going to upgrade it to Edgy. Maybe when Feisty is released in April, it will work for me.

---

