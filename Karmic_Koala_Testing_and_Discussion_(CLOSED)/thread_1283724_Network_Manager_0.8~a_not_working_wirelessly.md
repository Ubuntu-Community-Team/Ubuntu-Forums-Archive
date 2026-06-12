---
title: "Network Manager 0.8~a not working wirelessly"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by linux6994 on 2009-10-05
This evenings update to Network Manager 0.8~a~git.2009083t2204 did not correct the recent Network-Manager problem of saving setting and works worse that the 0.7 package. It did not connect to wireless at all. Luckily I have the WICD package locally in cache. I am using WICD to connect.

---

### Post by novafluxx on 2009-10-05
I just did updates as well, and now I can't connect either, network manager starts up, but doesn't automatically connect, then when I click it to select my network, it appears to freeze there, and if I log out then back in, its no longer appearing in the panel.

I'm sure it'll be fixed soon...heh

---

### Post by milliman on 2009-10-05
Noticed the same here too.  I'm only updating this one machine for now until it is fixed.  Hopefully by the morning.

---

### Post by crjackson on 2009-10-05
> **novafluxx said:**
> I just did updates as well, and now I can't connect either, network manager starts up, but doesn't automatically connect, then when I click it to select my network, it appears to freeze there, and if I log out then back in, its no longer appearing in the panel.

I'm sure it'll be fixed soon...heh

I"m have the same issue.  After reboot it does show back up, and the radio is detecting active wireless in the area, but if I try to connect it freezes up again.

What a bummer...  I hope it gets fixed tonight or tomorrow.  I was just about to crown this beta good enough for my main laptop.  Glad I didn't.  Still running hardy on that one.

---

### Post by 16sinker on 2009-10-05
I also am having this problem. It's the first glitch I've had since upgrading from Jaunty to Karmic beta, so I'll be watching this thread closely and hope for a fix soon.

---

### Post by linux6994 on 2009-10-05
Everyone needs to install WICD first so you can use it as a second alternative!

---

### Post by dalonso on 2009-10-05
> **linux6994 said:**
> This evenings update to Network Manager 0.8~a~git.2009083t2204 did not correct the recent Network-Manager problem of saving setting and works worse that the 0.7 package. It did not connect to wireless at all. Luckily I have the WICD package locally in cache. I am using WICD to connect.

Temporary fix until network-manager is updated again, and if you have a bit of luck and your apt cache is still holding the previous libnm and network-manager debs.

[INDENT]1) sudo dpkg -i /var/cache/apt/archives/libnm-util1_0.8~a~git.20090923t064445.b20cef2-0ubuntu2_i386.deb
2) sudo dpkg -i /var/cache/apt/archives/libnm-glib2_0.8~a~git.20090923t064445.b20cef2-0ubuntu2_i386.deb
3) sudo dpkg -i /var/cache/apt/archives/network-manager-gnome_0.8~a~git.20090923t220421.1ac8ffd-0ubuntu4_i386.deb
4) reboot [/INDENT]

---

### Post by tlois on 2009-10-05
Ditto here.  A pain, because one computer is a desktop with wireless, so can't just plug in ethernet as with my laptops.  Will try the above in the morning- too tired to deal with it now.

---

### Post by travishume on 2009-10-05
Seems to be fixed now.  Time to update.

---

### Post by novafluxx on 2009-10-06
Its been fixed already?

---

### Post by travishume on 2009-10-06
Yep.  Using it now.
network-manager-gnome 0.8~a~git.20091002t194214.8515a07-0ubuntu1
network-manager-vpnc 0.8~a~git.20090928t155845.44e0005-0ubuntu1

---

### Post by slakkie on 2009-10-06
There is a new release coming of NetworkManager. Yesterday they fixed some bugs: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/413622/comments/12](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/413622/comments/12)

---

### Post by Grimhound on 2009-10-06
Just updated. Wireless completely broken for me. Feeling aggravated.

---

### Post by Hated On Mostly on 2009-10-06
You guys should try the version in the repository that was posted in this thread:

