---
title: "Proposal for Offline Software Installers"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by unmole on 2010-04-10
Hello everyone,
From [Ubuntu OfflineUpdateSpec]("https://wiki.ubuntu.com/OfflineUpdateSpec")
> While it's very easy to install more packages via Synaptic, people who don't have access to Internet find it very difficult to install more packages and updates. Also multiple installations which are not connected to each other have to download and install the same packages multiple times to install them. This not only is sub-optimal, it also wastes a lot of bandwidth.

A simplistic solution to this particular problem would be to create a self-extracting shell script (Perhaps with a Zeinity interface) which extracts all the required dependencies (.debs) to a temporary area and then installs (dpkg -i ./*) all of them. This approach has drawbacks but has pros too. Consider the following cases:

1) I need my WiFi to work to get online. But for my WiFi to work, I would have to use Jockey/Synaptic to install the required drivers for which I need internet in the first place. 

If the driver was bundled as an installer, I could download it from say my friend's computer and get online.

2) I live in a place where internet access is hard to come by but I need ubuntu-restricted-extras to be able to really use my computer. If I could somehow obtain an [installer]("http://hacktolive.org/wiki/Ubuntu-restricted-extras_offline_installer")  for it, not only am I able to use it but I can share it with those around me.


I'm going to try implement a installer for Broadcom STA driver for Lucid. Any ideas or feedback are welcome.

---

### Post by mac9416 on 2010-04-10
Hi, unmole!

Offline installation is made possible by software such as Keryx which acts as a portable package manager. This works fine for one person with experience with a package manage, but what if you want to share the applications you download with friends? Or make it easy enough for Grandma to install software? 

To deal with this, people have attempted to create one-file installers similar to Windows installers. They look much like the one you have described, but usually more complex.

Here are several such attempts. Hopefully you can find some useful information in them.
 [http://code.google.com/p/superdeb/](http://code.google.com/p/superdeb/)
 [http://hacktolive.org/wiki/SuperDeb](http://hacktolive.org/wiki/SuperDeb)
 [http://sayanriju.co.cc/debshare.html](http://sayanriju.co.cc/debshare.html)

Keep us updated on progress and any difficulties you run into. Good luck!
-mac

---

### Post by unmole on 2010-04-17
@mac9416
Thanks for the reply. Keryx is great for what it does, create a portable repository that can can be updated from anywhere. SuperDebs need the runz framework to run and creating them is a bit risky as it tends to move core files around. I already had tried the two. But Sayan's DebShare was a revelation. It is exactly what I had in mind but only better! Thanks a lot for pointing it out. Now I don't have to reinvent the wheel. :D

---

### Post by mac9416 on 2010-04-17
I'm glad Debshare helped you, unmole. I agree, it looks overall like a good idea. But I do see some weaknesses:

1) Debshare uses a list of "do not include" packages that come with Ubuntu. The problem is, that list changes from release to release and from *buntu flavor to *buntu flavor. A better way to handle this would be to read installed packages from one or more /var/lib/dpkg/status files. The user could input a status file from each distro he wants the debshare to work on.
2) It uses 'dpkg --install --force-depends' to install packages, which could break dependencies. A better method would be to use dpkg-scanpackages to create a simple repository, add it to an /etc/apt/sources.list.d/debshare.list, and call APT to handle the installation.

I have thought about working on a Debshare-like project, but my development time has been spent on Keryx. If I find some free time, I may make some improvements on Debshare. If you decide to work on it, keep me posted on your progress and give me a holler if you need any help.  :)

---

