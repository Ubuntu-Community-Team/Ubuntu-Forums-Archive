---
title: "Missing packages from upgrading online to hoary"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by Jet2k5 on 2005-04-10
Hey guys,

I wasn't able to get my hands on a cd-r to burn the hoary cd, so I tried the online upgrade.  Everything seemed to fly by smooth until I did ' uname -r'.  I'm running 'cat /etc/issue' and it reports back that I'm running Hoary, but then I asked around in the channels and they said that hoary has 2.6.10?  I'm I wrong? Because I have 2.6.8.  So if it missed to install the kernel, there has to be some probability that there are more packages missing.  What I'm planning on is downloading and burning the .iso, and then upgrading it from some of the links that I see posted.

But just a few other questions how come the upgrade webt bad?  And how come a lot of my progs where erased?  Like limewire, gtkpod, etc .... sucks, because I have to re-install everything, so I might as well just re-install everything.  But I would expect the ubuntu upgrade to go by smooth, not have these issues.

-Luis

---

### Post by jdong on 2005-04-10
Did you use "apt-get dist-upgrade", as opposed to "apt-get upgrade" ?

---

### Post by Jet2k5 on 2005-04-11
Yes I did " apt-get dist-upgrade".  Is there a file that holds back the kernel from being updated maybe?

I'm going to get some cd-rs later tonight, and burn the ISO on ( if my cd-rw works in Ubuntu now ) and upgrade from that.  I'm just going to pop the cd in, reboot and go from there if possible.  If not then I'll have to follow the wiki again, which for some reason I don't trust it will work, since it didn't work the first time.

 :|

---

### Post by jdong on 2005-04-11
Nothing holds back the kernel, unless you removed the "linux-386, linux-686" metapackage.


Can you post your sources.list for us to double-check?

---

