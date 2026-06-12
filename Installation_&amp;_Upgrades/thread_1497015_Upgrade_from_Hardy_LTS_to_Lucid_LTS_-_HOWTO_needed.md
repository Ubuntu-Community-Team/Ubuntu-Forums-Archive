---
title: "Upgrade from Hardy LTS to Lucid LTS - HOWTO needed"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by pgmer6809 on 2010-05-30
I would like to upgrade from Hardy Heron to Lucid Lynx.
I am not given that option in the Update manager, and anyway the conventional wisdom seems to be that it is unwise to skip so many versions when doing an upgrade.

(When will Canonical allow an Upgrade of one LTS to the next? )

Hence I think my best bet is to do a clean install of Lynx.
Is there an authoritative list of directories/files to be backed up?
/home of course, but what about various files in /etc, /var or /opt?

I have a way of backing up the list of installed packages, but what about the list of installed WINE applications?
I would like to upgrade from Hardy Heron to Lucid Lynx.
I am not given that option in the Update manager, and anyway the conventional wisdom seems to be that it is unwise to skip so many versions when doing an upgrade.

(When will Canonical allow an Upgrade of one LTS to the next? )

Hence I think my best bet is to do a clean install of Lynx.
Is there an authoritative list of directories/files to be backed up?
/home of course, but what about various files in /etc or /opt?

I have a way of backing up the list of installed packages, but what about the list of installed WINE applications?

Further backup is one thing; restoring is something else. There too one needs a bit of a procedure (i.e to use the list of save packages there are certain key steps to take.)

Is there a nice HowTo on this topic?
Furthermore backup is one thing; restoring is something else. There too one needs a bit of a procedure (i.e to use the list of save packages there are certain key steps to take.)

Is there a nice HowTo on this topic?

---

### Post by davidmohammed on 2010-05-30
you probably want to read [this]("https://help.ubuntu.com/community/LucidUpgrades") before you do the upgrade...

---

### Post by seshu6392 on 2010-05-30
Well, it does mention that stuff in /etc get reinstalled but I couldn't find what it does to /usr where, i believe, all the libraries are stored.

I'm running 9.10 and have several libraries such as libserial, urg, avr-gcc, openCV etc. installed and working. So I don't want to do the ./configure; make; sudo make install for all these libraries again if i upgrade.

The link says that "renewing the installation" lets you keep your home directory as opposed to "upgrade" How exactly am I supposed to "renew the installation", given that my libraries don't get erased?

So basically, what do i do to get 10.04 without affecting the libraries and, if possible, various packages that i installed?

---

### Post by davidmohammed on 2010-05-30
... if you've had to make various libraries then you'll have to suck-and-see if the upgrade works.  No guarantees since you didn't install from the ubuntu repository.  I recommend you first backup your computer before moving from 9.04 to 9.10 and finally to 10.04.

---

### Post by seshu6392 on 2010-05-30
well, i have 9.10 and yes, they haven't been installed from the repos...

a trivial question: what all should i backup? i don't have an extnl harddisk. and even if i backup all the /etc files, i don't think things will work out well if i just blindly replace the corresponding folders...

in short, what all should i backup so that my settings and stuff don't get modified greatly.

my idea of backing up is to just copy into another partition of my hard disk...

---

