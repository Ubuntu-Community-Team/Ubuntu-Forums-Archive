---
title: "Could anyone walk me through an instalation?"
date: 2018-06-01
forum: Installation &amp; Upgrades
---

### Post by priest84 on 2018-06-01
Hi! 

I am obviously new to Ubuntu (Linux as a whole), and I cannot figure out how to install Itch.io. The Itch.io site has instructions, but I don't even know how to follow them. I'm on the latest version of Ubuntu 18.04? I could really use some one more knowledgable to walk me through this, please.

---

### Post by TheFu on 2018-06-01
[https://itch.io/docs/itch/installing/linux/](https://itch.io/docs/itch/installing/linux/) provides packages.  These may or may not be compatible with the 18.04 system.   
> Various Linux distributions have varying opinions on how software should be distributed &#8212; this makes Linux a particularly hard platform to target, given the sheer number of different format to support.
is true, but both flatpak and "snaps" address this issue.   Perhaps sending them some feedback about those options would help everyone.

To install a .deb package file on Ubuntu, [https://askubuntu.com/questions/40779/how-do-i-install-a-deb-file-via-the-command-line](https://askubuntu.com/questions/40779/how-do-i-install-a-deb-file-via-the-command-line) explains.  Installing packages from untrusted sources is a danger to your system.  Be careful, ensure the source is  reputable, and it is usually best to avoid .deb file installations, since the dependencies have to be met manually, by you and maintained manually, by you.  In short, installing a .deb file usually leads to a system in "apt hell" in 3-6 months, which cannot be patched.   

Reputable packages will have the installation of the .deb file enable a PPA and they will maintain the packages in a way to keep them current, patched, as part of your normal, weekly, update/upgrade patching process.

---

