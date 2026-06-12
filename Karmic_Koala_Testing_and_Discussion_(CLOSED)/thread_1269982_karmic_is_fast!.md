---
title: "karmic is fast!"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oboedad55 on 2009-09-19
I just booted up the LiveCD of alpha 6 and it runs extremely fast on my ancient P4 desktop. I think I'm gonna install it on an extra partition and give it a whirl. Congrats to the whole team, it looks like a winner!


Jon

---

### Post by amauk on 2009-09-19
There's been huge improvements in the booting process, from Ubuntu (with the conversion of init scripts to upstart's event-driven system) and from upstream (kernel mostly)

---

### Post by oboedad55 on 2009-09-19
I've just been fussing with firefox mainly, which seems quite zippy. Once I install add-ons it may slow down, but for the moment it's quite fast.

---

### Post by nhasian on 2009-09-19
it was my understanding that the software to speedup the boot process wasnt going to be introduced to Karmic until the Beta release?

---

### Post by Luca_turicci on 2009-09-19
Well, they added it on the 6th alpha, it's faster.

But!! when i installed it and did some updates, it shows a lot of proccesses at boot time.

Also, i'm not sure but, when i booted tonight, there was a new (and awesome) splash screen for ubuntu, i'm using a bisigi theme, i've used it for weeks and have never seen that screen before...

---

### Post by talkingwires on 2009-09-19
They've been working on boot speed as a major feature of Karmic (and, to some extent, the previous release), so the foundations are there. There *are* more improvements in the works, which you can test via a developer's PPA (sorry, I don't remember the link), that are set to land before the Beta. So, if you're installing Alpha 6, you will notice a reduced time to boot, but if everything goes according to plan, the Beta will be even faster.

Of course, you should expect breakage as these updates drop, which last I heard, should be after this weekend. Karmic's been fairly stable until the past two weeks. Expect more turbulence as the last major changes get merged before the Beta Freeze.

It's kinda strange, as usually the breakage in Ubuntu's development cycle occurs in the middle; after the fifth Alpha, it's usually smooth sailing. But, Karmic is shaping up to be a very solid release, so the more people testing it, the better.

---

### Post by Amaranth on 2009-09-19
The changes made to the boot are coming now because we're in Feature Freeze so the developer working on it doesn't have to worry about the system changing out from under him. He started working on it and uploading the changes soon after Feature Freeze and the work will continue up until Beta Freeze. However, I think we've seen most of the speedups we're going to get this cycle. The real focus is the 10 second boot (to the desktop) of the next cycle.

---

### Post by Invincible23 on 2009-09-19
> **oboedad55 said:**
> I just booted up the LiveCD of alpha 6 and it runs extremely fast on my ancient P4 desktop. I think I'm gonna install it on an extra partition and give it a whirl. Congrats to the whole team, it looks like a winner!


Jon

I'm running karmic on an ancient PIII :) Karmic indeed is real fast

---

### Post by Sashin on 2009-09-19
Are you talking about simply booting karmic or actually using it?

Is it noticeable faster than jaunty?

---

### Post by oboedad55 on 2009-09-19
> **Sashin said:**
> Are you talking about simply booting karmic or actually using it?

Is it noticeable faster than jaunty?

I'm just talking about the LiveCD. I don't know what the installed system is like, although others may comment. If you're thinking of "upgrading" remember karmic is still in alpha testing.

---

### Post by Copernicus1234 on 2009-09-19
It doesnt seem to work when attempting to install it in Virtual Box. Alpha 5 worked fine but not alpha 6. The install goes fine, but after reboot the system doesnt boot up and just ends up in some kind of loop.

---

### Post by Marat89 on 2009-09-19
I had the same problems.
To solve it, I abbort the session and restart the box. Then it boots fine.

---

### Post by damarusama on 2009-09-19
OMG yes karmic is fast, I am on a eeepc 701 and is getting better and better, now with full on compiz, desktop effect, mkv movie plays faster even! It's crazy! I can now project on the wall animation of fractal while playing on my synth psychedelic music ! and everything run smoothly ! Finally a nice desktop OS that evolve!

:popcorn:

---

### Post by Compintuit on 2009-09-19
If Karmic can ever pull off a 10-sec boot, I may just eat my hat. I'm on a modern system, too - 1.86GHZ,1GB (800MHZ)RAM, intel 128MB integrated graphics. *My BIOS loads in 10.1 seconds.*So, yeah, I doubt it will ever get there.

---

### Post by oboedad55 on 2009-09-19
> **Compintuit said:**
> If Karmic can ever pull off a 10-sec boot, I may just eat my hat. I'm on a modern system, too - 1.86GHZ,1GB (800MHZ)RAM, intel 128MB integrated graphics. *My BIOS loads in 10.1 seconds.*So, yeah, I doubt it will ever get there.

I'm not holding my breath for ten seconds either. Actually now that I have karmic installed it's more sluggish on my system than jaunty, and that's with ext4 on both. Go figure.

---

### Post by m-tarek on 2009-09-19
I had a big problem with jaunty booting, The system needed a minute to boot.
but with karmic now, that problem's gone=D>, but it still slow,it needs to 30 seconds.:confused:
and my laptop is core2duo 2.16GHZ, 3GB of Ram 
and no body here or in launchpad could solve [this problem]("http://ubuntuforums.org/showthread.php?t=1269015").](*,)

