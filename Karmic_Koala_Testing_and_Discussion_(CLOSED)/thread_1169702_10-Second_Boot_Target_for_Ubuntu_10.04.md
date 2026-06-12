---
title: "10-Second Boot Target for Ubuntu 10.04"
date: 2009-05-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ghindo on 2009-05-25
We knew from [the beginning]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html") that Karmic was supposed to have a faster boot time, but at UDS, it looks like the developers are aiming for a 10-second boot time with Karmic.

[http://identi.ca/notice/4558529](http://identi.ca/notice/4558529)
[http://twitter.com/szilveszter/statuses/1946601057](http://twitter.com/szilveszter/statuses/1946601057)

Watch Mark Shuttleworth talk about it (mentions it at 1:20):  [http://www.youtube.com/watch?v=t3PJPYWtJ9o](http://www.youtube.com/watch?v=t3PJPYWtJ9o)

---

### Post by ktp on 2009-05-25
> **ghindo said:**
> We knew from [the beginning]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html") that Karmic was supposed to have a faster boot time, but at UDS, it looks like the developers are aiming for a 10-second boot time with Karmic.

[http://identi.ca/notice/4558529](http://identi.ca/notice/4558529)

Watch Mark Shuttleworth talk about it (mentions it at 1:20):  [http://www.youtube.com/watch?v=t3PJPYWtJ9o](http://www.youtube.com/watch?v=t3PJPYWtJ9o)

That would be great!!

---

### Post by MacUntu on 2009-05-25
Seems possible with dual core and 7200rpm disk.

Edit: From the clapping and laughing I conclude this was more like a running gag? Didn't fully understand what he said.

---

### Post by camper365 on 2009-05-25
Well, my computer is kind of old and has a 5400 RPM disk and a 1.86 GHz single core processor and the Jaunty 20 second boot time is actually 22 seconds. So maybe the Karmic 10 second boot time will be 12 seconds even on an old computer.

---

### Post by super.rad on 2009-05-25
I'll believe it when I see it

---

### Post by tad1073 on 2009-05-25
How do you get your boot times so low? On my system Ubuntu 9.10 boots in about 50 sec.
That is from pushing the power button, logging in, then opening the terminal to start conky.

With 9.04 it was about 55 sec.

---

### Post by taavikko on 2009-05-25
My desktop KDE running 9.04 boots ~14s (coreI7 barracuda 7200.11 1TB)
Laptop Gnome 9.10 boots ~17s (Athlon QL-62 (dual-core) and some crappy hdd)

---

### Post by ghindo on 2009-05-25
> **tad1073 said:**
> How do you get your boot times so low? On my system Ubuntu 9.10 boots in about 50 sec.
That is from pushing the power button, logging in, then opening the terminal to start conky.

With 9.04 it was about 55 sec.I think it depends a lot on how you define a full boot.  If you mean from the time you press the power button to after you've logged in and your hard drive goes idle, it's probably going to be a bit longer than if you just measured from the time you press the power button to GDM.

---

### Post by davideotape on 2009-05-25
> **tad1073 said:**
> How do you get your boot times so low? On my system Ubuntu 9.10 boots in about 50 sec.
That is from pushing the power button, logging in, then opening the terminal to start conky.

With 9.04 it was about 55 sec.

Boot times talked about are often those that start from grub passing on control to the boot sequence to gsm appearing. This is because 1. Bios is beyond control of ubuntu and 2. You could have lots of startup programs and fancy compiz effects that slow the loading of programs.

---

### Post by gjoellee on 2009-05-25
I don't think the Ubuntu developers will reach that goal for Karmic. I think it is possible to boot in 10 seconds, but for Ubuntu that won't be in Karmic unless you manually remove about all the daemons or something like that.

---

### Post by tad1073 on 2009-05-25
so, your saying that 50 sec. is fairly fast?

---

### Post by ghindo on 2009-05-25
> **gjoellee said:**
> I don't think the Ubuntu developers will reach that goal for Karmic. I think it is possible to boot in 10 seconds, but for Ubuntu that won't be in Karmic unless you manually remove about all the daemons or something like that.Why don't you think Ubuntu devs can achieve this?  I mean, we've seen[ five-second boots]("http://lwn.net/Articles/299483/") before, why is ten seconds such an insurmountable task?

---

### Post by MacUntu on 2009-05-25
> **tad1073 said:**
> How do you get your boot times so low? On my system Ubuntu 9.10 boots in about 50 sec.
That is from pushing the power button, logging in, then opening the terminal to start conky.

With 9.04 it was about 55 sec.

Most boot times you see are GRUB -> GDM because that's what bootchart measures by default. GRUB -> GDM is pretty good with newer kernels but the time it takes to load the Gnome session should (could?) be improved.

As for "not possible": [http://img.xrmb2.net/images/396964.png](http://img.xrmb2.net/images/396964.png) :P Just a kernel "light" and some readahead optimization. I'm sure with SSDs being the future boot times won't be an issue at all.

---

### Post by davideotape on 2009-05-25
> **tad1073 said:**
> so, your saying that 50 sec. is fairly fast?

Depends. A lot of the variables include hardware and bios, which are totally outside the os's control.

---

### Post by garba on 2009-05-25
well getting rid of silly messages like "grub loading stage 1.5" might save 1 cpu cycle, that could be a start ;)

---

### Post by MacUntu on 2009-05-25
> **garba said:**
> well getting rid of silly messages like "grub loading stage 1.5" might save 1 cpu cycle that could be a start ;)

Does GRUB2 come with such useless messages? I've seen GRUB2 being a topic at UDS.

---

### Post by tad1073 on 2009-05-25
> **garba said:**
> well getting rid of silly messages like "grub loading stage 1.5" might save 1 cpu cycle that could be a start ;)

How does one get rid of that message?

---

### Post by inportb on 2009-05-25
One closes the eyes...

---

### Post by vade on 2009-05-25
> **ghindo said:**
> Why don't you think Ubuntu devs can achieve this?  I mean, we've seen[ five-second boots]("http://lwn.net/Articles/299483/") before, why is ten seconds such an insurmountable task?
To achieve the 5 second boot a lot of tampering with fundamental parts of the system was required which may break things under some configurations. Ubuntu needs to make sure that everything works under every configurationn so they can't do anything too crazy with the boot process.

Anyways Jaunty already bootcharts in 12 seconds on my system, which has no SSD, so 10 seconds is very possible on some systems even witrhout an SSD. But some systems will never boot in 10 seconds, not even 20 or 30. Because of the hardware.

---

### Post by garba on 2009-05-25
> **tad1073 said:**
> How does one get rid of that message?

helping the devs improve their common sense, for instance ^^ I am quite fond of this bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/131389](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/131389)

:D

---

### Post by Totzo on 2009-05-25
Boot times aside, I've been having a play with debian unstable of late and am very impressed with the speed of everything in comparison with ubuntu. I'm a long time fan of ubuntu (since the warty days) but have noticed it becoming increasingly slow over the last few releases where most things are concerned. I understand that simplicity of use is of the utmost importance but should that compromise performance?

---

### Post by inportb on 2009-05-25
Well, yes. In the days of ever faster computers, it is natural that some resources be dedicated to making the whole computing experience smoother. Unfortunately, not all computers are up to the challenge =/

---

### Post by Regenweald on 2009-05-25
grub2 + enhanced upstart ?

---

### Post by vishalrao on 2009-05-26
Yes, the 10 sec comment in the video was jokingly mentioned, sabdfl quirked "12 sec is also okay as long as its purdy (pretty)" and there was more laughter and applause... I do hope and I will be very impressed if they achieve 10 sec GRUB to GDM boot :)

---

### Post by TrueTom on 2009-05-26
> **garba said:**
> helping the devs improve their common sense, for instance ^^ I am quite fond of this bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/131389](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/131389)

