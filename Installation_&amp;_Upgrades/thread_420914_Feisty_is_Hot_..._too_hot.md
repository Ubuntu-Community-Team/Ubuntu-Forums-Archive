---
title: "Feisty is Hot ... too hot"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by afaflix on 2007-04-24
I currently own a Dell XPS Laptop which has a NVIDIA card in it.

on Ubuntu 6.10 I ran Beryl for which I had to scramble around for the correct drivers. Envy helped me out there.  Then 7.04, Feisty Fawn comes out.   Somehow the Envy installed drivers interfered with the push-button setup of Ubuntu and I had a lot of error messages scroll by. But it ran.
Yet, I wasn't quite happy with it, knowing that something just wasn't right and soon enough I found that when I play little flashgame the cooling fans start to kick in soon and shortly after the computer shuts down in a very rapid fashion.

I reinstalled since twice from scratch (including format just to be sure) same thing.
Edgy works, Feisty overheats.  it even overheats if I import my music collection into amarok ... or my mailboxes into kmail. 
youtube is a killer ... any video for that matter.

btw .. this is not a "bug" as such that it shuts down because it takes a wrong reading .. it's overheating and the shut-down is justified.

I can run the same flash games, or videos in 6.10 or windows xp, on the same machine without problems.

vmlinuz-2.6.20-15-generic  is the problem child as far as I can deduct it.  it matters not if I enable or disable 'desktop effects' or 'restricted drivers'.

Envy doesn't seem to like Feisty at all, but I'm sure that will change.

Am I the only one with this problem?

So long
                             Afaflix

---

### Post by jlx on 2007-04-24
You are not the only one. I have same problem. Nvidia card XFX 6800 GT and PIV 3Ghz. Suddenly pc started reseting randomly. I thought it was the power source or maybe the video card. I decided to buy a new power source until I read the posts in the forum.
If I start Ubuntu Feisty when resets I check cpu temperature in BIOS and it's about 58ºC. If after Ubuntu resets I enter windows, it resets again because CPU it's still too hot. 
If I shutdown PC and wait some minutes, then I enter windows first and everything it's working. I have no resets and I can play C&C3 or PES 6. When I check CPU temperature this time I get 52ºC.
Feisty Fawn it's really overheating CPU. I can't use my PC (I have to work with my laptop) until someone finds the solution for that critical bug.

---

### Post by sloggerkhan on 2007-04-24
I haven't overheated, but Feisty on my comp seems to have introduced a lot more temperature variability. My laptop's CPU will hit 54 deg. C or so on occasion for seemingly no reason. Used to it staying under 52 deg. C.
Haven't had it overheat to shutdown point or anything, though. Once it hits such a temp it usually cools down in a moment to a minute by 1-3 degrees.

---

### Post by mgvbstar on 2007-04-24
Yeah, I get same problem.  I have ace aspire 5672 notebook (core duo 1.66, ati mobility x1400).  Before feisty temp was about 45-50 C but with feisty it sits at 55 C when idle and up to 60 when not idle. It's too hot, my hands sweat when I type :(

---

### Post by mgvbstar on 2007-04-24
Is it possible to downgrade the kernel until it gets fixed? If so, how would I go about doing that?

---

### Post by jlx on 2007-04-25
I discard overheating. System resets even at grub menu. This morning I had 4 or 5 resets and the temperature was about 50ºC. I start thinking again about power source or nvidia driver. I'm trying nvidia-glx-new.

---

### Post by rhardie on 2007-04-25
I have recently re-loaded my OS from the 7.04 Beta because I wanted to run in full 64 bit mode on my AMD 64 Athlon.  I downloaded the ISO onto a CD and formatted and reinstalled.

Since the new OS install, I notice that I can leave my work station for a couple of hours and upon return, I am required to log in my user name as well as password.  Next, I have a blank screen and then a white square (3X3) is in the upper left of the monitor.

I reboot to get normal operation.

The things I see different from my old install is:

1. Beta to full release
2. 32 bit to 64 bit

Any ideas?  I'm going to post this elsewhere too.

RHardie
Austin, TX

---

