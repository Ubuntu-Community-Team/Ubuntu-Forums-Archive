---
title: "To upgrade or not to upgrade?"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by fINTiP on 2008-11-01
Perhaps it's a little soon, but...

I've never really upgraded an ubuntu distro before. I've just done several different installs on different computers. I entered in to ubuntu on 7.10, at one point tried using 6.04 on an older computer, and have stuck with 8.04 for a long time.

So I'm relatively new to the LTS philosophy. I had thought to myself that I would stick with Hardy when I got it, because a stable LTS with all issues resolved sounded nice. 

But does this mean that things like a tabbed nautilus are not an option for me? Getting the upgraded X.org would be a problem? Upgrading my Kernel sounds like a big deal- is that possible without doing an entire upgrade to 8.10?

I'm still working on getting the kinks out of my system on 8.04, upgrading to 8.10 sounds foolish. But I still want the gizmos. Is there an in between option? Will the LTS receive all of these updates?

Short version: What are the pros and cons of sticking with the LTS vs. upgrading every time?

L

---

### Post by Craige4107 on 2008-11-01
> **fINTiP said:**
> Perhaps it's a little soon, but...

I've never really upgraded an ubuntu distro before. I've just done several different installs on different computers. I entered in to ubuntu on 7.10, at one point tried using 6.04 on an older computer, and have stuck with 8.04 for a long time.

So I'm relatively new to the LTS philosophy. I had thought to myself that I would stick with Hardy when I got it, because a stable LTS with all issues resolved sounded nice. 

But does this mean that things like a tabbed nautilus are not an option for me? Getting the upgraded X.org would be a problem? Upgrading my Kernel sounds like a big deal- is that possible without doing an entire upgrade to 8.10?

I'm still working on getting the kinks out of my system on 8.04, upgrading to 8.10 sounds foolish. But I still want the gizmos. Is there an in between option? Will the LTS receive all of these updates?

Short version: What are the pros and cons of sticking with the LTS vs. upgrading every time?

L
Pros sticking with the LTS?  Your OS works.  Read from the list of problems related to this release.  It truely wasn't ready to be released yet.  I tried 3 times to upgrade or or fresh install.  At different points, there was serious issues, to the point that I had to reload my Windows OS.  Upgrade at your own risk.  Good luck.

---

### Post by Rbchound on 2008-11-01
I concur.  Wait until the bugs are worked out before upgrading to 8.10.  Me personally, I am having tons of issues.  I am going to reload Hardy tomorrow.  I have my home folder on a separate partition, so re installation should be a breeze.  Just in case I am backing up my home folder to another hard drive.

---

### Post by rage-against-windows on 2008-11-01
Ive had zero problems since upgrading to 8.10 from 8.04. I wanted to upgrade due to the wireless aircard support offered in 8.10, and it runs my sprint compass 597 perfectly. I was expecting a bug or 2 but so far so good on my old HP Compaq nx6110 with 715 megs of ram, it runs like a dream. I plan on upgrading the desktop in the next few days, Ill let you know how it goes.

---

### Post by Declanthedork on 2008-11-01
I upgraded and ran in to some problems with the installer. So, no. Wait until it's more stable.

---

### Post by sondosia on 2008-11-01
Just wondering, when do you think Ibex will be "more stable"? Do I have to wait for 9.04 to come out?

---

### Post by fINTiP on 2008-11-07
That's a good question... that's one of the reasons I want to stick with 8.04- it will have enough time to eventually have all the bugs shake out.

But no one has answered my questions- will I be able to update my kernel or update nautilus within 8.04 without problem, or will that mess up my 8.04 install altogether? Or will those come about by default as 8.04 continues to get support?

L

---

### Post by Pumalite on 2008-11-07
I have upgraded without problem, but I'd tell you that when I have an OS that I like and it works; I stick to it.

---

### Post by petermck on 2008-11-07
I had no real problems with the upgrade but unless there is something you really need in 8.10 like the 3G wireless support I would stick with 8.04 for a few months. A browse of the forum shows that there are some problems with Nvidia drivers, slower boot times and a mixed bag of other graphics and I/O issues, but a very common one seems to be slow downloads of the upgrade and interrupted upgrades. Unless you have a fast, stable network connection I'd stick with 8.04.

---

### Post by TimGS on 2008-11-07
Hi L,

Read this [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) which talks about the backports repository. If you includes this in your sources you will receive updates on some packages beyond the usual security updates and bug fixes (I believe it is an Ubuntu policy to 'freeze' the included packages at release time, and to only supply security updates and bug fixes in the default repos).

That doesn't guarantee of course that what you are looking for will be included there. I wouldn't have thought that you'd be finding newer Kernels or editions of Gnome in there.

You could try installing newer .deb packages with "dpkg -i packagename" but I don't know if doing this with something like Gnome would cause problems with some of the Ubuntu-specific packages that expect the 'normal' Gnome version for your version of Ubuntu.

Personally I'd stick with Hardy. There seems a point of diminishing returns in terms of time spent in trying new distros or new versions of distros that is quickly reached.

-- Tim.

---

### Post by jerrylamos on 2008-11-07
DON'T upgrade to 8.10 if you have Intel video graphics chips.  