:D

Funny. Every time I see some BS going on in a Launchpad bugreport there is usually the same person involved.

---

### Post by Seventh Reign on 2009-05-26
I'd be happy if it took 24 hours to boot up, if it meant you only had to reboot once every 5 years, and it NEVER crashed.

---

### Post by davideotape on 2009-05-26
> **Seventh Reign said:**
> I'd be happy if it took 24 hours to boot up, if it meant you only had to reboot once every 5 years, and it NEVER crashed.

That was the general consensus on irc during the uds session, as long as there was a very good hibernation option. Then again, that was before we started wondering about -2s boots and whether Mark Shuttleworth was dr who.

---

### Post by MacUntu on 2009-05-26
> **vishalrao said:**
> Yes, the 10 sec comment in the video was jokingly mentioned, sabdfl quirked "12 sec is also okay as long as its purdy (pretty)"

Thanks. ;)

"Scotty, we need to boot faster."
"Captain, it takes 20 seconds at least."
"I give you 12."
"I'll do it in 10."

[img]http://cache.gizmodo.com/assets/images/gizmodo/2008/08/star-treks-scotty.jpg[/img]

---

### Post by TrueTom on 2009-05-26
+1 for obscure Zapped quote.

---

### Post by ghindo on 2009-06-09
Scott Remnant recently gave a pretty thorough explanation on the ubuntu-devel list about boot time for Karmic and Karmic+1:

