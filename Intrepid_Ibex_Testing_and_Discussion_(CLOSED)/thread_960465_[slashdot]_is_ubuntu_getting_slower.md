---
title: "[slashdot] is ubuntu getting slower?"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wizard10000 on 2008-10-27
Interesting /. article.  TFA has benchmarks.

[http://linux.slashdot.org/article.pl?sid=08/10/27/1212214](http://linux.slashdot.org/article.pl?sid=08/10/27/1212214)

And a link to TFA -

[http://www.phoronix.com/vr.php?view=13022](http://www.phoronix.com/vr.php?view=13022)

---

### Post by blazercist on 2008-10-27
I read this article earlier today, it has a lot of valid data and only a few inconsistencies, I am dissapointed, although I haven't found a suitable substitute.  I will continue using Hardy Heron until I can find one.

---

### Post by olskar on 2008-10-27
I am also a bit disappointed.. Getting slower every release used to be Windows thing..

---

### Post by SteveNorman on 2008-10-27
sometimes I worry about the 6 month upgrade. Having a deadline like that means that at the end of 6 months the os is out regardless of whether the bugs really get fixed. Then focus shifts to the next release,, so its possible that known problems get barrel rolled into the next release. I would like it better if they where like,, "we estimate 2 more months till we get it right folks,,keep your shirt on". Or getting a little more gentoo about what packages get loaded (let the person downloading have more customized options). Personally I really liked 7.4, but I hosed it with the automatix debacle. I liked 7.10 as well,, I guess we have the option of loading whatever release we like versus jumping on the new release every 6 months.

---

### Post by fjf on 2008-10-27
I guess thats the price you pay for having a kernel able to work with every piece of hardware out there...

---

### Post by plun on 2008-10-27
> **olskar said:**
> I am also a bit disappointed.. Getting slower every release used to be Windows thing..

Vista "concrete"....:)

There was problem in the beginning with the tool chain, it took a while (pre Alpha 1)

After latest kernels and Gnome 2.24.1 it is rather bad.  :( 

I can see memory runs, like leakage and processes going up and down in CPU.... also networking seems to slow down.

Impossible to "nail" anything and for me its the same as Phoronixs conclusion

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=10](http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=10)

Reschedule....

---

### Post by jfernyhough on 2008-10-27
> **fjf said:**
> I guess thats the price you pay for having a kernel able to work with every piece of hardware out there...Mmm, I've compiled 2.6.28-rc2 using Kernelcheck and it feels quicker. It uses the same settings as those used by the Ubuntu 2.6.27-7 kernel and works in pretty much the same way (it just won't work OOTB for any hardware that requires restricted drivers, plus DKMS breaks).

---

### Post by inportb on 2008-10-27
Sure it's getting slower, and it's because your hardware isn't getting any faster :)

You simply cannot expect an OS to not get slower while it steadily gains features. This should not be a surprise to anyone, or disappointing, for that matter. If you want fast, get damnsmalllinux.

---

### Post by psyke83 on 2008-10-27
> **inportb said:**
> Sure it's getting slower, and it's because your hardware isn't getting any faster :)

You simply cannot expect an OS to not get slower while it steadily gains features. This should not be a surprise to anyone, or disappointing, for that matter. If you want fast, get damnsmalllinux.

Read the article. Several of the tests show a 2x slowdown when comparing 7.04 to 8.10, using the same version of userspace software (e.g. encoding via LAME).

This is not about the increasing complexity of software and the need to buy new hardware.

My guess is that the CFS scheduler plays a big part in these regressions (CFS was introduced with the 2.6.23 kernel, and first seen in Ubuntu via Hardy's 2.6.24 kernel).

Perhaps their test conditions are somewhat flawed, but these results certainly show that some further investigation is necessary.

---

### Post by plun on 2008-10-27
> **jfernyhough said:**
> Mmm, I've compiled 2.6.28-rc2 using Kernelcheck and it feels quicker. It uses the same settings as those used by the Ubuntu 2.6.27-7 kernel and works in pretty much the same way (it just won't work OOTB for any hardware that requires restricted drivers, plus DKMS breaks).

Well

[http://www.nvnews.net/vbulletin/showthread.php?t=121790](http://www.nvnews.net/vbulletin/showthread.php?t=121790)

Message 21 from "zander"...O:)

Instead of running a new kernel it must be possible to find what "hogging" Intrepid for the moment.

Da--ned annoying that something after a while just slows down everything...

---

### Post by paxmark1 on 2008-10-27
as posted previously that is why i went to lenny on my old machine

especially true on Kubuntu

lenny rocks on old equipment and is stable and has a farily new kernel and the new apt's.

I am sticking with Hardy and backports on my first machine.

---

### Post by forcecore on 2008-10-27
I hope that final has serious slowdown bugs fixed, currently this section is quite bad: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=4](http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=4) BUT maybe there is some very small bug what causes it so lets wait 3 days and see.

---

### Post by jfernyhough on 2008-10-27
> **plun said:**
> Well
[http://www.nvnews.net/vbulletin/showthread.php?t=121790](http://www.nvnews.net/vbulletin/showthread.php?t=121790)
Message 21 from "zander"...O:)Sweet!

> 
Instead of running a new kernel it must be possible to find what "hogging" Intrepid for the moment.

Da--ned annoying that something after a while just slows down everything...Try adding elevator=deadline to the GRUB kernel line - certainly on my laptop (and EeePC) this hugely improves responsiveness during disk activity.

---

### Post by marmuta on 2008-10-28
Pulseaudio is hogging cpu for me, is anyone else seeing this?
After a fresh reboot it uses up 10-20% on an otherwise empty desktop with no audio even playing. It only goes down when I "pulseaudio -k; pulseaudio" it in a terminal.