The upgrade won't boot without workarounds, see Launchpad Bug #259358.

Since I try early levels of Ubuntu, I use dual boot.  Make sure! the new one is working before using it as the main.

If you look over Ubuntu Forums Installation & Upgrades, make careful note of any people having trouble with the same hardware you have.

Jerry

---

### Post by sub_acoustic on 2008-11-07
or if you have an ATI card, don't do it, wait
my day has been ruined trying to sort this out, none of the posted fixes work for me

---

### Post by jengo on 2008-11-07
> **jerrylamos said:**
> DON'T upgrade to 8.10 if you have Intel video graphics chips.  

The upgrade won't boot without workarounds, see Launchpad Bug #259358.

Since I try early levels of Ubuntu, I use dual boot.  Make sure! the new one is working before using it as the main.

If you look over Ubuntu Forums Installation & Upgrades, make careful note of any people having trouble with the same hardware you have.

Jerry

I know what you mean, i have two friends lined up that want ubuntu on their systems. They both have intel graphics. This is one of the biggest nightmares ive ever had with ANY ubuntu release. I think im going to have to download a copy of 8.04 for them or something. I cant even get their systems to boot after install. :(

---

### Post by jengo on 2008-11-07
btw jerry, could you give me some links for a workaround?

---

### Post by cariboo on 2008-11-07
I would say upgrading depends on how competent a user you are. If you can repair problems without panicking, then go ahead and upgrade. Before upgrading have a look here:

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

For some upgrading is easy, for others it is a horror, it's up to you.

Jim

---

### Post by fINTiP on 2008-11-07
I do have an ATI- I'm actually trying to get advanced graphics working, have an open post in the desktop customization forum.... it's killing me trying to get that to happen.

I think I'm sticking with 8.04 simply because I want long term, don't want to spend time trying to fix stuff. I just want to spend time optimzing my current system- I still don't have my Pulse Audio stuff cleared up with skype and firefox, and have resorted to using epiphany a lot of the time now (to my chagrin, though I have been impressed with epiphany... for some reason I don't seem to have opera in my repositories, though I'd much rather be trying that).

I wish Ubuntu would slow down it's pace of release and spend more time polishing its releases... maybe they should adjust to a 9 month cycle. Seems like every release since I've been around gets the same "it's a nightmare" review when it comes out. 8.04, people said the same things, tons of problems, especially for an LTS. :\

L

---

### Post by Pumalite on 2008-11-07
If you have space in your hard drive; you could make space for a new OS and install 8.10 there as a clean install and dual or triple boot until you decide which one you like best. If you want to try; let us know.

---

### Post by Redrazor39 on 2008-11-07
Well, if you do a clean install, you're free from the upgrade woes people are complaining about. That's what I do every time. Usually I wait a month or two before upgrading so the kinks are worked out, but this time I couldn't resist. Intrepid is so much snappier and has a bunch of small fixes that make my computing experience better.

---

### Post by nhbubba on 2008-11-07
I would not..

Tonight I pulled down an iso, slapped together a (*fresh!*) vmware image and started playing around with 8.10 server. I have decided to sink some cash into a home-file server using real, non-surplus/reject hardware.

A short list of issues I have already run across:

[LIST]
[*][webmin seems to have fallen out of favor]("https://help.ubuntu.com/community/WebMin"). At work I have an ubuntu box racked in a lab far-far away. webmin has done nicely by me. (Given this particular install dates back to 7.04. Some here may have dealt with loosing this package long ago.) [ebox]("https://help.ubuntu.com/community/eBox") seems to be the suitable replacement. However it definitely does not seem to be what I am looking for. Even Ubuntu devs [seem to feel]("https://lists.ubuntu.com/archives/ubuntu-devel/2007-July/023984.html") that ebox != webmin. Fortunately installation from the deb packaging [looks easy]("http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html").

[*]The [md driver seems to have issues]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285156") when replacing a down soldier on RAID10 sets. This is, as mentioned in the launchpad report, a regression. Werkz great on my pre 8.10 setups. (Incidentally, [here]("http://robbat2.livejournal.com/231207.html?view=337959") is what seems to be a workaround.)

[*][Installing the mdadm package buys you]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/280414") a full install of something called citadel! A big-time collaboration tool. Just what I needed.
[/LIST]

This is not, from my perspective, ready for prime-time. And for my needs I do not think the new release buys me anything over the previous rev anyway. YMMV.

---

### Post by jedimasterk on 2008-11-08
Release Notes: "After ejecting a CD tray containing a disc, the tray will be immediately retracted, making it difficult to remove the disc (bug 283316). This can be worked around by pressing the eject button again before the disc is fully mounted, after which it will stay open. We expect to fix this in a post-release update."

I had done a fresh install and this bug was present. I burned an iso with Brasaro went to eject and good thing I have quick hands. Got rid of Ibex due to this bug, as well as Nvidia and Compiz rendering title bar problem as well as resolution setting problems in some games. I also experienced long logon and logoff times. as well as the souds for logon and loggoff being out of sync. Put Hardy back on and all is well. I value my hardware and fingers!.

---