[https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028308.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028308.html)

Interesting read; definitely worth checking out.

---

### Post by diebels on 2009-06-09
[QUOTE=https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028308.html]10s is a good number, especially for a generic, hardware agnostic,
non-stripped down Linux distribution.  From that starting point,
development teams will be able to customise and tailor Ubuntu for
specific hardware - and the OEM team will be able to produce custom
Remixes of Ubuntu that boot even faster.

I think it likely that we'll match Moblin's 5s benchmark on similar
hardware, with a device-tailored Moblin-based remix of Ubuntu.

(The 2s benchmark is afaict mostly aimed at the Automotive industry,
 and for specialist devices rather than computing devices)

And just to affirm something we've already stated; this benchmark time
is to a fully logged in desktop (auto-login) with an idle CPU and Disk.
Deferring services is not an option unless done properly (ie. switching
services from startup to on-demand activation).[/QUOTE]

Note the detail on fully logged in desktop. The time is NOT to GDM as everybody has assumed.

---

### Post by olskar on 2009-06-09
> **diebels said:**
> Note the detail on fully logged in desktop. The time is NOT to GDM as everybody has assumed.

That is great

---

### Post by 23meg on 2009-06-09
It's worth emphasizing that the 10 second(ish) boot speed target is a target for Ubuntu 10.04, **not Karmic**.

---

### Post by gnomeuser on 2009-06-09
> **olskar said:**
> That is great

Well that just leaves us with a bunch of interesting problems. This will probably lead to a push to make automatic login the default which is insecure. Additionally on automatic login there is no password to unlock the keyring so the first thing greeting a user would very likely be network manager asking for you to unlock the keyring.

Similar problems face the encrypted homedir space.

There are interesting challenge with this approach, I am unsure how to approach them if at all. Personally I find the quick boot appealing but the tradeoff in security seems problematic. Once I am logged in and connected to a network all my information is right there, regular people store passwords for things like paypal in the Firefox key store.. It does not take a lot of brain power to imagine the kind of fun people might have with a stolen laptop like that. 

Not that requiring a password at login is automatically unbreakable but it at least something.

---

### Post by gnomeuser on 2009-06-09
> **23meg said:**
> It's worth emphasizing that the 10 second(ish) boot speed target is a target for Ubuntu 10.04, **not Karmic**.

Please change the thread title in that case.

---

### Post by 23meg on 2009-06-09
> **gnomeuser]This will probably lead to a push to make automatic login the default which is insecure. [/QUOTE]

I have yet to see any indication towards that said:**
> Please change the thread title in that case.

I was just thinking of that; done.

---

### Post by MacUntu on 2009-06-09
Time to get that reference platform. :p

Do I need to be part of the Launchpad team to subscribe to ubuntu-boot? I'm just curious but wouldn't be an active member...

---