---

### Post by plun on 2008-10-28
> **marmuta said:**
> Pulseaudio is hogging cpu for me, is anyone else seeing this?
After a fresh reboot it uses up 10-20% on an otherwise empty desktop with no audio even playing. It only goes down when I "pulseaudio -k; pulseaudio" it in a terminal.

Yup...but for me it comes after a while playing music.
I can also notice a memory leakage.

Start **top** within the terminal

Especially streamed music such as LastFM breaks it......


Probably nothing to do and Intrepid will be shipped with this. :( 


(the same for both PA 0.9.10 and 0.9.13)

---

### Post by marmuta on 2008-10-28
> **plun said:**
> Yup...but for me it comes after a while playing music.


True, happens to me too sometimes when sound was playing for a while. Other times all audio just goes silent until I restart pa+apps :rolleyes:. 

I'll see if can find a hint about what's causing the slowdowns next time it happens and add to this here bug [#207135]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/207135").

pa aside, Intrepid really feels slow. Evolution, Thunderbird and everything using sqlite like firefox and liferea are sluggish and take little naps every so often.

---

### Post by ronacc on 2008-10-28
Disclaimer : I have run no objective benchmarks so this is purely a subjective observation . I have gutsy , hardy , intrepid and opensuse 10.1 ,all on different drives in the same box and for my " day to day " use Intrepid actualy "feels " faster . I certainly have not seen a 50% slowdown in any of the apps I routinely use , I will admit the I do not game and that my box is severe overkill for what I really use it for .

---

### Post by plun on 2008-10-28
> **ronacc said:**
> Disclaimer : I have run no objective benchmarks so this is purely a subjective observation . I have gutsy , hardy , intrepid and opensuse 10.1 ,all on different drives in the same box and for my " day to day " use Intrepid actualy "feels " faster . I certainly have not seen a 50% slowdown in any of the apps I routinely use , I will admit the I do not game and that my box is severe overkill for what I really use it for .

Take this as a reference case.

- Start Firefox with four tabs

- Start LastFM and a network stream with your favorite music

- Start something else, Openoffice document or just the update manager....

*top" should be running all the time..... something IS wrong..!

---

### Post by billenbois on 2008-10-28
[IMG]http://http://www.phoronix.com/data/img/results/ubuntu_bench_2008/3a.png[/IMG]
[http://www.phoronix.com/data/img/results/ubuntu_bench_2008/3a.png](http://www.phoronix.com/data/img/results/ubuntu_bench_2008/3a.png)

just that graphic alone should tell everyone of you thinking "ah retards, its normal!" that something *is* *going* *wrong*

now that'd be cool if they tested various kernels and stuff to pin it out.

---

### Post by ronacc on 2008-10-28
@ plun  I'll give your test a try , as I said I was giving a purely subjective opinion about what I do day to day , I use Opera instead of FF , never use lastFM ( my "background noise" comes from a radio in another room) and the docs I most often read are either plain text so I use gedit or else pdf's so I use acroread (document viewer has always seemed slow and clunky to me ) . as I noted I don't stress the box much .

@ billenbois  I read TFA and saw that graphic ( and others) and when I get the chance I may download the test suite and toss it at my box just for grins . The slowdown indicated is indeed dismal , infact so dismal I will have to see it for myself to believe it . Their stated test procedures certaily seem valid but the magnitude of the slowdowns does make me wonder .

---

### Post by philinux on 2008-10-28
> **plun said:**
> Take this as a reference case.

- Start Firefox with four tabs

- Start LastFM and a network stream with your favorite music

- Start something else, Openoffice document or just the update manager....

*top" should be running all the time..... something IS wrong..!

Did this and system working fine.

---

### Post by plun on 2008-10-28
> **ronacc said:**
> @ plun  I'll give your test a try , as I said I was giving a purely subjective opinion about what I do day to day , I use Opera instead of FF , never use lastFM ( my "background noise" comes from a radio in another room) and the docs I most often read are either plain text so I use gedit or else pdf's so I use acroread (document viewer has always seemed slow and clunky to me ) . as I noted I don't stress the box much .



Ok.... take a 2 hours compile and test a new kernel :)

I can also see this when I sorting IRC groups....  Freenode got about 4500 groups and it can take minutes to sort and filter.

In the end of Hardy we saw the same and it was Firefox3 sqlite database....in this case it is something different.

Also going up to PA 0.9.13... just for fun..:)

---

### Post by zoomy942 on 2008-10-28
> **plun said:**
> Well

[http://www.nvnews.net/vbulletin/showthread.php?t=121790](http://www.nvnews.net/vbulletin/showthread.php?t=121790)

Message 21 from "zander"...O:)

Instead of running a new kernel it must be possible to find what "hogging" Intrepid for the moment.

Da--ned annoying that something after a while just slows down everything...



thats so awesome seeing nvnews linked here.  im a mod over there.  awesome!

---

### Post by ronacc on 2008-10-28
I don't know what this means as far as any "slowdown" might be concerned but I did notice that a few days back my cpu core temps dropped ~10C , they had been running a little higher than hardy on the same box and now are "normal".

---

### Post by plun on 2008-10-28
> **zoomy942 said:**
> thats so awesome seeing nvnews linked here.  im a mod over there.  awesome!

Ok, nice :)

The challenge for me is streamed music and I give up further checks. 

nVidia and a new kernel was a tricky one... 2.28.RC2 builds OK with vitualization unchecked,  nVidia patch OK and install OK.

