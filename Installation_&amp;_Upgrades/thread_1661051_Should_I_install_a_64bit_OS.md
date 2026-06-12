---
title: "Should I install a 64bit OS?"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by jerry85 on 2011-01-06
I'd like to install the the 64bit edition, but I'm not sure I should..

I've been told its faster for certain processor loaded applications, like audio editing and producing software. (I'm also planning on installing something like SPICE and/or gEDA, basically electronic circuit design and simulation, but this is an other story ;))

Is it really faster? (I have an amd 64 x2 3800+; 2Gb RAM)
won't it cause problems installing certain app's? or are those only windows-problems..
Are there any downsides to a 64bit os? (and upsides? :))

Thanks!

---

### Post by LFS-Nr-3305 on 2011-01-06
I did (10.04 on Athlon-64 ADD3800IAA5CU CPU, good for energy saving). I had the same questions before so I did a test installation before. I now am using the 64-bit Ubuntu approx. 6 months. Firefox, Open Office, Thunderbird, VMWare, GIMP, Zapping TV, Vuescan (needed additional, older libraries), Crossover professional (needed additional compatibilty libraries) with Dreamweaver MX, Irfanview and Internet Explorer, jpilot, Sun Java 6, Opera, Kmail, Brasero and other multimedia software, Dosemu, Truecrypt and everything else did work out-of-the box, so I think there is no reason not to install a 64-bit OP System. If I read all the facts about 64-vs 32-bit OP, it seems to bring an approx. 10% advantage.

---

### Post by presence1960 on 2011-01-06
If you have a 64 bit processor you should use 64 bit OSs. You paid for the technology so you might as well use it. 64 bit has matured and runs quite well, so much so that if you look at our forum's categories the 64 bit forum has been closed. [Here]("http://ubuntuforums.org/announcement.php?f=343") is the explanation.

---

### Post by jfbilodeau on 2011-01-06
I've been using Ubuntu64 for a couple of years now. I did not have any issues with the last two releases. I would recommend it.

---

### Post by jerry85 on 2011-01-06
thanks for the advice! I'm probably going to install it. It's just that I'm a new Linux user and still figuring out what the possibilities are (as well as the difficulties..) 

perhaps I'll start by installing it on a separate partition :) so I can test it w/o loosing my working ubuntu.

---

### Post by oldos2er on 2011-01-06
> **jerry85 said:**
> won't it cause problems installing certain app's? 

If you have hardware for which the manufacturer only supplies 32-bit drivers, that's one possible problem.

Also if you're going to run 64-bit Ubuntu with flash, you should install 64-bit flash, which is not in the repos (be careful installing a package such as ubuntu-restricted-extras, which forces 32-bit flash). Click the FlashAid link in my sig for more info.

---

### Post by LFS-Nr-3305 on 2011-01-07
> **oldos2er said:**
> If you have hardware for which the manufacturer only supplies 32-bit drivers, that's one possible problem.

Also if you're going to run 64-bit Ubuntu with flash, you should install 64-bit flash, which is not in the repos (be careful installing a package such as ubuntu-restricted-extras, which forces 32-bit flash). Click the FlashAid link in my sig for more info.

You are correct. What I have is a firefox plugin
flash 10.3 d162, (10.3.162.29) which I seem to remember having installed not from those repositories which were enabled or installed in my Ubuntu originally.

Never had a problem installing or using it.

---

### Post by jepong on 2011-02-13
for 64bit flash... i suggest to add _ppa:sevenmachines/flash_ in you repository and install _flashplugin64-installer_.

---