### Post by hexsel on 2009-06-09
> **gnomeuser said:**
> Well that just leaves us with a bunch of interesting problems. This will probably lead to a push to make automatic login the default which is insecure. ...

Bah every time I read a inflammatory of someone overreacting to some other user, you're at it.

Truly, it appears that they are MEASURING the time as if automatic login is on, but that does NOT mean they will make that the default.

Although, since most computers are used by a single person anyway (specially laptops), I'm not entirely sure most users wouldn't trade security for convenience (see the social networks phenomenon).  I would, and have it on by default - pisses me off that I can't connect to the wireless network without entering my password anyway (even tried a few hacks to AppArmor that didn't do anything).

---

### Post by taavikko on 2009-06-09
~10s is ambitious goal.
and as hardware is getting more powerful it shouldn't pose any real difficulties. but for ppl using older hardware...

Currently my Core7 goes 11s to kdm.
Which doesn't really matter, since it gets rebooted not-so-often.

If targeting 10s that could only mean that certain services are started 
only on first access. e.g Cups.
which could lead to more trimmed down desktop (always a nice idea)
which is then again more important to older hardware than purdy fast boot.

Have no idea what I was after with this post :D
EDIT// who changed the title :) I was tossing my head for 9.10, but no biggie.

---

### Post by diebels on 2009-06-09
> **hexsel said:**
> 
Truly, it appears that they are MEASURING the time as if automatic login is on, but that does NOT mean they will make that the default.

Although, since most computers are used by a single person anyway (specially laptops), I'm not entirely sure most users wouldn't trade security for convenience (see the social networks phenomenon).  I would, and have it on by default - pisses me off that I can't connect to the wireless network without entering my password anyway (even tried a few hacks to AppArmor that didn't do anything).

Well said=D>

I also got pissed off by the wireless thing and switched to wicd. I switched back to network manager when it was fixed. You just click the enable for all users in edit connections.

With physical access there is no security anyway. Just fire up single user mode!

---

### Post by olskar on 2009-06-09
> **hexsel said:**
>  I would, and have it on by default - pisses me off that I can't connect to the wireless network without entering my password anyway (even tried a few hacks to AppArmor that didn't do anything).

Having an empty password for the keyring works

---

### Post by NCLI on 2009-06-09
> **olskar said:**
> Having an empty password for the keyring works
I think this would be preferrable(for security reasons):
> **diebels said:**
>  ... just click the enable for all users in edit connections.

---

### Post by jbruced on 2009-06-09
> **inportb said:**
> One closes the eyes...

first online laugh today, thanks.

---

### Post by gnomeuser on 2009-06-09
> **23meg said:**
> I have yet to see any indication towards that; can you cite any, or is it just your speculation? It's been my impression that the automatic login is used merely for benchmarking; the actual login speed would be ~10s + whatever time it takes to get past GDM.


Looking that outline presented as posted by Scott James Remnant on ubuntu-devel today:

> 
..snip...

And just to affirm something we've already stated; this benchmark time
is to a fully logged in desktop (auto-login) with an idle CPU and Disk.
Deferring services is not an option unless done properly (ie. switching
services from startup to on-demand activation).

..snip..
Budgets.

I've split the boot into a few obvious sections, and given each one a
time budget. *To reach the target of 10s, each of these sections needs
to be at or under its budget.

*2s *Kernel and initramfs.

* * *This includes both, since arguably the need for an initramfs is a
* * *kernel implementation detail anyway (the kernel can mount the root
* * *filesystem itself in many circumstances)

*2s *Plumbing

* * *This is for driver loading, filesystem mounting, general busy
* * *work, etc.

*2s *X.org server

* * *Includes the display manager that actually starts it. *Also
* * *includes any services required for the user's session that can be
* * *started alongside the X server

*4s *Desktop session

* * *Everything from the window manager, file manager to the panel and
* * *its applets. *Also includes any services they require.


If we profile using automatic login that is a different path than going to GDM. It would not give the same results if we switched, especially since a lot of this is likely going to rely on layout of files and reading them smartly. Not to say impossible to apply the work across those two solutions (and more if you bring in Kubuntu and friends to the party) but this does seem very minded at a different target than our standard Ubuntu.