But as "jfernyhough" wrote DKMS is broken...

I cannot figure out howto load xorg, it hangs on libglx.so loading...:confused:](*,):^o[-X


(then also Pulseaudio from GIT broke during compile....:redface:)

---

### Post by dabl on 2008-10-28
> **ronacc said:**
> I don't know what this means as far as any "slowdown" might be concerned but I did notice that a few days back my cpu core temps dropped ~10C , they had been running a little higher than hardy on the same box and now are "normal".

Yep, same thing here. My overclocked X6800 was running up near 80 C when I pushed it, in Hardy  :?  Not too pleased with that.  Now it's around 65 - 70 C when busy, and 50s when idling -- much better.  :)

---

### Post by | MM | on 2008-10-28
Hi,

Just another anecdotal data point.

Since Hardy (and now Intrepid) i have noticed many more stutters, and the mouse freezes during heavy io, say, during installing updates or cold starting applications.  This never happened in prior versions.

Everything seems slow to load, firefox and nautilus particularly.

Perhaps one dev cycle should focus on optimising the desktop stack.

---

### Post by jfernyhough on 2008-10-28
> **plun said:**
> Ok, nice :)

The challenge for me is streamed music and I give up further checks. 

nVidia and a new kernel was a tricky one... 2.28.RC2 builds OK with vitualization unchecked,  nVidia patch OK and install OK.

But as "jfernyhough" wrote DKMS is broken...

I cannot figure out howto load xorg, it hangs on libglx.so loading...:confused:](*,):^o[-XSame happened to me. I had to cold reset, then on next boot CTRL-ALT-F1, log in, and run $ sudo nvidia-xconfig. It worked after that.

> PA 0.9.13I installed from a PPA repo (can't remember which) and it was fine, though after a while sound would die. After reinstalling I've been using 0.9.10 and it's been fine so far.

---

### Post by blazercist on 2008-10-28
> **| MM | said:**
> Hi,

Just another anecdotal data point.

Since Hardy (and now Intrepid) i have noticed many more stutters, and the mouse freezes during heavy io, say, during installing updates or cold starting applications.  This never happened in prior versions.

Everything seems slow to load, firefox and nautilus particularly.

Perhaps one dev cycle should focus on optimising the desktop stack.

I agree completely.

---

### Post by plun on 2008-10-28
> **jfernyhough said:**
> Same happened to me. I had to cold reset, then on next boot CTRL-ALT-F1, log in, and run $ sudo nvidia-xconfig. It worked after that.

I installed from a PPA repo (can't remember which) and it was fine, though after a while sound would die. After reinstalling I've been using 0.9.10 and it's been fine so far.

Well, I tried exactly that, did you uninstall 177.80  (non patched driver ? )

PA...  with 0.9.10 I can see CPU runs during LastFM sessions, 0.9.13 crashes...therefore I went to GIT. :^o

Just for Fun...always learns something new out of failures..:) 

Everything will be SRUs so it just to test...

---

### Post by zoomy942 on 2008-10-28
> **| MM | said:**
> Hi,

Just another anecdotal data point.

Since Hardy (and now Intrepid) i have noticed many more stutters, and the mouse freezes during heavy io, say, during installing updates or cold starting applications.  This never happened in prior versions.

Everything seems slow to load, firefox and nautilus particularly.

Perhaps one dev cycle should focus on optimising the desktop stack.


i had that happen so i decided to try the 8.10 RC of xubuntu.  holy cow man - it's blazing fast

---

### Post by plun on 2008-10-28
> **jfernyhough said:**
> Same happened to me. I had to cold reset, then on next boot CTRL-ALT-F1, log in, and run $ sudo nvidia-xconfig. It worked after that.



Solved.... installed the driver again followed with a reboot then it works !

Rhythmbox works again without CPU hogs...:)

Next > "Beat" PA from GIT ...

---

### Post by kestal on 2008-10-28
I will admit, I LOVE ubuntu. I will also admit, Windows has its moments.

However, if Ubuntu really wants to market itself mainstream then it has to realize that it will be compared to Windows a lot.

Especially now, I can EASILY say that my Ubuntu load up speed is HORRIBLE compared to Windows (and this is an out of the box Ubuntu 8.10 install). I have made my opinions clear on the sheer bloat that comes with Ubuntu but not many people seem to get it.

Ubuntu 8.10 looks heavenly and it has not crashed a single program since I tried it, but if it takes 3x as long to Log into it than it does for me to Log into XP (with bloatware up to my chin), then whats the selling point? Sure, I can customize it, but I can do the same in Windows, plus games work on it natively.

Despite any of this, a quad core (with 4gb of ram and 512mb video card) should not appear to load up Ubuntu sluggishly, no matter HOW you try to spin your lies. Ubuntu needs to find a way to fix this.

---

### Post by zoomy942 on 2008-10-28
> **kestal said:**
> I will admit, I LOVE ubuntu. I will also admit, Windows has its moments.

However, if Ubuntu really wants to market itself mainstream then it has to realize that it will be compared to Windows a lot.

Especially now, I can EASILY say that my Ubuntu load up speed is HORRIBLE compared to Windows (and this is an out of the box Ubuntu 8.10 install). I have made my opinions clear on the sheer bloat that comes with Ubuntu but not many people seem to get it.

Ubuntu 8.10 looks heavenly and it has not crashed a single program since I tried it, but if it takes 3x as long to Log into it than it does for me to Log into XP (with bloatware up to my chin), then whats the selling point? Sure, I can customize it, but I can do the same in Windows, plus games work on it natively.

Despite any of this, a quad core (with 4gb of ram and 512mb video card) should not appear to load up Ubuntu sluggishly, no matter HOW you try to spin your lies. Ubuntu needs to find a way to fix this.


try xubuntu for a day or 2.  see what you think about speed then.

---

### Post by kestal on 2008-10-28
> **zoomy942 said:**
> try xubuntu for a day or 2.  see what you think about speed then.

I dislike Xubuntu for its lack of drag/drop features as well as on-the-fly custom icon changes like in Gnome (well, for a few other features, too).

However, I am currently waiting for Xfce 4.6 to become released.

whats sad is that, if you are relatively decent at program, there **IS** a way to increase boot up speed and overall performance by modifying the Kernel (while keeping it perfectly stable and allowing it to boot up within 5 seconds, into the desktop), however knowing my luck that'll never happen.

---

### Post by rzrgenesys187 on 2008-10-28
> **dabl said:**
> [QUOTE=ronacc]  View Post
I don't know what this means as far as any "slowdown" might be concerned but I did notice that a few days back my cpu core temps dropped ~10C , they had been running a little higher than hardy on the same box and now are "normal".Yep, same thing here. My overclocked X6800 was running up near 80 C when I pushed it, in Hardy  :?  Not too pleased with that.  Now it's around 65 - 70 C when busy, and 50s when idling -- much better.  :)[/QUOTE]

