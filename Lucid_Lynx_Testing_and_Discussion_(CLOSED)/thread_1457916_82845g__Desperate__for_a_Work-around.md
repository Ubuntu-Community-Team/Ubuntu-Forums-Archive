---
title: "82845g _Desperate_ for a Work-around"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by purgatori on 2010-04-19
Ok, I have pretty much tried everything as far as fiddling around with my xorg.conf and disabling things like acpi and KMS goes, and I am STILL experiencing (seemingly) random crashes of the xserver thanks to this unholy accelerator/driver. I had a similar problem with Karmic, except that X used to lock, instead of crash... but the crashing is more frequent than the locks ever were, and it is seriously interfering with my ability to work :( 

I have filed a bug for this, and have followed the bug reports and forum threads of people who have encountered similar/identical problems with this piece of hardware, and have yet to come across anything close to a guaranteed workaround, other than using vesa. This problem seems to be extremely widespread, across multiple Linux distributions, so I'm sure that there will be a *fix* eventually, but for the moment, I just want a workaround.

Vesa would be fine, except the resolution is unacceptably low, and causes my display to get all distorted and funky. Are there other rendering methods/drivers I can use besides vesa and intel, and still get a decent X display? Or does anyone know if there is a certain version of the Intel driver which is known to be free of these problems (and hopefully, doesn't have too many others)? In other words, is there something I can do which isn't *too* radicaly, and which will get my system back to a usable state? 

Any help would be *greatly* appreciated.

---

### Post by Reiger on 2010-04-19
If VESA is acceptable and you have a half-decent external monitor you can fix the problem via the monitor. Try configure it (the monitor) through the OSD and see if you can set either resolution or preferably aspect-ratio/scaling settings to get a 1:1 desktop:monitor-resolution.

The net effect should be that -for the time being- you run e.g. a 1600x1200 desktop rather than a 1920x1200 one; so it uses only part of the monitor (black bands on the sides).

---

### Post by purgatori on 2010-04-19
> **Reiger said:**
> If VESA is acceptable and you have a half-decent external monitor you can fix the problem via the monitor. Try configure it (the monitor) through the OSD and see if you can set either resolution or preferably aspect-ratio/scaling settings to get a 1:1 desktop:monitor-resolution.

The net effect should be that -for the time being- you run e.g. a 1600x1200 desktop rather than a 1920x1200 one; so it uses only part of the monitor (black bands on the sides).

I have an old CRT, which doesn't really posses that sort of functionality, afaik.

---

### Post by dino99 on 2010-04-19
just found that thread, maybe you can grab some info:

[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/the-dreaded-82845g-intel-integrated-graphics-does-any-linux-work-with-it-802465/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/the-dreaded-82845g-intel-integrated-graphics-does-any-linux-work-with-it-802465/)

---

### Post by RJQ on 2010-04-19
For me there is only two options (call them work-around or not) is either live with the crashes or downgrade the Ubuntu version all the way to the last one that was working fine, believe me, I been following this for two years now with no avail, and honestly I don't think there is going to be any fix, nvidia and ati are the ones in favor now at some degree, and this is a linux-xorg wide problem, change in distros make no difference, for my intel card 2008 is the last time it worked. ubuntu 10.04 in my machine is little more stable (crashing fewer times) but not near 8.04 (rock solid) and since this is a matter of luck (depending when, where and how your card was made) good luck to you.

---

### Post by purgatori on 2010-04-19
> **dino99 said:**
> just found that thread, maybe you can grab some info:

[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/the-dreaded-82845g-intel-integrated-graphics-does-any-linux-work-with-it-802465/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/the-dreaded-82845g-intel-integrated-graphics-does-any-linux-work-with-it-802465/)

Thankyou, but I have already looked over this thread, and didn't find any viable solutions for my problem contained therein :(

[quote=RJQ]For me there is only two options (call them work-around or not) is either live with the crashes or downgrade the Ubuntu version all the way to the last one that was working fine, believe me, I been following this for two years now with no avail, and honestly I don't think there is going to be any fix, nvidia and ati are the ones in favor now at some degree, and this is a linux-xorg wide problem, change in distros make no difference, for my intel card 2008 is the last time it worked. ubuntu 10.04 in my machine is little more stable (crashing fewer times) but not near 8.04 (rock solid) and since this is a matter of luck (depending when, where and how your card was made) good luck to you.[/quote]

Two years... wow. That certainly is not encouraging. What I ended up doing was using this ppa: [https://launchpad.net/:~brian-rogers/+archive/graphics-testing](https://launchpad.net/:~brian-rogers/+archive/graphics-testing) -- to roll downgrade xorg-video-intel and libdrm* to, I believe, Jaunty versions. This seems to have fixed the problem for me (although I had to spend some time tweaking xorg to compensate for the performance issues that came along with this drive). Not a great solution, but certainly better for me than downgrading the whole distro, or using vesa. 

Just in case they do end up fixing this problem at some point, can you advise me as to where I could go to track whatever progress is made in that direction?

---

### Post by RJQ on 2010-04-20
I did the downgrade of the driver too in karmic and to me was the same as using vesa, sloppy performance, but again you may find out already that some people are very please with their machines and intel cards, this is definitely a matter of luck, some got their machines back to normal with new or cutting edge drivers, others not, there are some articles all around the web, but nothing for sure that works for everyone, any way do not give up, you may find that the drivers start working again, if the downgrading of the driver works for you stick to it, there is pleny of bugs also filed in every distro quite tiring to follow, I am sorry if I cant point to you any in particular is been a while since I give up in that direction. in launchpad last I check no real fix is been achieved and is currently active in lucid. may be is time to convert this old machine of mine in a huge dvd player...

Again if you keep Ubuntu look in Launchpad for the Intel problems to keep track of the progress, good luck.

---

