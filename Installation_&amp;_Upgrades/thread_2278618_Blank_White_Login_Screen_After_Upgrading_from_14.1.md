---
title: "Blank White Login Screen After Upgrading from 14.10 to 15.04"
date: 2015-05-18
forum: Installation &amp; Upgrades
---

### Post by chiques on 2015-05-18
I made the mistake by saying "yes" to upgrade my ubuntu version now I've screwed up 2 of my machines. They have the same problem, after upgrading and rebooting there is a bright white screen where my login screen would normally be. 

I can Atl+F6 and log in through there. From the command prompt I can run ```
startx
``` but it loads something called "Lightweight X11 Desktop Environment" which is not what I normally run.

Does anyone have any advise on what the problem could be?

---

### Post by Vladlenin5000 on 2015-05-18
It might be related to graphics drivers. Did you have the proprietary drivers installed? If so, install again.

PS - It started with LXDE because you either have Lubuntu or at some point you installed LXDE or lubuntu-desktop to a different Ubuntu flavor. It certainly wasn't the upgrade that installed it.

---

### Post by Vladlenin5000 on 2015-05-18
However, [here]("http://ubuntuforums.org/showthread.php?t=2276622") you posted a quite different comment... Different machines? :p

---

### Post by chiques on 2015-05-18
> **Vladlenin5000 said:**
> However, [here]("http://ubuntuforums.org/showthread.php?t=2276622") you posted a quite different comment... Different machines? :p

Yeah, but that's just a band aide fix which I thought was isolated to a single machine. This seems to be related to the actual upgrade which is why I posted it again. 

I went ahead and performed the same fix:
[http://askubuntu.com/questions/613626/black-login-screen-ubuntu-15-04](http://askubuntu.com/questions/613626/black-login-screen-ubuntu-15-04)

I'll try reinstalling the hardware drivers as well.

---

### Post by chiques on 2015-05-18
This did not work: [http://askubuntu.com/questions/613626/black-login-screen-ubuntu-15-04](http://askubuntu.com/questions/613626/black-login-screen-ubuntu-15-04)

---

### Post by Vladlenin5000 on 2015-05-18
If course it didn't. It's a NO solution and let me add, it's dumb in itself.

Now, again, DID you have proprietary drivers - nvidia or AMD/ATI - installed? You did, didn't you? ;)

That is often not a problem if the drivers were installed from the official repositories. Installing from binaries from either nvidia or AMD requires the same procedure whenever the kernel is upgraded. PPAs also are disabled with a release upgrade and if you had a PPA as the repository for the graphics driver in 14.10 then the same issue should be expected.

---

### Post by chiques on 2015-05-18
> **Vladlenin5000 said:**
> 

Now, again, DID you have proprietary drivers - nvidia or AMD/ATI - installed? You did, didn't you? ;)

That is often not a problem if the drivers were installed from the official repositories. Installing from binaries from either nvidia or AMD requires the same procedure whenever the kernel is upgraded. PPAs also are disabled with a release upgrade and if you had a PPA as the repository for the graphics driver in 14.10 then the same issue should be expected.

I have an ATI Radeon 9600. I have never selected to install any proprietary drivers.

---

### Post by chiques on 2015-05-24
I looks like something changed in from 14.10 to 15.04.

I booted the live cd for 15.04 and it immediately goes into a Kernel Panic lockup.

[ATTACH=CONFIG]262190[/ATTACH]


I just went ahead and reformatted and reverted to 14.10. Everything works fine now.

---

### Post by chiques on 2015-11-27
Had the same problem on another machine (15.04). I did this and it fixed the white blank screen in the greeter.

sudo apt-get purge lightdm-gtk-greeter

---