Was the decreased temperature on Intrepid?  I've noticed the last couple releases that my cpu temp seemed to be ~10-15 degrees higher when idling as opposed to Fiesty.

---

### Post by ronacc on 2008-10-28
> **rzrgenesys187 said:**
> Was the decreased temperature on Intrepid?  I've noticed the last couple releases that my cpu temp seemed to be ~10-15 degrees higher when idling as opposed to Fiesty.

yes the decreased temp was on intrepid  ,ewrly on intrepid was running about 10C hotter than hardy or gutsy on the same box the a few days ago (I'm not sure exactly when ) the temps dropped back down to what I "normaly" see , 32>35C idling on an amd64X2 4600 (no overclock).

---

### Post by crjackson on 2008-10-28
Wow! This thread is really discouraging. I was planning to run Intrepid on my systems in a couple of weeks but now I’m wondering if I should just move to a whole new distro. Ubuntu is the only distro I’ve ever used, but it sounds like it’s going down the tubes fast and I should just drop it all the way and look elsewhere for my Linux needs.

---

### Post by rzrgenesys187 on 2008-10-28
> **ronacc said:**
> yes the decreased temp was on intrepid  ,ewrly on intrepid was running about 10C hotter than hardy or gutsy on the same box the a few days ago (I'm not sure exactly when ) the temps dropped back down to what I "normaly" see , 32>35C idling on an amd64X2 4600 (no overclock).

That's a shame.  My sound quality is very bad so I won't be running it for a bit yet :(

---

### Post by plun on 2008-10-28
> **ronacc said:**
> yes the decreased temp was on intrepid  ,ewrly on intrepid was running about 10C hotter than hardy or gutsy on the same box the a few days ago (I'm not sure exactly when ) the temps dropped back down to what I "normaly" see , 32>35C idling on an amd64X2 4600 (no overclock).

We have the same card model, a 7600GS as I remembers it.

I went down to around 50 celcius degrees with the 2.6.28 kernel.
59 normal for Intrepids kernel

All my CPU "hogs" are now gone...:)

So something must be terrible wrong with Intrepids kernel.

or if it can be DKMS and kernel/driver...:confused:

---

### Post by lerrup on 2008-10-28
> **kestal said:**
> I will admit, I LOVE ubuntu. I will also admit, Windows has its moments.

However, if Ubuntu really wants to market itself mainstream then it has to realize that it will be compared to Windows a lot.

Especially now, I can EASILY say that my Ubuntu load up speed is HORRIBLE compared to Windows (and this is an out of the box Ubuntu 8.10 install). I have made my opinions clear on the sheer bloat that comes with Ubuntu but not many people seem to get it.

Ubuntu 8.10 looks heavenly and it has not crashed a single program since I tried it, but if it takes 3x as long to Log into it than it does for me to Log into XP (with bloatware up to my chin), then whats the selling point? Sure, I can customize it, but I can do the same in Windows, plus games work on it natively.

Despite any of this, a quad core (with 4gb of ram and 512mb video card) should not appear to load up Ubuntu sluggishly, no matter HOW you try to spin your lies. Ubuntu needs to find a way to fix this.

Frankly hilarious - I have never had a linux distro boot slower than windows on similar hardware (back to Mandrake in 2004) and feel you are either seriously stuffed with your setup or lying.

On my T60, Ubuntu boots at the same speed XP wakes from suspend...

Are you comparing like with like - it would be more sensible to take the time up to being able to get on line as a metric rather than when you can see the login screen.

---

### Post by Lucretius on 2008-10-28
I thought I was the only one..

Ubuntu is an absolute slug at the moment... even running large video files that formally gave me no problem,  even with multiple windows open... are now stuttering badly.

Games wont run smoothly and everything is taking an age to load.

Something is badly wrong.

System:

Athlon 2500XP
1GB DDR
Nvidea 7600gt

---

### Post by scaine on 2008-10-28
> **Lucretius said:**
> 
Athlon 2500XP
1GB DDR
Nvidea 7600gt

Strange - I'm running Athlon (think it's an X2 - 2200?) here too, 2Gb DDR and an Nvidia 6800GT and I'm very impressed with Intrepid so far.

I would say that Intrepid has certainly had the rockiest beta road I've ever travelled, but since about 3 weeks ago, it's been very stable and running very well.  I'm using Banshee hooking into Last.FM and playing over my Samba share to my little server - full effect compiz and I'm very pleased with the CPU.

I used DeVeDe to create a full length DVD from four AVI files a couple of days ago and it took an hour to encode and burn.  Honestly, all good.

I wonder if all these reported problems are possibly memory related?  My 2Gb is rarely over 50% utilised, except by cache.

Hope you guys sort out your speed problems, but I thought it was worthwhile to point out that some of us are definitely less affected by these problems (if at all) than this thread is making out.

---

### Post by psyke83 on 2008-10-28
> **lerrup said:**
> Frankly hilarious - I have never had a linux distro boot slower than windows on similar hardware (back to Mandrake in 2004) and feel you are either seriously stuffed with your setup or lying.

On my T60, Ubuntu boots at the same speed XP wakes from suspend...

Are you comparing like with like - it would be more sensible to take the time up to being able to get on line as a metric rather than when you can see the login screen.

Prove it. In my experience, Windows XP *does* boot faster with a reasonable configuration (trimming unnecessary 3rd party startup programs, defragmenting drives and cleaning the registry). Although XP employs some tricks to give the illusion of an even faster boot (services and explorer.exe still loading when the desktop appears), overall it is faster than Ubuntu (from kernel init to GNOME desktop).

Ubuntu is not a lightweight distribution. Linux is not the same as Windows. There are, in fact, legitimate reasons for Ubuntu to boot slower (more features compared to a stock XP install, and hardware detection via modprobe, udev, etc). That's not to say we shouldn't let these facts hold us back from optimizing speed...

---

### Post by kestal on 2008-10-28
> **psyke83 said:**
> Prove it. In my experience, Windows XP *does* boot faster with a reasonable configuration (trimming unnecessary 3rd party startup programs, defragmenting drives and cleaning the registry). Although XP employs some tricks to give the illusion of an even faster boot (services and explorer.exe still loading when the desktop appears), overall it is faster than Ubuntu (from kernel init to GNOME desktop).

Ubuntu is not a lightweight distribution. Linux is not the same as Windows. There are, in fact, legitimate reasons for Ubuntu to boot slower (more features compared to a stock XP install, and hardware detection via modprobe, udev, etc). That's not to say we shouldn't let these facts hold us back from optimizing speed...

I will say right now, that I am not disagreeing with the fact that XP uses a few tricks and the illusion of booting up quicker. You know what? with that said, it sells! These tricks were done in an Linux build with the same results. They managed to boot Ubuntu within 5 seconds after the splash.

I agree that Ubuntu is not a lightweight distribution. I would not want it to be. But there are other ways to increase the speed and performance of the overall system. From a marketing point of view, it is what will give decent Linux distributions a hard time. (even if the points are valid).

Link Is as follows:
[http://lwn.net/Articles/299483/]("http://lwn.net/Articles/299483/")

- Fact: A linux developer at Intel, powertop head, as well as a few others, managed to pull off the same wizardy that happens with XP (while keeping the stable outlook of the overall system).
- In the example this was done with Fedora and Ubuntu.
- Unfortunetely (or at least to my knowledge), unless the Kernel and X are moderately redone, this is not possible.

Ontop of that, though Ubuntu has a lot out of the box, it has TOO much. Half of the features and programs that are included are a waste. Half of the themes are outdated and should be removed. Most of the screensavers, too. That would cut down on a lot of space to include more driver support and provide other areas with much more needed attention.

Even fixing it up with a newbie-friendly installation with options to choose from at start. I mean, every time I install Ubuntu, I have to spend an hour or so carefully removing the things I do not need. (and making sure not to remove packages within Evolution as that also removes gnome-panel - good job Ubuntu - though further inspecting I guess it makes sense, I just wish they'd rename a few files to avoid that).

---

### Post by ronacc on 2008-10-28
> **plun said:**
> Take this as a reference case.

- Start Firefox with four tabs

- Start LastFM and a network stream with your favorite music

- Start something else, Openoffice document or just the update manager....

*top" should be running all the time..... something IS wrong..!

ok I got a chance to try your test .I don't have a lastFM account so I streamed the BBC using the radio screenlet. FF with 4 tabs (one with flash) and an open document in OO 3.0 . plus boinc running 2 tasks 1 seti 1 astropulse . plus playing a WMV in VLC  . No lag anywhere and it didn't even upshift my CPU off the bottom speed step .
I didn't have top running I missed that step so I'll do it again with top.
EDIT: no change and nothing strange with top .

my specs  MB gigabye ga-m55plus-s3g rev2.1  ,CPU amd64x2 4600 , video nvidia 7600gs/256mb/177.80 driver , ram 4gb , internet slow (384kb/s) US cable .
intrepid/gnome installed at A3 from live cd and updated twice daily .

---

### Post by autocrosser on 2008-10-28
Well--as far as boot-time......

My system---Intel Core2 Q9300
Cold boot to GDM.... (see boot chart) Now, true I'm running "high-end" hardware, but 34 sec to GDM is not too bad--The only things I have done is the "noticks=off" in my kernel line & remove some unused things from my services (PPP stuff).

I have 4G of DDR2 1066 ram, so I don't really see slowdowns unless I am crunching SETI data units with all four cores.......The system becomes slightly sluggish then. I would think that the stress-test of all 4 cores running at 100% would cause a problem---but it is not very much of one.

Now true--during Fiesty testing I was able to go cold to GDM in about 15~18 sec with the system I had then--Pent D 3.2 & 4G DDR400---I'm sure that my current system could knock that down to 10~12 sec...But I run my desktop for days at a time (average uptime is 8 days), so 10~20 sec is not much of a bother to me.

---

### Post by ronacc on 2008-10-28
> **plun said:**
> We have the same card model, a 7600GS as I remembers it.

I went down to around 50 celcius degrees with the 2.6.28 kernel.
59 normal for Intrepids kernel

All my CPU "hogs" are now gone...:)

So something must be terrible wrong with Intrepids kernel.

or if it can be DKMS and kernel/driver...:confused:

yes same video card mine runs about 55C with 2.6.27-7 and the 177.80 driver was up as high as 59C awhile back .

---

### Post by | MM | on 2008-10-29
> **psyke83 said:**
> Prove it. In my experience, Windows XP *does* boot faster with a reasonable configuration (trimming unnecessary 3rd party startup programs...

I second that.  Windows XP starts up significantly faster than Ubuntu on my system.

---

### Post by kestal on 2008-10-29
> **| MM | said:**
> I second that.  Windows XP starts up significantly faster than Ubuntu on my system.

At least I am not going crazy. Good to know. :)

Also @ autocrosser.

34 seconds to GDM (Cold Boot) is ***horrible*** for an Intel Core2 with 4gb of ram. Cold-booting, My Quad Core rig + XP (desktop) can do that in 15 seconds, and the majority of that is due to the post sequence prior to even seeing the splash screen (about 20 seconds to desktop, if I use VTP - but yay for eye candy). Hell, the stock windows bar in splash doesn't even have a chance to go through once. On Ubuntu, its just painful almost, having to wait and watch as it slowly goes up.

So explain how a 34s is 'decent'. I mean, the idea of a quick boot and the rather sluggishness of opening up programs is what is stopping me from staying with Ubuntu 100% of the time. Opening up Firefox should not take more than a second. (and in which, it does for a lot of people). My XP firefox opening is almost instant. 

I mean, I got my rig so I wouldn't have to deal with that kind of stuff. The reason why I paid so much money is so I could see a massive improvement. When people are used to seeing 10 second boot times with instant program opening, they do not want to transfer to something that takes 34 seconds.

---

### Post by vishzilla on 2008-10-29
Firstly, Phoronix should test other distros too to see if its a general Linux trend or just Ubuntu's. Just because Ubuntu is too popular, it shouldn't always get the only attention.

---

### Post by psyke83 on 2008-10-29
> **kestal said:**
> So explain how a 34s is 'decent'. I mean, the idea of a quick boot and the rather sluggishness of opening up programs is what is stopping me from staying with Ubuntu 100% of the time. Opening up Firefox should not take more than a second. (and in which, it does for a lot of people). My XP firefox opening is almost instant.

That's not an indication of Ubuntu being inherently less efficient. In XP and beyond, Firefox starts quicker because of Windows' built-in prefetch function that monitors frequently-used applications. If you delete C:\WINDOWS\Prefetch\*.* and reboot, then you'll see the true application startup performance.

Ubuntu uses "readahead" to preload a static list of boot files into memory, but it doesn't monitor applications in the same way as Windows. There are some alternatives ("preload", available in our repository, and the somewhat new [prefetch]("http://code.google.com/p/prefetch/")).

---

### Post by autocrosser on 2008-10-29
Did you look at my bootchart? Almost all the time is involved with udevd in two instances & a full 4 sec is with readahead---I commented that Fiesty (before some of these services) was cold to GDM around 18sec with a much older set-up & I opinioned that with my current set-up that would be about 10~12 sec--Is that more to your time-span?

And my programs open very quickly unless I'm using all my cores @ 100% crunching SETI--and even then they run fairly well--2~3 sec opening times.

In any case--I only reboot when I need to--this system runs 24/7---so the point in my case is almost moot--how long will the windows install run? My longest times are measured in weeks--not hours.


> **kestal said:**
> At least I am not going crazy. Good to know. :)

Also @ autocrosser.

34 seconds to GDM (Cold Boot) is ***horrible*** for an Intel Core2 with 4gb of ram. Cold-booting, My Quad Core rig + XP (desktop) can do that in 15 seconds, and the majority of that is due to the post sequence prior to even seeing the splash screen (about 20 seconds to desktop, if I use VTP - but yay for eye candy). Hell, the stock windows bar in splash doesn't even have a chance to go through once. On Ubuntu, its just painful almost, having to wait and watch as it slowly goes up.

So explain how a 34s is 'decent'. I mean, the idea of a quick boot and the rather sluggishness of opening up programs is what is stopping me from staying with Ubuntu 100% of the time. Opening up Firefox should not take more than a second. (and in which, it does for a lot of people). My XP firefox opening is almost instant. 

I mean, I got my rig so I wouldn't have to deal with that kind of stuff. The reason why I paid so much money is so I could see a massive improvement. When people are used to seeing 10 second boot times with instant program opening, they do not want to transfer to something that takes 34 seconds.

---

### Post by cariboo on 2008-10-29
Using XP boot time as a benchmark is not a true comparison, WIndows XP is 7 years old and was a horror when it first came out. There weren't many drivers available and it was sloooow. If you are going to compare boot times. We should chart how long Vista takes to boot against How long Intrepid takes, and test the same task in each OS.

Subjectively Firefox takes much longer to start up in VIsta then it does in Intrepid. Actually IE8 takes the same amount of time to load as Firefox does in Intrepid. Those are the only two programs that I use regularly between OS's, but I have found that Intrepid overall is faster then Vista.

Jim

---

### Post by dabl on 2008-10-29
I don't get all the passion about boot time.  :confused:

If you're all about a fast boot, it seems that you do have other choices:

1. Use suspend-to-RAM (S2RAM).  On my desktop rig, Intrepid wakes up in about 10 - 15 seconds, including a browser session if that's the way I hibernated it.

2. Install something like DSL or Slax.

I've never heard that *buntu had "fastest cold boot in town" in its performance objectives, nor does that seem real important to me either.

---

### Post by Npl on 2008-10-29
> **cariboo907 said:**
> Using XP boot time as a benchmark is not a true comparison, WIndows XP is 7 years old and was a horror when it first came out.Uh.. so what?
It runs fine now that drivers are sorted and the UI runs circles around any Linux Distro I tried (with or without Compiz crap). And the old XP has no problem accelerating h264 Video, something the oh-so-modern Ubuntu still fails to do.

Besides, the boot-time is the least important point, when I just read the headline, I thought about insignificant differences... halfing the speed in alot of computational tasks (compression database, etc) is quite bad.

---

### Post by zoomy942 on 2008-10-29
> **kestal said:**
> I dislike Xubuntu for its lack of drag/drop features as well as on-the-fly custom icon changes like in Gnome (well, for a few other features, too).

However, I am currently waiting for Xfce 4.6 to become released.

whats sad is that, if you are relatively decent at program, there **IS** a way to increase boot up speed and overall performance by modifying the Kernel (while keeping it perfectly stable and allowing it to boot up within 5 seconds, into the desktop), however knowing my luck that'll never happen.


hi buddy.

did you try it out?  Xubuntu does the drag and allows custom icon changes  :)

---

### Post by Amazona aestiva on 2008-10-29
At first I've not experianced these changes. Moreover Hardy is far the best in my private opinion.

And anyway:
I don't think that article says so much, because

1. Ubuntu is faster (at least for me) then any Windows I've seen.( I admit that a fresh Windows installation can be faster than Ubuntu, but that's not a long period )