Now the decision to pick one or the other is likely going to be up for debate, and it's also a decision that can absolutely be made based on the purpose of the remix. The desktop standard Ubuntu we have today might well stay gdm bound whilst UNR/Moblin could do automatic login. 

Sure it might work and at least anything except the last 4 seconds for the desktop session would be the same, but I assume one actually optimizes for the reality one elects to live in. If the plan looks to optimize for automatic login it is natural to think that it will at least be considered - it's not an all together unnatural thought, e.g. openSUSE' GNOME release does automatic login by default. So we have major distros doing this.

All I am saying is that if there is a push to do automatic login even on a separate remix, it is worth considering that these are different codepaths. It is also worth noting that there are other problems we should not let surprise us by going this route. 

As (nearly) always I don't mean problems as being a bad thing, I think that historically everytime we are forced to sit down and evaluate the situation and our desires for the future we have improved Linux as a whole. We should embrace problems and view them as a challenge to come up with elegant and creative solutions.

---

### Post by zekopeko on 2009-06-09
^^^^^^
well couldn't GNOME be loaded in the background while you wait at GDM?

---

### Post by Gourgi on 2009-06-09
> **zekopeko said:**
> ^^^^^^
well couldn't GNOME be loaded in the background while you wait at GDM?

what if i want to start fluxbox and not Gnome?

---

### Post by Wiebelhaus on 2009-06-09
> **ghindo said:**
> We knew from [the beginning]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html") that Karmic was supposed to have a faster boot time, but at UDS, it looks like the developers are aiming for a 10-second boot time with Karmic.

