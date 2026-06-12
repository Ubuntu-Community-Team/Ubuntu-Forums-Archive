---
title: "Secure remote network installation (minimal tools)"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by DA_uf on 2007-09-21
How can I perform a "Secure remote network installation" as mentioned here [http://www.ubuntu.com/news/ubuntuserver704](http://www.ubuntu.com/news/ubuntuserver704) ?

I found this [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot) BUT I ALSO WILL NOT BE USING A UBUNTU CD, AND I DON'T HAVE apt-get.

Basically, I can ssh into my remote dedicated server which is booted with a Gentoo Minimal LiveCD.  I can ask the remote tech to reboot to the Hard Drive or to the LiveCD.  I don't think I can start with a Ubuntu CD.

The environment offers wget and tar.  It did not come with a package manager like synaptic, apt-get or even the Gentoo flavor "emerge".  But after a wget, (actually it used links, but I used wget on other downloads) it had "emerge".  Ubuntu should have apt-get at that point.

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/) expects you to have binutils already and cc and/or gcc to build what you download.  I was unable to find gnu binaries.

Following the Gentoo Minimal LiveCD instructions at [http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml](http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml) , I AM CONVINCED THAT UBUNTU (or any Linux) can do a remote network install with just ssh, wget and tar.  (Maybe beginning at chapter 3 or 4).  But maybe I am wrong here and must have a Ubuntu CD?

A way to confirm that sshd and networking will be available BEFORE requesting the tech to perform a reboot would be great.

Please advise.

---

### Post by calvinkim on 2008-03-11
I'm not sure if following links would be helpful, but try them out.
They are Ubuntu and Debian specific.

[https://help.ubuntu.com/community/Installation/OverSSH](https://help.ubuntu.com/community/Installation/OverSSH)
[http://www.underhanded.org/papers/debian-conversion/remotedeb.html](http://www.underhanded.org/papers/debian-conversion/remotedeb.html)

---