2. I wouldn't mind to wait a bit longer, if the system is so stable.

3. I've seen other linux distros that are way more slower than Ubuntu.

Summary:
This article won't persade me and I think neither many Ubuntu users to change or do something. On the other hand it's quite interesting what is in Feisty that makes it double as fast as the recent ones in memory management?

Just my opinion.:)

Regards

---

### Post by philinux on 2008-10-29
The thing that irks is that the alphas 1-4 ish were/seemed a lot faster than the beta and RC.

---

### Post by zoomy942 on 2008-10-29
> **philinux said:**
> The thing that irks is that the alphas 1-4 ish were/seemed a lot faster than the beta and RC.


i would 10000% agree with you.

its so confusing when you fresh install an RC and it's slower.

---

### Post by Half-Left on 2008-10-29
The thing is Ubuntu doesn't offer optimized kernel, the generic one is not as it name implies. They do tend to leave some dbug options on but yet dont have debug in there packages for testing period(debug symbols)

I think they should look at optimized versions of the kernel and packages.

---

### Post by plun on 2008-10-29
> **dabl said:**
> I don't get all the passion about boot time.  :confused:

If you're all about a fast boot, it seems that you do have other choices:



Nope and its not the challenge for the moment either...:)

Clearly the kernel is bad, really bad.

