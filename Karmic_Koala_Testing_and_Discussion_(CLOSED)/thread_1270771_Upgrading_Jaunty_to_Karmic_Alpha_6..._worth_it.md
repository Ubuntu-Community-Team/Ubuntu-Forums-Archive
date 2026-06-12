---
title: "Upgrading Jaunty to Karmic Alpha 6... worth it?"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by humphreybc on 2009-09-20
Hi there,

I need some opinions on whether it's a wise move to upgrade to Karmic Alpha 6 to fix a bug that I'm having.

Okay, so [here is the bug.]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/423711")

At the moment I can't get drivers above Catalyst 9.4 to work on my current setup. Now this would be fine IF I hadn't just bought a Dell 24" widescreen full 1080p monitor to plug my laptop into, which I want to run dual screen with my laptop, have the Monitor as a 2nd desktop which I can drag windows across to, ALL with compiz enabled.

According to [this]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1135612&page=1") thread here, what I want to do will not work with 9.4, but appears to get better as ATI fixed the problem between Catalyst 9.5 - 9.9.

So my question is, do you think upgrading to Alpha 6 from Jaunty will introduce more problems than it's worth to fix this one bug?

Thanks
Benjamin

P.S How does one upgrade to an Alpha version anyway? I presume it involves adding stuff to your sources list, but what stuff...

---

### Post by scragar on 2009-09-20
Don't upgrade to an alpha release, they are buggy, odds are your system will be rendered useless more than once before the official release.

Instead see if you can download the software you need using packages.ubuntu.com and the search box, you want to set the release to karmic, and you'll probably have to manually download some dependencies, although I cannot be possitive.

---

### Post by Paqman on 2009-09-20
Wait for the final release. Karmic is still a bit rough, we've seen a _lot_ of broken systems over the last week or two. 

It's going to be great when it's finished, but it just ain't.

---

### Post by humphreybc on 2009-09-20
Okay, so could you help me work out what packages I need to install?

