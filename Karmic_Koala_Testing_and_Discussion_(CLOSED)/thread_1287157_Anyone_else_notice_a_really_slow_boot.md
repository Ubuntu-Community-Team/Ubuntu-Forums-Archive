---
title: "Anyone else notice a really slow boot?"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-10-09
Is Karmic supposed to boot slower than Jaunty for the time being?

On my laptop jaunty never took more than 25 or so seconds to login screen but karmic takes 40 seconds+. Is this due to the new xsplash etc, or is it supposed to be booting at least a bit faster than jaunty by karmic.

I'm completely aware that the boot goals are for lucid not karmic, but I wasn't expecting such a regression.

---

### Post by hanzomon4 on 2009-10-09
With the latest updates yeah

---

### Post by cariboo on 2009-10-09
Karmic is still in beta, wait until the release to complain about a slow boot. Things can still change quite a bit between now and October 29th.

---

### Post by jeremyswalker on 2009-10-09
> **cariboo907 said:**
> Karmic is still in beta, wait until the release to complain about a slow boot. Things can still change quite a bit between now and October 29th.

I agree with the not complaining about a beta product. My laptop is slower to boot in Karmic than in Jaunty, as well. I'm not complaining about it. However, I have heard numerous reports of Karmic beta booting much faster than Jaunty. Apparently, I'm not a part of that group. :(

---

### Post by Elfy on 2009-10-10
I would agree with not complaining - but stating that it is happening I can go along with.

My 30sec boot is now 80secs ;)

---

### Post by Merk42 on 2009-10-10
Wow I restarted my Karmic VM to see, and after the lone white Ubuntu icon I just get a blank screen. Had it up for a while now and nothing...

---

### Post by hikaricore on 2009-10-10
On the bright side those of us who never reboot (twice a month if that?) won't really have anything to worry about.  ^_^

---

### Post by Aearenda on 2009-10-10
> **forestpixie said:**
> I would agree with not complaining - but stating that it is happening I can go along with.
+1

It is reassuring to me that I am not alone with the same problem, and prevents me wasting time trying to determine if I have a hardware problem or a bug to register.

---

### Post by Sashin on 2009-10-10
Yeah, the whole point in this thread was to find out if I was alone and if anything would be done about it. If it was unique to my machine there would be a good chance that it wouldn't be fixed by final release so this is reassuring.

---

### Post by VMC on 2009-10-10
> **Sashin said:**
> Yeah, the whole point in this thread was to find out if I was alone and if anything would be done about it. If it was unique to my machine there would be a good chance that it wouldn't be fixed by final release so this is reassuring.

From what I understand from reading at Launch Pad, they haven't really dealt with the final push for faster booting. Hopefully it will be one of the last items to address. One of the devs touched on the subject, but I couldn't direct you to the post. At the time I was having issues with Intel drivers.

My karmic as it stands right now takes ~40 secs. Jaunty takes the shorter route. I'm one of those that re-boots often.

There's a corollary to this. My shutdown is extremely fast! I was about to shut down when I thought about the dichotomy. Most would gladly have it reversed.
On the one end we hear mostly about boot-up but rarely anything on shutdown.

---

### Post by kadafi69 on 2009-10-10
my boot is taking longer too, and i dont have the grub boot logo.

---

### Post by golusweet on 2009-10-10
Yes, It takes longer time than Jaunty.

I don't think so, Boot time will be reduced now.

---

### Post by P4man on 2009-10-10
Im seeing the exact opposite. Alpha's wheren't any faster than jaunty for me, in fact possibly even slower, but yesterday I did a fresh install of karmic beta, and I was shocked how fast it boots. Its well under 30s to get the login screen, and under 40s to get to a desktop. That is after installing virtualbox, nvidia binary drivers, enabling compiz and on a modest 4 year old machine. Short of Slitaz (and splashtop heh), Ive never seen anything boot this fast.

---

### Post by Insane_Homer on 2009-10-10
under Jaunty (clean install) bootchart was reporting 28 seconds boot time

2nd boot after Karmic upgrade it jumped to 1:27 (59 seconds slower)

Current boot time is 1:22 

So nearly a minute slower.

On my laptop with a clean install (one of the last alpha builds if I recall) the boot time of Karmic is 1:28 that too was around the 30 second mark on 9.04