I also believe that something is wrong with **esound** and the socket against PulseAudio.

PA from GIT was a real "pig"  :biggrin:... so I am back on 0.9.10 and if I disable sound within about : config  Firefox is faster and also much less CPU.

I am going to ask the mozilla-team if they knows more about esound.

:-k

---

### Post by philinux on 2008-10-29
Maybe it was the earlier kernels that made the alphas that much quicker.

---

### Post by marmuta on 2008-10-29
Ok, some good news. I found a few causes for my slowdowns at least. They can't explain the Phoronix benches but most of my performances problems with Intrepid are gone now.

Pulseaudios cpu hogging was actually caused by mnemosyne. I had it autostarting and hiding to the tray and forgot about it. Filed bug [#290691]("https://bugs.launchpad.net/ubuntu/+source/mnemosyne/+bug/290691"). Please confirm if anybody is using it too.

I didn't get pulseaudio to spike the cpu during audio streaming/playing anymore, which Plun and I were seeing, but I'll keep an eye on it.

The sluggishness of Evolution and Thunderbird got a little better when I switched the radeon os driver from EXA to XAA, which is the default for Intrepid anyway. Flash runs better too and no more lags in gnome menu.

Only the sqlite stuff gives me headaches now. Liferea is close to unusable, fsyncs everywhere. Filed this bug here [#290666]("https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/290666").
I really wish less apps would use sqlite, they all seem to suffer from mindless fsyncing. 
Phoronix showing this huge performance drop for sqlite makes me cringe.

---

### Post by hardyn on 2008-10-29
Agreed.  this same battery of tests should be tested against a similarly loaded distro; as all linuxes share variants of the same kernel, it would quickly identify where the issues may lay.

i really think more technical information regarding the architecture of the test battery is needed.  what applications are are highly threaded, single threaded, graphics tool kit, processor based optimizations (sse, mmx, etc).  what about trying other processors (amd 32/64 intel 32/64 single and multi-core) etc.

seems like a bit of flashy headline article; there maybe something to it... but sounds like a bit of hype grabber.

 


> **vishzilla said:**
> Firstly, Phoronix should test other distros too to see if its a general Linux trend or just Ubuntu's. Just because Ubuntu is too popular, it shouldn't always get the only attention.

---

### Post by glasen on 2008-10-29
Hi,

A user at the german forum "www.ubuntuusers.de" did some tests with his Lenovo T60 (same hardware as the one in the Phoronix-test) on Ubuntu 8.10. His scores are dramatically better than the ones from the Phoronix test :

LAME-MP3 : 60.62s

OGG : 35.05s

FLAC : 28.82s

WAVPACK : 31.22s

FFMPEG : 33.76s

SQLITE : 24.21s

SCIMARK (composite) : 290.28 Mflops

Tandem-XML (write) : 54.22s

How can it be that two systems with the same hard -and software got so different test results? And there are other tests with slower machines (mine included) which got better results than the T60 in the Phoronix test.

The numbers of the Phoronix test are far away from to be plausible. If an maschine that has a slower CPU performs better than a faster machine and a completely identical machine of another user performs better too, than there is a great possibility that the Phoronix test is faulty.


Discussion at Phoronix :

[http://www.phoronix.com/forums/showthread.php?t=13486&page=6](http://www.phoronix.com/forums/showthread.php?t=13486&page=6)

Discussion at ubuntuusers.de (in german) :

[http://forum.ubuntuusers.de/topic/warum-sind-die-kernel-nach-2.24-so-verdammt-l-1/5/](http://forum.ubuntuusers.de/topic/warum-sind-die-kernel-nach-2.24-so-verdammt-l-1/5/)

---

### Post by kestal on 2008-10-29
> **psyke83 said:**
> That's not an indication of Ubuntu being inherently less efficient. In XP and beyond, Firefox starts quicker because of Windows' built-in prefetch function that monitors frequently-used applications. If you delete C:\WINDOWS\Prefetch\*.* and reboot, then you'll see the true application startup performance.

Ubuntu uses "readahead" to preload a static list of boot files into memory, but it doesn't monitor applications in the same way as Windows. There are some alternatives ("preload", available in our repository, and the somewhat new [prefetch]("http://code.google.com/p/prefetch/")).

I didn't mean to say that Ubuntu was less efficient. Ubuntu adds so much XP does not offer. I did have a chance to try out preload, that actually made a lot of difference. 2-3 sec load up of  firefox is better than 6-10 second load up.

For the newer computers/laptops,  what would the disadvantage be of this?

With that said then, whats your opinion on sReadahead?

---

### Post by ronacc on 2008-10-29
I always take "benchmarks" with a grain of salt unless I run them myself on the machine I am actualy using ( not the same type/configuration , the machine I am physicaly typing on ) . even properly desined and executed benchmarks do not represent the reality of my environment/use , therefore I pay more attention to my "subjective" impression than to a supposed "objective" test .

---

### Post by jfernyhough on 2008-10-29
> **glasen said:**
> Hi,

A user at the german forum "www.ubuntuusers.de" did some tests with his Lenovo T60 (same hardware as the one in the Phoronix-test) on Ubuntu 8.10. His scores are dramatically better than the ones from the Phoronix test :
That doesn't necessarily mean anything, unless he also performs the same tests using each release of Ubuntu as Phoronix did. Then he could compare performance between releases, which was the point of the test, not to compare performance between machines.

---

### Post by glasen on 2008-10-29
You didn't get the point. The point about the comparison is if the scores Phoronix got, are plausible. It is not about "Ubuntu 7.04 is faster than Ubuntu 8.10". 

Example :

System A, B and C are compared. An all Systems Ubuntu 8.10 is installed. 

System A is faster (better CPU, more RAM, etc.) than system B and system C is equal to system A (A=C>B). Now we run some tests. The test shows the following results :

System A is slower than system B and system C is faster than B (C<B<A). Every human with some kind of intelligence would now think, that something went wrong with the test, because system A should be as fast as system B and system C should be the slowest.

Now substitute System A with the IBM T60 tested by Phoronix (Core2Duo T2400 1.87GHz, 1GB DDR2-RAM), system B with my personal Latitude D505 (P-Mobile 1.7GHz, 2GB DDR1-RAM) and system C is the same as system A (IBM T60 of another user at the german forum).

A is completely irrelevant that we didn't test another version. We showed that the numbers Phoronix got for Ubuntu 8.10, are faulty and that the scores of the users T60 are nearly identical to the numbers of Ubuntu 7.04 Phoronix got with its T60.

---

### Post by jfernyhough on 2008-10-29
Right, I understand. A faster machine certainly shouldn't be slower than a slower system.

If I remember correctly, the Phoronix tests installed various other bits of software; I wonder if these might affect things?

---

### Post by plun on 2008-10-29
> **jfernyhough said:**
> 
If I remember correctly, the Phoronix tests installed various other bits of software; I wonder if these might affect things?

Yup, probably important.

I see what I see after running Intrepid from pre Alpha to final.

Everything is back to normal with kernel 2.6.28.   (esound ? )

Another test would be with a plain Vanilla 2.6.27.4 kernel

---

### Post by plun on 2008-10-29
Followup... found the bug ....:)

> System started to have IO lock-ups until I maximized (?!) one of the deadlocked processes, and then all blocked processes continued. Most of the time, though, **it just slowly hangs more and more of the system** until I have a **full hardlock**.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262843)


nVidia GPU core temp also went down about 10 degrees for me
with another kernel...:confused:

---

### Post by jfernyhough on 2008-10-29
> **plun said:**
> nVidia GPU core temp also went down about 10 degrees for me with another kernel...:confused:All of my temps are down... CPU, HDD, Nvidia... (2.6.28rc2)

---

### Post by plun on 2008-10-29
> **jfernyhough said:**
> All of my temps are down... CPU, HDD, Nvidia... (2.6.28rc2)

Well... seems to be a rather critical bug.

I have Conky or Screenlets System monitor running and its so easy to
see if something is wrong or if everything just works. 

PackageKit also started to work for me without "racing conditions" (apt-backend)...

---