This is apparently the fixed package: [https://launchpad.net/ubuntu/+source/fglrx-installer](https://launchpad.net/ubuntu/+source/fglrx-installer)

But I have already tried that and it didn't really work...

---

### Post by scragar on 2009-09-20
[http://packages.ubuntu.com/karmic/fglrx-amdcccle](http://packages.ubuntu.com/karmic/fglrx-amdcccle)

OR

[http://packages.ubuntu.com/karmic/xorg-driver-fglrx](http://packages.ubuntu.com/karmic/xorg-driver-fglrx)

Honestly I think they'd depend on each other anyway, so install both(and any dependencies you'll need before it will let you install them).

---

### Post by Copernicus1234 on 2009-09-20
I had planned to, but have decided to wait for the first few betas since things still break now and then when doing updates.

---

### Post by humphreybc on 2009-09-20
> **scragar said:**
> [http://packages.ubuntu.com/karmic/fglrx-amdcccle](http://packages.ubuntu.com/karmic/fglrx-amdcccle)

OR

[http://packages.ubuntu.com/karmic/xorg-driver-fglrx](http://packages.ubuntu.com/karmic/xorg-driver-fglrx)

Honestly I think they'd depend on each other anyway, so install both(and any dependencies you'll need before it will let you install them).

Should I uninstall my 9.4 drivers first, or just install these packages, then uninstall 9.4 and install 9.9?

---

### Post by scragar on 2009-09-20
> **humphreybc said:**
> Should I uninstall my 9.4 drivers first, or just install these packages, then uninstall 9.4 and install 9.9?

It's an upgrade, you shouldn't need to uninstal anything.

---

### Post by moviemaniac on 2009-09-20
My brother upgraded from Jaunty a few days ago (also having had troubles with the previous fglrx drivers) and it was smooth sailing. Everything worked and works as it should (apart from the known bugs affecting every system right now...)

---

### Post by humphreybc on 2009-09-20
Well that didn't work at all. I upgraded to the newer fglrx packages manually, then uninstalled 9.4 and installed the newest ATI drivers, 9.9 and I've still got the same problem.... ****** boot splash screen, "low graphics mode" when I start up that is unusable because it can't start on display 0 etc etc etc

How the hell do you fix this, it's beginning to really piss me off that I cannot install anything higher than 9.4

---

### Post by ranch hand on 2009-09-20
I would just wait until 9.10 is ready.

As of today it seems to work well.  For the last 7 to 10 days it has been very weird.  I would not upgrade any system that I am trying to use to 9.10.

It has a lot of very basic changes in it and there is going to be some pain in doing this.

It is, I think, going to be worth the wait.

Try not to get your panties in a bunch and HAVE FUN.

---

### Post by itchy8me on 2009-09-20
definitely going to be worth the wait.

Been running karmic for a while now, and i have to say that there's been accelerated development taking place on many fronts. The ones i've been eyeing are bluetooth support and pulseaudio.. looking good, very good. The bluez team have been working very hard the last couple of months. respect!

unfortunately this weekends updates broke my desktop and laptop installations. So i wouldn't upgrade if you have a critical system!

---

### Post by humphreybc on 2009-09-20
> **itchy8me said:**
> definitely going to be worth the wait.

Been running karmic for a while now, and i have to say that there's been accelerated development taking place on many fronts. The ones i've been eyeing are bluetooth support and pulseaudio.. looking good, very good. The bluez team have been working very hard the last couple of months. respect!

unfortunately this weekends updates broke my desktop and laptop installations. So i wouldn't upgrade if you have a critical system!

Regarding the better bluetooth support, do you know if they have fixed the bug where Toshiba laptop users cannot turn on bluetooth unless they go back into Windows and enable it? This would be all good except that I don't have windows on my computer anymore...

---

### Post by itchy8me on 2009-09-20
that i dont know.

by the way, i think updating the fglrx drivers is not enough, you'll have to do a full upgrade with "do-release-upgrade -d" and sudo apt-get dist-upgrade"

---

### Post by humphreybc on 2009-09-20
> **itchy8me said:**
> 
by the way, i think updating the fglrx drivers is not enough, you'll have to do a full upgrade with "do-release-upgrade -d" and sudo apt-get dist-upgrade"

I'll just wait for karmic to come out then.

Cheers

---

### Post by matthew.ball on 2009-09-21
Slightly off-topic, rather than the Alpha releases, would you recommend Beta?

From Intrepid, I jumped over when Jaunty hit Beta, and I have had no issues (if anything Jaunty beta was better than Intrepid, so I probably have a bad base line example to use), I was thinking of upgrading again when Karmic hits Beta...

This machine has nothing *important*, single-install, separate /home partition, I only use it for school work, and have all the work backed up on my student account.

---

### Post by ranch hand on 2009-09-21
Well, we are 10 days, roughly, from beta and things are pretty rough still.  There are a number of things that need a lot of work.

All that work is sure to cause some more problems.  This is not a release or even a release candidate.  There is a solid 5 weeks yet until the release date.

If you are talking about putting this on as a production OS I think you are nuts.

You don't eat a meal until it is ready.  You may need to do a lot of tasting to get it finished right but you are not eating it.

Give this bugger a chance to get done.  It really will be worth the wait.

---

### Post by xebian on 2009-09-21
Worth every penny.  

Just upgraded my laptop Kubuntu jaunty to karmic, and am now posting with it right now.  I  have to do 1 aptitude safe-upgrade but had to do 3 more apt-get dist-upgrade to complete.  It wasn't completely smooth but no heavy liftng.  knetworkmanager won't connect but the trusty old ifup/down network interfaces configuration saved the day.  Installed the plasma-widget-network-manager ( which removes the netwotk-manager-kde ).  Reboot, and wireless was easy as a pie.  Using BCM4318 btw.  Eye candy is also great using xserver-xorg-video-radeon drivers on ATI x200m card.

---

### Post by humphreybc on 2009-09-21
Do you know what version of Catalyst drivers are shipped with Karmic? They're usually a few versions behind the ones available from ATI direct... which is a shame. I wish ATI would submit the latest drivers to Ubuntu for inclusion in the updates straight away.

---

### Post by Seren on 2009-09-21
> **humphreybc said:**
> Do you know what version of Catalyst drivers are shipped with Karmic? They're usually a few versions behind the ones available from ATI direct... which is a shame. I wish ATI would submit the latest drivers to Ubuntu for inclusion in the updates straight away.

It is a pre-release version of catalyst 9.10 (supposed to be released in October but given in advance to ubuntu).

---

### Post by humphreybc on 2009-09-21
> **Seren said:**
> It is a pre-release version of catalyst 9.10 (supposed to be released in October but given in advance to ubuntu).

Oh cool, so when I upgrade to Karmic when it comes out I don't have to download and install drivers from ATI, I can just install the xorg-driver-fglrx package from the repos and this will be 9.10?

Will xorg-driver-fglrx be updated when 9.11/9.12 etc onwards come out?

---