### Post by jlx on 2007-04-25
By now I have no resets (cross my fingers). I'm going to leave the system up playing a movie or something. 
The last thing I've thought was that default Feisty nvidia drivers resets the system. That reset makes my nvidia card crazy and the next times it resets randomly. The main causes for resets are video card drivers, power source and God playing dice, maybe. I don't know what to think. I'm running out of theories. Any ideas?

---

### Post by jlx on 2007-04-26
Finally I've come to the conclusion that my problem is the power source. On saturday I'll be buying a new one. If that doesn't solve the resets I'll have to buy a new motherboard.

---

### Post by Ripfox on 2007-05-04
I have officially decided to downgrade to Edgy...my lappy is brand new hp dv6000 and it's TOO hot under Feisty.

---

### Post by gnuts on 2007-05-06
I am running my dual core turion64 at powersave mode all the time because of heat problems keeps it at about 56C. I hear the next kernel version helps with these problems, maybe it will be backported to feisty soon?

---

### Post by kaede on 2007-05-11
> **ripfox said:**
> I have officially decided to downgrade to Edgy...my lappy is brand new hp dv6000 and it's TOO hot under Feisty.
is there any solution beside downgrading to edgy ? coz my pcmcia wifi not working very well in edgy. sighh yesterday my notebook reach 72 degree. wonder why? :(

---

### Post by bradmayne on 2007-06-22
you guys are makin me nervous!!  I just overheated an old emachine and my mom FREAKED OUT!! I could really care less cuz the the thing was a POS and my mom has a brand new hp pavilion with an AMD dual (sweet) and I got a brand new toshiba satellite a135 s4527 (killer) but with this talk of overheating due to feisty (im getting a BIOS error now on my lappy)  i'm wonderin if i should be going back to edgy for awhile!  Dumb question now but is there a way to roll back to 2.16-10?  And how do the developers now of these critical bugs? Let me know whats up guys/gals peace out!!

---

### Post by sloggerkhan on 2007-06-22
my machine has settled down. I think there've been a couple kernel updates that might've helped.

---

### Post by bluknight on 2007-06-23
> **mgvbstar said:**
> Is it possible to downgrade the kernel until it gets fixed? If so, how would I go about doing that?

I can only run Feisty with the Edgy kernel 2.6.17-11 and I read that 2.6.20-15 has bugs (?). When I upgrade to 2.6.20-16.29 Feisty hangs on boot. I can tell you how I downgrade my Feisty kernel manually. See

[http://ubuntuforums.org/showthread.php?t=450246&page=2](http://ubuntuforums.org/showthread.php?t=450246&page=2)

But can someone tell me how to upgrade my running 2.6.17-11 to a cool, Feisty bootable kernel?

---

### Post by afaflix on 2007-07-31
Ok ... I have lived with my room heater (aka laptop) for a while now.

It was 3 days ago when I decided to install xubuntu gutsy tribe 3
I created an install image on a USB stick and I am a happy camper ever since.

I ran some video applications while in the background I had amarok import a mp3 library ... either one of those tasks by themself was able to raise the room temperature before.

Not a problem anymore.

so for those still plagued by heat issues:  whatever it was, they fixed it.

Cheers guys.


and thanks

---

### Post by olavjunior on 2007-08-23
Ok, I'm kinda freekin out here reading this thread! I have a hp dv2130 and after installing feisty I've been bothered with fan-noice. I hadn't thought much about it before, and now it hit me that I bouth a new laptop just to get rid of fan noice! So I got the cpu-sensor applets on the bar, and when my cpu is cold it's 65C andwhen it's hot it easily reaches 85C!!! It haven't shut down jet though, and my fans  go at slow speed when it's under 70C. 

What shall I do? install a beta of Gutsy? Is that stable? Or should I downgrade? Fck!

EDIT: hahaha, it seems like the good old fan blow out -trick did the trick! :) I thought my laptop was to new to have collected much dust, but I was wrong! (gotta start cleaning more :s ) Now the temp lie around 55-60C on normal load, and starts running for a few secs when cpu-temp gets over 60C it seems. NICE! It's no problem with a cpu on 58C is it?? I can't think so when mine in the past month has been on 70-75 :s

---