---

### Post by inportb on 2009-09-19
> **Compintuit said:**
> If Karmic can ever pull off a 10-sec boot, I may just eat my hat. I'm on a modern system, too - 1.86GHZ,1GB (800MHZ)RAM, intel 128MB integrated graphics. *My BIOS loads in 10.1 seconds.*So, yeah, I doubt it will ever get there.

You are? Betcha can't run Crysis :)
btw, the 10 second boot is supposed to be from GRUB to desktop. I don't think anyone could control what your BIOS's doing, unless you install coreboot.

---

### Post by andrewabc on 2009-09-19
> **Compintuit said:**
> If Karmic can ever pull off a 10-sec boot, I may just eat my hat. I'm on a modern system, too - 1.86GHZ,1GB (800MHZ)RAM, intel 128MB integrated graphics. *My BIOS loads in 10.1 seconds.*So, yeah, I doubt it will ever get there.

The 10 second boot is for Karmic+1 (10.04).
I really wish people would stop associating it with 9.10.

---

### Post by camper365 on 2009-09-19
Mine actually takes a while to boot (compared to 10 seconds) If the beta thing is true, then I'm really looking foward to it. Only 11 days to go...

---

### Post by linusr on 2009-09-20
My laptop finally plays well with Ubuntu.

Is it nvidia driver which made the change or ext4?

---

### Post by linusr on 2009-09-20
My laptop finally plays well with Ubuntu.

Is it nvidia driver which made the change or ext4?

---

### Post by oboedad55 on 2009-09-20
> **linusr said:**
> My laptop finally plays well with Ubuntu.

Is it nvidia driver which made the change or ext4?

Wouldn't be the file system. Must be the new driver.

---

### Post by froggyswamp on 2009-09-20
Kernel 2.6.31 to speed up Linux desktop

[http://www.techworld.com.au/article/317416/kernel_2_6_31_speed_up_linux_desktop](http://www.techworld.com.au/article/317416/kernel_2_6_31_speed_up_linux_desktop)

---

### Post by wfp on 2009-09-20
I do not see any speed increase what so ever so far on this alpha. Actually karmic was about 5 seconds faster on boot than koala. Totem is still constantly crashing, and so is vlc. Firefox 3.5 on my box is a lot slower than firefox 3.0 on karmic. Where still at alpha, but no speed increase here. Not trying to be negative but thats how it's been so far for me.

---

### Post by oboedad55 on 2009-09-20
> **wfp said:**
> I do not see any speed increase what so ever so far on this alpha. Actually karmic was about 5 seconds faster on boot than koala. Totem is still constantly crashing, and so is vlc. Firefox 3.5 on my box is a lot slower than firefox 3.0 on karmic. Where still at alpha, but no speed increase here. Not trying to be negative but thats how it's been so far for me.

You mean jaunty is faster, right? The automount bug was enough to do me for now.

---

### Post by linusr on 2009-09-20
> **oboedad55 said:**
> Wouldn't be the file system. Must be the new driver.

had to be, nvidia drivers was an major blocking issue

hope nvidia delivers better drivers or open source it

---

### Post by Ric_NYC on 2009-09-20
I don't think it boots faster than Jaunty.
The last alpha has "3 boots" after something was broken days ago...

It starts with a "verbose mode", then it shows xplash , then there's the login screen... after that there's another xplash!

---

### Post by andrewabc on 2009-09-20
> **Ric_NYC said:**
> I don't think it boots faster than Jaunty.
The last alpha has "3 boots" after something was broken days ago...

It starts with a "verbose mode", then it shows xplash , then there's the login screen... after that there's another xplash!

Yep, it is broken at the moment, but they will be fixing it.
I was surprised when booting alpha 6 liveusb to see text when booting, then the xsplash (throbber is broken), then I heard ubuntu login sound while xsplash played for several more seconds, then desktop showed up fully loaded.

---

### Post by TheStroj on 2009-09-20
Well, I didn't try carmic yet, but Ubuntu 9.04 boots really fast by me. It takes like 15 seconds from PC power on, to Desktop on Ubuntu 9.04 (excluding the time i need to press "Enter" to boot Ubuntu). From Dual Boot to Ubuntu Desktop it takes like 7 seconds.

---

### Post by nhasian on 2009-09-21
by modern system do you mean 4 years old?  :-P

> **Compintuit said:**
> I'm on a modern system, too - 1.86GHZ,1GB (800MHZ)RAM, intel 128MB integrated graphics. *My BIOS loads in 10.1 seconds.*So, yeah, I doubt it will ever get there.

---

### Post by Borjs85 on 2009-09-21
I suposse it's because the new driver for the intel 945g, but my EEEPC 901 it's faster than every distro I've tried and Windows XP. Even flash videos are working well. I can't believe it, Karmic is a very promising release

---

