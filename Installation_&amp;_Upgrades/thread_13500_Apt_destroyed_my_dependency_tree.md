---
title: "Apt destroyed my dependency tree"
date: 2005-01-31
forum: Installation &amp; Upgrades
---

### Post by MrPsycho on 2005-01-31
Hello

I am fairly new to linux, so please bear with me.  I recently noticed that I had about 125 packages on my upgrade list which were marked as available to upgrade.  I figured this was a sizeable amount so I would go ahead and add them.

When I made this upgrade it asked me if I wanted to go with default method or "smart".  I kept reading that and I knew I should have gone with default, but some little voice told me to make a go for smart.  Lo and behold, the smart system in synaptic selectively removed a lot of things which one might think are useful.. GDM for instance.  Now theres a whole tree of things I can't install to get back to where I was.
ALSA drivers, half of the gnome utilities, gtk, etc.  I hope it didn't mess with my kernel.  ](*,) 

Is there some way to revert to my previous packages without trying to find which of the 100 or so I need to switch?  If not, what would you recommend.  I'm open to suggestions.  Right now I've manually started X and I can only run it as root.

Thanks in advance.

---

### Post by az on 2005-02-01
You added a some entries into your sources.list, didn't you?

No.  There is no way to revert.

You may clean up your apt sources.list and keep only Ubuntu repositories and try to reinstall ubuntu-desktop.  Usually, a smart upgrade is the way to go.  The trick is to not trust any non-official repositories.

---

### Post by MrPsycho on 2005-02-01
Yes..it may be be possible that I added some unofficial repositories.    :cry:  

My problem is I already had to make special package installs of gtk to get my xfce desktop working (it required a version which wasnt available on ubuntu servers).

I've cleaned out my sources.list but I still cant install.  I get these problems:

>  Depends: libopenh323-1.13.2 but it is not going to be installed
 Depends: libpt-1.6.3 but it is not going to be installed
 Depends: libpt-plugins-alsa but it is not going to be installed or
 	libpt-plugins-oss but it is not going to be installed
 Depends: libpt-plugins-v4l but it is not going to be installed or
 	libpt-plugins-avc but it is not going to be installed or
 	libpt-plugins-dc but it is not going to be installed


Update: I believe I have narrowed down the problem to a backport of pciutils which was installed.  The version is 1:2.1.11-14backports.org , I'm going to attemp forcing the version back to warty.  If I do enough of these version rollbacks is it possible I can get it to work again?

---

### Post by BlackFenix on 2005-02-04
try run a apt-get -f install

---