[http://identi.ca/notice/4558529](http://identi.ca/notice/4558529)
[http://twitter.com/szilveszter/statuses/1946601057](http://twitter.com/szilveszter/statuses/1946601057)

Watch Mark Shuttleworth talk about it (mentions it at 1:20):  [http://www.youtube.com/watch?v=t3PJPYWtJ9o](http://www.youtube.com/watch?v=t3PJPYWtJ9o)

You think he was serious? it sounded a bit like a joke.

Serious question I'm not being facetious.

---

### Post by hachaboob on 2009-06-10
I think we will have to wait for SATA3 and SSDs that take advantage of 6Gb/s before breaking the 10s barrier.

---

### Post by ghindo on 2009-06-10
> **hachaboob said:**
> I think we will have to wait for SATA3 and SSDs that take advantage of 6Gb/s before breaking the 10s barrier.It's already been done.  A fast boot isn't really a matter of raw speed; it seems to me it's more a matter of optimizing and prioritizing services.  Read the rest of the thread to see what I mean.

---

### Post by gnomeuser on 2009-06-10
> **Gourgi said:**
> what if i want to start fluxbox and not Gnome?

Fedora used to have a project called Early gdm. The idea was to get gdm up and running as soon as possible and then complete the boot in the background while the user was typing his password. This approach had a number of issues but it worked.

As is pointed out though, you incure a heavy penalty if you preload the wrong desktop session. Due to the way things work, I suspect this might be possible but there are still tasks that couldn't complete without an actual login having been performed. Something like unlocking the keyring can't be done without a password, if we haven't got the password we can't connect to the network. Which all leads to this being unsuitable for preloading. There is sure to be other fun little corners to examine as well.

---

### Post by Reiger on 2009-06-10
The real problem (in general, networking is a special case of this) is the various daemons that must be started as root, then drop to some other (dumb) user. Think apparmor, pulseaudio etc. etc.

---

### Post by MacUntu on 2009-06-10
> **gnomeuser said:**
> If we profile using automatic login that is a different path than going to GDM. It would not give the same results if we switched, especially since a lot of this is likely going to rely on layout of files and reading them smartly.

If you profile the boot process till usable desktop you'll unlikely read more than 200MB so this should be done in two seconds or less anyway.

There is virtually no difference between automatic login boot time and boot time - time to log in. So no, I see no indication that anyone wants to make automatic login default.

---

### Post by zekopeko on 2009-06-10
> **gnomeuser said:**
> Fedora used to have a project called Early gdm. The idea was to get gdm up and running as soon as possible and then complete the boot in the background while the user was typing his password. This approach had a number of issues but it worked.

As is pointed out though, you incure a heavy penalty if you preload the wrong desktop session. Due to the way things work, I suspect this might be possible but there are still tasks that couldn't complete without an actual login having been performed. Something like unlocking the keyring can't be done without a password, if we haven't got the password we can't connect to the network. Which all leads to this being unsuitable for preloading. There is sure to be other fun little corners to examine as well.

well you login into your default session. GDM knows that you want GNOME/KDE or something else. and pulling the rest of your default session shouldn't be a problem, should it?

---

### Post by gnomeuser on 2009-06-10
> **zekopeko said:**
> well you login into your default session. GDM knows that you want GNOME/KDE or something else. and pulling the rest of your default session shouldn't be a problem, should it?

It is because of the previously mentioned chicken and egg problem type. Anything that relies on being run in the session that requires access to the keyring e.g. cannot be run to completion. There are likely other problems where we even have to run things system wide to login thus slowing boot in other places instead of the session handling or continue doing what we do.

There may also be concerns with regards to information leaks if you load things outside the session that belongs under the session, I don't know enough about that area to say for sure. I will though attempt to research this.

But yes, we can, and do, preload a lot of information about session login. The biggest speedups for the desktop session is likely going to be:

Compiz, which takes forever to start up.
GConf roundtrip reductions which have been done upstream (thank you to Micheal Meeks over at Novell for that profiling and hacking).
gnome-panel which also loads pretty slowly currently.

There are other tricks to play, if we want the same speedups for other environments similar profiling efforts will need to be undertaken. I don't know if the KDE and Kubuntu people e.g. plan doing the same session profiling work.

One reason why we may not actually want to do the session part for Karmic is that for Karmic+1 we hit the release of GNOME3 which brings with it a replacement for gnome-panel (gnome-shell) and a replacement for GConf (dconf), and it aims to replace compiz with the clutter port of Metacity known as Mutter. DConf especially being much better designed for the performance cases we see as problem areas currently. In effect these replacement products would obsolete a large amount of work after 6 months which is kind of suboptimal from the "I pay my developers to produce lasting improvements" pov. Effort is probably better spend focusing on the upcoming targets.

---

### Post by diebels on 2009-06-10
> **gnomeuser said:**
> Looking that outline presented as posted by Scott James Remnant on ubuntu-devel today:

If we profile using automatic login that is a different path than going to GDM. It would not give the same results if we switched, especially since a lot of this is likely going to rely on layout of files and reading them smartly. Not to say impossible to apply the work across those two solutions (and more if you bring in Kubuntu and friends to the party) but this does seem very minded at a different target than our standard Ubuntu.


What are you on about here? Different path?

*2s *X.org server

* * ***Includes the display manager that actually starts it**. *Also
* * *includes any services required for the user's session that can be
* * *started alongside the X server

So there are no different paths are there? You just check the box for automatic login in gdmsetup if you like automatic login, if you don't you uncheck it.

There are probably much support for the security concerns, so the autologin will be off by default. But the wireless password available for all users without use of keyring should be default in my opinion. (The checkbox for "Available to all users" should be checked by default for wireless connections in the nm-connection-editor.)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=117100&d=1244630595[/IMG]

---

### Post by castrojo on 2009-06-10
> **gnomeuser said:**
> Compiz, which takes forever to start up.
GConf roundtrip reductions which have been done upstream (thank you to Micheal Meeks over at Novell for that profiling and hacking).
gnome-panel which also loads pretty slowly currently.

Nautilus is the third broken thing here. 

> One reason why we may not actually want to do the session part for Karmic is that for Karmic+1 we hit the release of GNOME3 which brings with it a replacement for gnome-panel (gnome-shell) and a replacement for GConf (dconf), and it aims to replace compiz with the clutter port of Metacity known as Mutter.

It hasn't been determined when Ubuntu will ship -shell by default. Everyone at the GNOME3 session at UDS was leaning towards "no" for the next LTS, but we'll see. 

> DConf especially being much better designed for the performance cases we see as problem areas currently.

Ryan Lortie was at UDS and explained to us the state of DConf. It's probably not LTS-ready either, but definitely will be awesome at some point.

(Please note, even if all the GNOME3 stuff isn't shipped by default it will be trivial to use it for people who want it, we're committed to that.)

---

### Post by jsmidt on 2009-06-10
The new Fedora 11 is booting up in ~20-25 seconds for most people, about twice as fast as it was a year ago with KMS+Plymouth.

If they can cut their boot time in half again in a year, Fedora should have ~10 second boot with KMS+Plymouth as well.

---

### Post by ghindo on 2009-06-10
The Ubuntu project to reduce boot time has been mentioned in Ars Technica:

[http://arstechnica.com/open-source/news/2009/06/ubuntu-aims-for-ten-second-boot-time.ars](http://arstechnica.com/open-source/news/2009/06/ubuntu-aims-for-ten-second-boot-time.ars)

---

### Post by rajeev1204 on 2009-06-11
My IBM Thinkcenter Windows XP desktop used to boot in 6-10 sec flat .IBM do a lot of tweaKING of their own and well if you know what to change in XP, it can boot as quick on any system.And this 10 sec boot was from power button to desktop screen.


9.04 takes around 20 sec on my system from power button to desktop screen,so nothing spectacular here.

---

### Post by golusweet on 2009-06-11
> **rajeev1204 said:**
> My IBM Thinkcenter Windows XP desktop used to boot in 6-10 sec flat .IBM do a lot of tweaKING of their own and well if you know what to change in XP, it can boot as quick on any system.And this 10 sec boot was from power button to desktop screen.


9.04 takes around 20 sec on my system from power button to desktop screen,so nothing spectacular here.


Streamlined Windows XP boots in 20 seconds with tweaking.

---

### Post by MacUntu on 2009-06-11
And you can take out your hard disk and put it let's say in an AMD-based PC? :popcorn:

XP indeed is a fast booter but the time of high CPU/IO-load after you see the desktop is way to long (like I have to wait for the panel in Gnome).

---

### Post by rajeev1204 on 2009-06-11
> **MacUntu said:**
> And you can take out your hard disk and put it let's say in an AMD-based PC? :popcorn:

XP indeed is a fast booter but the time of high CPU/IO-load after you see the desktop is way to long (like I have to wait for the panel in Gnome).


This was an intel P4 with 768 MB! Ram ,no audio etc ,super machine indeed then.Of course intel onboard all things.So its got nothing to boot really :)

And that 10 sec boot time is a fact btw,and like i said IBM did do a good job with their thinkcenters.It was a workstation system btw.Not a regular system, so had a special mobo etc.
In 9,04,most of my boot time is taken up initialising the X server and then on to the panel.

---

### Post by rajeev1204 on 2009-06-11
> **golusweet said:**
> Streamlined Windows XP boots in 20 seconds with tweaking.


Depends on what kind of system you have.You say it like its a scientific number .There are no fixed times for boot,only average times.

Also,like many mention on this thread,it depends a lot on what apps you have at startup,and a lot of other factors.

---

### Post by gnomeuser on 2009-06-11
> **whiprush said:**
> Nautilus is the third broken thing here. 

It hasn't been determined when Ubuntu will ship -shell by default. Everyone at the GNOME3 session at UDS was leaning towards "no" for the next LTS, but we'll see. 

Ryan Lortie was at UDS and explained to us the state of DConf. It's probably not LTS-ready either, but definitely will be awesome at some point.

(Please note, even if all the GNOME3 stuff isn't shipped by default it will be trivial to use it for people who want it, we're committed to that.)

True, that is going to be a factor to consider. Personally I have a lot of confidence in everyones ability to create and maintain good software. I look forward to taking it for a spin.

I hope we might see at least a separate technology preview edition shipped with GNOME3. I think that if we can't get it beaten into submission by LTS time something like that would make everyone happy and serve the testing agenda in some released capacity.

---

