---
title: "Ubuntu, Kubuntu, Xubuntu on same computer"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by jwk on 2006-06-09
I wont to try Gnome, KDE and Xfce (never used any, so want to try them all). I  have dial-up, and only have access to DSL on Sunday. I ordered Ubuntu, and downloaded the Desktop cd's of Kubuntu and Xubuntu, and going to burn the cd's this weekend. I wont to have all 3 to swich between. I have read that you need the alternative install disks in order to install one OS, then install another Desktop enviroment off a cd. I really don't feel like waiting 2 weeks to get the right cds, so does anybody know how to install them off of the desktop cds? I have played with .deb files before (trying to get the net install of debian working), and have lots of experence using a CLI (I currantly run Mac OS X) but this will be my first real Linux experence. Thanks in advance.

---

### Post by matt_man22 on 2006-06-10
First install whichever CD you currently have, whether it be a live or alternate CD.  Then run the following commands, but disregard whichever one you already installed:
```

sudo apt-get ubuntu-desktop
sudo apt-get kubuntu-desktop
sudo apt-get xubuntu-desktop
```

Now you have all three desktops.

---

### Post by aysiu on 2006-06-10
You cannot install the other desktop environments off the Desktop CDs.

You can install them from the online repositories, but since you're on dial-up, I'd recommend using the Alternate Installer CDs instead.

Though, you could also use DSL on Sunday to install the other desktops. Use *aptitude* instead of *apt-get*, though: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop 
sudo aptitude install xubuntu-desktop
``` If you install them with *apt-get* or Synaptic, they won't be so easy to remove later.

---

### Post by jwk on 2006-06-10
[QUOTE=aysiu]Though, you could also use DSL on Sunday to install the other desktops.[/QUOTE]

I would, but I think packing my desktop around would be a little hard. :D I think I figured out why I can't install it from the desktop cd, so if I am right, I don't fell like it doing it from them.;)  I'll just download the the alternative install disks. Thanks for the help :-|

---

### Post by melenor on 2008-05-21
> **aysiu said:**
> You cannot install the other desktop environments off the Desktop CDs.

You can install them from the online repositories, but since you're on dial-up, I'd recommend using the Alternate Installer CDs instead.

Though, you could also use DSL on Sunday to install the other desktops. Use *aptitude* instead of *apt-get*, though: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop 
sudo aptitude install xubuntu-desktop
``` If you install them with *apt-get* or Synaptic, they won't be so easy to remove later.

why would aptitude work better then Synaptic or apt-get? I thought that apt-get, aptitude and Synaptic were all the same thing.

---

### Post by aysiu on 2008-05-21
> **melenor said:**
> why would aptitude work better then Synaptic or apt-get? I thought that apt-get, aptitude and Synaptic were all the same thing.
Two years ago, when I made that post you quoted, *apt-get* had no mechanism for removing unwanted dependencies. Even now, I don't know if *apt-get autoremove* will remove an entire desktop environment.

---

### Post by A$h X on 2008-05-22
I don't think it does, as i found to my cost when I tried xubuntu desktop on my existing ubuntu install. I had a fun time going through my logs to manually remove programs that came with xubuntu. There were a few commands which took out the majority of apps, but to completely scrub xubuntu from my system I followed the "pure gnome" desktop guide from psychocats.

---

### Post by melenor on 2008-05-22
can i get the link to the guide? because i decided that i don't really like the other ones. Thanks.

---

### Post by aysiu on 2008-05-22
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by fickenbaisage on 2008-05-23
> **aysiu said:**
> Two years ago, when I made that post you quoted, *apt-get* had no mechanism for removing unwanted dependencies. Even now, I don't know if *apt-get autoremove* will move an entire desktop environment.

So you're saying it's not safe to run apt-get autoremove? I'm concerned cause I run it regularly along with aptitude autoclean.

---

### Post by aysiu on 2008-05-23
> **fickenbaisage said:**
> So you're saying it's not safe to run apt-get autoremove? I'm concerned cause I run it regularly along with aptitude autoclean.
When did I say it wasn't safe?

I said I don't know that *apt-get autoremove* will [re]move an entire desktop environment. I still don't.

A metapackage is an empty package that's basically just a pointer to other packages. That's what *xubuntu-desktop* is. If you remove *xubuntu-desktop* with *apt-get* or Synaptic, all you'll do is remove the pointer, not the packages it points to.

If you installed *xubuntu-desktop* with *aptitude*, removing it also with *aptitude* will remove the packages it points to as well.

I don't know if this is true for *apt-get autoremove* in the case of *xubuntu-desktop*, *ubuntu-desktop*, and *kubuntu-desktop*. In many cases, *autoremove* will remove unwanted dependencies, but those are usually dependencies for real packages, not empty metapackages.

If you're mainly concerned about safety, it's quite the other way around, actually. Sometimes *aptitude* gets overzealous and wants to remove more than you want removed. If you simply use *apt-get*, I doubt anything will be removed that you don't want removed... in fact, nothing may be removed at all (which was my original point).

---

### Post by fickenbaisage on 2008-05-23
> **aysiu said:**
> When did I say it wasn't safe?

I said I don't know that *apt-get autoremove* will [re]move an entire desktop environment. I still don't.

A metapackage is an empty package that's basically just a pointer to other packages. That's what *xubuntu-desktop* is. If you remove *xubuntu-desktop* with *apt-get* or Synaptic, all you'll do is remove the pointer, not the packages it points to.

If you installed *xubuntu-desktop* with *aptitude*, removing it also with *aptitude* will remove the packages it points to as well.

I don't know if this is true for *apt-get autoremove* in the case of *xubuntu-desktop*, *ubuntu-desktop*, and *kubuntu-desktop*. In many cases, *autoremove* will remove unwanted dependencies, but those are usually dependencies for real packages, not empty metapackages.

If you're mainly concerned about safety, it's quite the other way around, actually. Sometimes *aptitude* gets overzealous and wants to remove more than you want removed. If you simply use *apt-get*, I doubt anything will be removed that you don't want removed... in fact, nothing may be removed at all (which was my original point).

I just want to make sure I don't do anything stupid to my filesystem while at the same time keeping my hard disk usage minimal by removing useless dependencies. I think I'll avoid using apt-get autoremove for the time being.

---

### Post by aysiu on 2008-05-23
> **fickenbaisage said:**
> I just want to make sure I don't do anything stupid to my filesystem while at the same time keeping my hard disk usage minimal by removing useless dependencies. I think I'll avoid using apt-get autoremove for the time being.
Regardless of what method you use, you will always be warned as to what's being removed, and you can then cancel the operation before "damage" is done.

Frankly, even if packages are removed, they can be easily reinstalled with no harm done to your system.

---

### Post by melenor on 2008-05-29
Yah i am having a problem i tried out KDE didn't like it, so i went 
sudo aptitude remove kubuntu-desktop
and it had an error with kio-umountwrapper this is the error
E: kio-umountwrapper: subprocess post-removal script returned error exit status 2
i would really like to get back to pure gnome. Thanks.

---