[http://ubuntuforums.org/showthread.php?t=1278133&page=2](http://ubuntuforums.org/showthread.php?t=1278133&page=2)

[https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)

I am using version 0.8~a~git.20090930t162132.866d48b-0ubuntu1~nmt1 which was up there earlier and it works perfectly. After you get a stable system, don't update anymore.

---

### Post by cariboo on 2009-10-06
> **Hated On Mostly said:**
> You guys should try the version in the repository that was posted in this thread:

[http://ubuntuforums.org/showthread.php?t=1278133&page=2](http://ubuntuforums.org/showthread.php?t=1278133&page=2)

[https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)

I am using version 0.8~a~git.20090930t162132.866d48b-0ubuntu1~nmt1 which was up there earlier and it works perfectly. After you get a stable system, don't update anymore.

Breaking things is what the beta is all about, if you want stable, you should have stayed with Jaunty, or waited till karmic is released.

---

### Post by canabal on 2009-10-06
Hey guys, I also lost connection, although it is wired, not wireless (desktop so no wireless)

Is there a way of reverting back to the old package or downloading the new package and installing it once it is fixed?  Where can I find it?

Thanks in advance.

---

### Post by slakkie on 2009-10-06
Guys, if you want to see if the issue is fixed, please try out the PPA of network-manager:

[https://launchpad.net/~network-manager/+archive/trunk/](https://launchpad.net/~network-manager/+archive/trunk/)

If you install network-manager from that PPA you will have the latest and greatest nm package and you can provide feedback to devs before it hits the official repo's of Karmic.

---

### Post by canabal on 2009-10-06
> **slakkie said:**
> Guys, if you want to see if the issue is fixed, please try out the PPA of network-manager:

[https://launchpad.net/~network-manager/+archive/trunk/](https://launchpad.net/~network-manager/+archive/trunk/)

If you install network-manager from that PPA you will have the latest and greatest nm package and you can provide feedback to devs before it hits the official repo's of Karmic.
Is there a way to download those files directly and then install them?  because my karmic no longer has any internet access.

---

### Post by slakkie on 2009-10-06
> **canabal said:**
> Is there a way to download those files directly and then install them?  because my karmic no longer has any internet access.

[https://launchpad.net/~network-manager/+archive/trunk/+packages/](https://launchpad.net/~network-manager/+archive/trunk/+packages/)

But atm there is a new version waiting to be build, so you need to be patient, but you should be able to download the packages once they are build.

---

### Post by canabal on 2009-10-06
great thanks.  I just decided to configure by command line.  I didnt know how before but I am glad I just did it so I will know what to do in the future if something similar arises and I do no have 2 computers.

---

### Post by Hated On Mostly on 2009-10-06
> **cariboo907 said:**
> Breaking things is what the beta is all about, if you want stable, you should have stayed with Jaunty, or waited till karmic is released.

Jaunty wasn't stable for me at all. This beta daily build that I am using is running perfect and is the only version of Karmic I have tried. I never touch an alpha version and only use a beta when the stable doesn't work. Jaunty was completely unusable for me and a lot of others.

[http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)

Besides, alphas are about breaking things. Betas are about fixing them. Constant introduction of regressions should not occur in a proper beta test. Ubuntu's revision control needs a lot of work. These aren't minor, slightly annoying regressions and bugs that people are seeing in daily updates. Some of these are pretty serious.

---

### Post by soro2005 on 2009-10-06
> **Hated On Mostly said:**
> Besides, alphas are about breaking things. Betas are about fixing them. Constant introduction of regressions should not occur in a proper beta test. Ubuntu's revision control needs a lot of work. These aren't minor, slightly annoying regressions and bugs that people are seeing in daily updates. Some of these are pretty serious.

Whatever *should* be doesn't matter a whole lot. The fact is that these betas have some massive breakage. They always had, and they probably will have in the future, partially due to the fact that people with more diverse setups and knowledge levels are using them, as opposed to the somewhat more geeky population of alpha testers. It is very commendable that you offer your computer for testing. But if you need it to be stable, you have two options: You install a beta which works, and then never change or upgrade anything until some time after the final release, or you use a different distro which is released and stable. Trust me, this here is peanuts compared to what we have had before.

---

