---
title: "How to update from one version to another"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by scheidecker on 2005-12-05
Hello all,

I am yet to adopt Ubuntu as my "official" desktop Linux. I have to give support to one of my remote locations that is outside the USA. Right now we are using Fedora. So if I want to go from Fedora 3 to Fedora 4 I can ssh those machines, use YUM to update the whole thing, then remove the old kernel, reboot the machine and let it boot with the new version. All very easy. Well, I would like to know how to accomplish that with Ubuntu. If I can do that, then I will have everybody's machine switched over to Ubuntu. Another question I have is: how is the Ubuntu wireless support? I am using Linux for 10 years but when you get to administer a lot of machines you get to a point where you want everything extremmely easy and handy.

Another question: **What a cool editor this one is!** It can even do PHP! I was using HTMLArea 3.0 in my projects. What is this editor? Can I use it freely as well! Cool! Please advice.

Thanks,
Scheidecker

---

### Post by Qrk on 2005-12-05
Upgrading Ubuntu is as easy as pasting a new source list into /etc/apt/sources.list, then typing sudo apt-get update, sudo apt-get dist-upgrade, and rebooting.

Breezy's wireless support is really good. (Hoary's and Warty's don't really come close) It was a major focus point of the release. I haven't used Fedora since, II, so I'm not sure how they compare.

---

### Post by az on 2005-12-05
[QUOTE=scheidecker]Hello all,

I am yet to adopt Ubuntu as my "official" desktop Linux. I have to give support to one of my remote locations that is outside the USA. Right now we are using Fedora. So if I want to go from Fedora 3 to Fedora 4 I can ssh those machines, use YUM to update the whole thing, then remove the old kernel, reboot the machine and let it boot with the new version. All very easy. Well, I would like to know how to accomplish that with Ubuntu. If I can do that, then I will have everybody's machine switched over to Ubuntu. Another question I have is: how is the Ubuntu wireless support? I am using Linux for 10 years but when you get to administer a lot of machines you get to a point where you want everything extremmely easy and handy.

Another question: **What a cool editor this one is!** It can even do PHP! I was using HTMLArea 3.0 in my projects. What is this editor? Can I use it freely as well! Cool! Please advice.

Thanks,
Scheidecker[/QUOTE]

With apt, you can change your sources.list to point to the new repositories (example, change breezy to dapper in four months when it is release) do
sudo apt-get update
sudo apt-get dist-upgrade.

If you have the ubuntu-desktop package installed, it will bring in the new kernel, too, so you do not have to do that step.

As for wireless, if there are linux drivers available at the time of release, they are part of the stock kernel, either as a module in the kernel-image package, or a module in the linux-restricted-modules package which matches your kernel version.  Some drivers require ancillary packages, like linux-wlan-ng or ndiswrapper-utils.  Usualy, the packages are included on the install cd for convenience.

As for the html editor, will the board runs vBuletin.  You can check on their site.  It is proprietary.

---