---

### Post by fut21 on 2009-10-10
I can confirm that karmic is a slow-booter. I have karmic installed on 3 different computeres and all bootes very slow compared to jaunty just like the numbers in #14. I hope it will get fixed until RC release.

---

### Post by emarkay on 2009-10-10
> **hikaricore said:**
> On the bright side those of us who never reboot (twice a month if that?) won't really have anything to worry about.  ^_^

Serious Question - I have seen this rather often, even with Window$ machines - and I am not talking about servers. 

How can the RAM be cleared, and any low level updates be installed if the machine is never rebooted.  I know that in many of those Win machines it's user ignorance/incompetence, and in Linux, lower level updates are much rarer, but one would think that a reboot every few days or so would ensure a "cleanslate" for apps to run.

Also for beta testing, you really SHOULD reboot after most updates, correct?

Curious.

---

### Post by P4man on 2009-10-10
> **emarkay said:**
> Serious Question - I have seen this rather often, even with Window$ machines - and I am not talking about servers. 

How can the RAM be cleared, 

Ram doesn't need to be "cleared". Unless you mean freed, and thats only necessary when some app has a memory leak and keeps using more RAM. In such case, restarting the app in question should do the trick.

> and any low level updates be installed if the machine is never rebooted.  I know that in many of those Win machines it's user ignorance/incompetence, and in Linux, lower level updates are much rarer, but one would think that a reboot every few days or so would ensure a "cleanslate" for apps to run.

It doesn't hurt to reboot every now and then, unless your system is a server which is expected to have 99.9% uptime :). In those cases, or Id say typically for servers, upgrades are planned, and patches/updates will be applied selectively if deemed useful or necessary and if needed, the machine will be rebooted at a conventient moment. This will happen more often with network facing servers, as security updates are more important, and typically, you have redunancy, so taking down one server at the time should hurt anyone. Network facing servers are typically patched/rebooted like once a week. But backoffice servers are often not rebooted for several months, or longer.

> Also for beta testing, you really SHOULD reboot after most updates, correct?


You should only reboot for updates when it tells you to reboot. But then again, it doesn't hurt on a desktop :)

---

### Post by hikaricore on 2009-10-10
> **emarkay said:**
> Also for beta testing, you really SHOULD reboot after most updates, correct?

Honestly I only reboot when a critical package is updated such as libc6.
Kernel updates don't require a reboot as the new kernel will take effect on the next boot and does not affect my current session.
Any services that are updated restart upon installation so that's not an issue either.
The classic if it ain't broke don't fix it applies here, why reboot when I don't need to?

---

### Post by Insane_Homer on 2009-10-11
> **Insane_Homer said:**
> under Jaunty (clean install) bootchart was reporting 28 seconds boot time

2nd boot after Karmic upgrade it jumped to 1:27 (59 seconds slower)

Current boot time is 1:22 

So nearly a minute slower.

On my laptop with a clean install (one of the last alpha builds if I recall) the boot time of Karmic is 1:28 that too was around the 30 second mark on 9.04

I posted these figures yesterday on the understanding that bootchart was reporting like for like.

my limited understanding is that the clock starts on choosing the boot image from grub and finished at the login prompt? (At least this was the case with Jaunty).

As you can see  Karmic bootchart reports boot times of 1:20+ seconds (my 1st recorded bootchart from a Jaunty boot was reported @ 22 seconds)

However I was sure that it was not that slow. So I booted this morning and timed it on a stop watch and it's **actually somewhere in the region of 35-40 seconds.**

So I'd suspect that they've  changed  bootchart to measure beyond the login screen?

Looking at the latest bootchart it does seem that the post login environment is being logged(gnome for me), since I can see it reporting load times for nautilus and gnome-clock.app etc.

---

### Post by MacUntu on 2009-10-11
> **Insane_Homer said:**
> So I'd suspect that they've  changed  bootchart to measure beyond the login screen?

Correct. That's why so many ppl are upset about their long boot times...

The 'time' value only shows how long bootchart ran - the interesting value is when your CPU/IO-graph starts to shows no activity for a longer period - that's your full boot time. If you can't find such an idling phase your boot time might even be longer than bootchart runs (you can change that in /etc/init/bootchart.conf by in-/decreasing the 45 second sleep).

---

