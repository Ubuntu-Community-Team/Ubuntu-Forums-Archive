---
title: "Does Karmic boot faster than Jaunty?"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by BarisBlaq on 2009-10-28
I was thinking it would, but does not for me =(

I know the 10 seconds boot-up is meant for Lucid and not Karmic, but still, I'm disillusioned with Karmic's performance.

With Jaunty, I had a 35 second boot from bios screen to login screen. I have a core 2 duo laptop.

I fresh installed Karmic RC, and replicated the same minor tweaks I had with Jaunty, but it boots around 50 secs (again bios screen to login).

Anyone with better/similar/worse experience? Any tips? 

Thanks!

---

### Post by jward3010 on 2009-10-28
I'm finding the same including a long enough move from login screen to Desktop, although I find Karmic nippy enough when loaded completely.

To conclude, Jaunty had the fastest boot times I know of. This is a regression but they are trying out some new technology, like encryptable disks and home folders and loading new modules for improved drivers, so it might be a while before this "new" stuff is refined.

Also, I have no idea how to do a profiled boot anymore, sticking "profile" at the end of the kernel line during GRUB stage donsn't seem to do anything. That might improve performance if I could do it.

---

### Post by phillw on 2009-10-28
what was the boot time before your 'tweeks' ?

Phill.

---

### Post by BarisBlaq on 2009-10-28
Yes, the time between login screen to desktop is also longer apparently, but I had never timed it on Jaunty (as it was quite short lol)..

Still, I don't have encryption enabled.. I kinda feel Grub2 also has some part in this regression, it seems getting to xserver takes longer.. Just my opinion of course, I'm no expert.

---

### Post by BarisBlaq on 2009-10-28
sorry phillw, just saw your post after I posted mt reply.

it was about 40 secs I guess, because I recall the tweeks didnt make much difference.. and what I mean by tweaks is disabling start-up apps I dont use (bluetooth, cups, etc), profiling the kernel, and setting **CONCURRENCY=shell **in /etc/init.d/rc

edit: reading [jward3010]("http://ubuntuforums.org/member.php?u=497188")'s edit, I'm not sure if profiling even improves anything now..

---

### Post by P4man on 2009-10-28
I have to agree. They took away our gdm login screen and usplash to improve boot times, and now we have featureless gdm login and xplash and worse boot times. Perhaps the benefits will show up later, but at this point I dont see much in Karmic that excites me.

---

### Post by BarisBlaq on 2009-10-28
> **P4man said:**
> They took away our gdm login screen

Yes! There were so many fine clever artwork at deviantart..

=(

---

### Post by scouser73 on 2009-10-28
With Jaunty I had a boot time of 21 seconds [all up and running], now I've done a fresh install of Karmic beta it's risen to 1.5 minutes.  I have stopped a few processes from starting at but but it's hardly made an impact.

---

### Post by DeMus on 2009-10-28
I use Jaunty 64 and I have 31 seconds between the end of Grub and the moment my desktop picture appears. Then it's still a few seconds to get all items in the panels. I use auto-login so I have no log-in screen.
Is that fast? I have no idea. I don't boot so often, the computer is mostly running 24 hours per day.
I am thinking of installing Karmic, but hearing the negative things around here i wonder if I should do that.
Well, I still have until tomorrow to decide. ;)

---

### Post by BarisBlaq on 2009-10-28
> **DeMus said:**
> I use Jaunty 64 and I have 31 seconds between the end of Grub and the moment my desktop picture appears. Then it's still a few seconds to get all items in the panels. I use auto-login so I have no log-in screen.
Is that fast? I have no idea. I don't boot so often, the computer is mostly running 24 hours per day.

I'm not exactly sure of "end of Grub". I time the boot up from appearance of bios screen to the login screen. But as jward3010 said, it also seems to take longer in Karmic from login to desktop, about 5-10 secs in my experience, vs 1-3 secs in Jaunty.

I do boot quite often cause I have a laptop. Your mileage may vary =P

I'd still love to hear more comparisons vs Jaunty.. And any suggestions to make the boot up faster
=)

---

### Post by jward3010 on 2009-10-28
> **DeMus said:**
> I use Jaunty 64 and I have 31 seconds between the end of Grub and the moment my desktop picture appears. Then it's still a few seconds to get all items in the panels. I use auto-login so I have no log-in screen.
Is that fast? I have no idea. I don't boot so often, the computer is mostly running 24 hours per day.

31 seconds sounds not great to be fair, also keep in mind that every BIOS loads differently and hence some take longer than others.
> **DeMus said:**
> I am thinking of installing Karmic, but hearing the negative things around here i wonder if I should do that.
Well, I still have until tomorrow to decide. ;)

I find very few negative things with Karmic, mainly fantastic improvements actually, very few regressions. In terms of boot times it has slowed, no doubt. In terms of general peformance for example on the desktop it's still very nifty, in fact those of you with Intel graphics should notice a big change from Jaunty to Karmic in this regard.

---

### Post by tuahaa on 2009-10-28
Boot times are *slightly* slower in comparison to 9.04 on my Laptop. KDE is slower to start up, but thats not 9.10's fault.

PS. I don't have any other OS installed.

---

### Post by grizato on 2009-10-28
Why don't yo try skinning the unused fat n the Koala?

The ovious question:(

---

### Post by QIII on 2009-10-28
My *impression *is that it boots faster all the way to the desktop, but I don't have any empirical data.

Unfortunately, I've gone all Karmic on all my machines, so I can't compare.  I can time it tonight.

Mileage may vary.  My primary machine is a quad core with a wheel barrow full of RAM, but I'll time that.

I have an old P4 machine with 750MB to check out, too.

---

### Post by justborn on 2009-10-28
> **DeMus said:**
> I use Jaunty 64 and I have 31 seconds between the end of Grub and the moment my desktop picture appears. Then it's still a few seconds to get all items in the panels. I use auto-login so I have no log-in screen.
Is that fast? I have no idea. I don't boot so often, the computer is mostly running 24 hours per day.
I am thinking of installing Karmic, but hearing the negative things around here i wonder if I should do that.
Well, I still have until tomorrow to decide. ;)

i do agree that karmic takes a longer time to boot,but it getting better day by day,(i.e beta to rc,and so on.... ).its a bit better.

but when it comes to the question of not swithing to karmic just because of the slow boot-up ,might be a bad idea.karmic has a better kernel and many great features in comparison to jaunty.and u said that, u boot only sometimes,so even if it takes 1.5(according to scouser73) min ,its not a big deal.karmic already seems to rock for me.:)

---

