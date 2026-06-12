---
title: "Install on HP Dv6646"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by stlcoptony on 2007-12-11
Ok, I wish I were writing this from my new computer, but I cannot get it to install. I have the HP dv 6646us, whose specs are listed [here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01163905&lc=en&cc=us&dlc=en&product=3552675&rule=44703&lang=en") and on circuit city's site [here]("http://www.circuitcity.com/ssm/HP-Pavilion-15-4-Widescreen-Laptop-PC-DV6646US/sem/rpsm/oid/191730/catOid/-12963/rpem/ccd/productDetail.do").
I tried the 7.10 live cd and could not get a gui to come up. On a second try I got the message that ubuntu  could not detect my monitor or graphics card. I tried configuring it by selecting LCD at 1280x800 and nvidia 7 series driver (pc has a nvidia geforce go 7150). I also tried sabayon's live dvd, which also produced some funny results. After I selected start or install sabayon from the live dvd menu, it would hang until I ejected the dvd and re-inserted it. I believe I could get sabayon installed but I would prefer ubuntu if at all possible. I read somewhere that this nvidia card is not yet supported? Anyway, if anyone can help it would be greatly appreciated. I really want this laptop to be linux only.

thanks,
tony

---

### Post by Keyper7 on 2007-12-11
Welcome to [our club]("http://ubuntuforums.org/showthread.php?t=582220"), my friend.

The first I'd suggest is trying to install [Feisty]("http://releases.ubuntu.com/7.04/").

---

### Post by stlcoptony on 2007-12-11
Holy crap, how did I miss a 24 page thread about probs with HP laptops??? Well, when are our club meetings? Will feisty work with the nvidia card? 

thanks

---

### Post by Keyper7 on 2007-12-11
I don't know if the open nv driver supports your board, but try installing the [latest beta proprietary driver]("http://www.nvnews.net/vbulletin/showthread.php?t=102509") and see how it goes.

---

### Post by Pumalite on 2007-12-11
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by pieisgood4589 on 2007-12-11
Yup, yup yup. Yup. Yummy.......

---

### Post by stlcoptony on 2007-12-11
Still no luck with getting ubuntu installed. I tried to edit xorg.conf, but I cannot figure out how to generate a modeline for a notebook monitor (I cannot find the specs anywhere!). Anyway I'm now trying every distro .ISO I have (and burning more...). If anyone could tell me either what I lose by installing feisty instead or how to install gutsy I would be overjoyed!!

thanks

---

### Post by djodjoman on 2007-12-12
Wow,

I have exactrly the same laptop hp dv6646us and had the same problems.
And I don´t know if this is the case, but i had a lot of difficult finding someone who had the same problems. Just found few related topics that wouldn´t help me at all.

The first distro i tried was fedora 7, which had strange problems when booting from cd or after installed as well, i do not recomend ... I believe should be something like sabayon. 

Then i tried UBUNTU as well and i had similar problemas, maybe the same, but it is been a while already ...
About UBUNTU i found someone has it installed, but did it through alternate install, after some dificulty.

Well, here´s the funniest thing, i could install fedora 8 and it is working ..... but when booting fedora i would gete errors message saying it couldn´t find any volume groups ... A very very strange solution I found was putting a 12 seconds delay before it start booting fedora, and tha problem gos away. But if you do not wait those 12 secs, then the erro will apear.

I´m convinced that erro is a kernel incompatibility. I´ll soon try to write to fedora developers and whoever to ask for them to try to fix that for future kernel updates or for the next distros.

Another issue about FEDORA 8 is that the hibernate function does not work, do not use it, or you will take a while making your FEDORA 8 work again.

An reinforce i got that it is a kernel incompatibility is that when i get some update, when rebooting, some strange things may appear on the screen.

And you will have to use ndiswrapper to get your wireless working, if possible, do just after a kernel update ... When you update your kernel and you have the wireless driver already working, it breaks down, and i´m still loking for a away to fix, as even reinstalling didn´t work, even after i tried removing some file.

And of course, get the nvidia 7 series driver at nvidia.com

Compiz won´t work thoug, but i don´t need it anyway!

Anyway, it seems the next release of ubuntu is a long term ... My friend told me it should be better, more stable and that maybe thoses issues won´t come up. As soon as it is released i´ll try, cos eventhoug the way it is is working fine, it is not perfect as it should be ... Sometimes you get really scared about what it is going on ...

Anyway, i hope you´ve done the recovery disk for your notebook, and that this may help you!

---

### Post by djodjoman on 2007-12-12
I forgot to mention, it is just funny that i when having those problems did the same as you, started downloading all distro hoping tha some would work fine!!!

I got mandriva, opensuse, debian, sabayon  but didn´t tried yet ... as FEDORA 8 is working ... I would also try gentoo, i´m still think tha maybe compiling the kernel would solve those problems ...

That is all now! =)

---

### Post by djodjoman on 2007-12-12
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				And i just found this, u could try, i didn´t try yet ....
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by stlcoptony on 2007-12-12
Just in case this helps you, Sabayon works perfectly out of the box except for wireless. I looking into that right now (should be studying for that last final, but my brain is now officially fried....)

thanks

---

### Post by djodjoman on 2007-12-12
who knows? I am really up trying to get a nice working distro for this notebook ... what about the funny things you were getting with sabayon? Has it stopped?

---

### Post by djodjoman on 2007-12-12
An wich version did u install?

---

### Post by stlcoptony on 2007-12-12
yeah, I used the sabayon 3.4f 64 bit dvd iso. No probs except the wireless, which I do not know how to fix on a gentoo/kde distro. I am now back with vista. I don't really mind vista (as long as it's on a capable system),but I just wanted to have a linux-only laptop to play with.... Seems I bought the wrong one, for now..

If anyone knows how to explain to me how to get sabayon working perfectly on this hp laptop, please let me know and windows will be gone again!

thanks

---

### Post by sergiom99 on 2008-01-05
I got my DV6646us working without any problems. I used the Kubuntu Gutsy 32bit alternate CD and the followed some of the instructions from this excellent post: 
[http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)
(make sure to read the whole post... always)
and now works like a charm sound, video, wireless, etc.

---

