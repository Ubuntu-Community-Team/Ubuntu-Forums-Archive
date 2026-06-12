---
title: "Remove Plymouth"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dacoolio on 2010-04-10
Looking through bootchart, Plymouth is taking quite a long time. I prefer a speedy boot over a pretty splash screen, so I want it gone. I tried uninstalling it, but Synaptic tries to uninstall pretty much all of ubuntu with it. Has anyone come up with a way to remove Plymouth? Thanks

---

### Post by NCLI on 2010-04-10
You're using the development version of Ubuntu, Lucid Lynx. Until it is released, all discussion of it should take place in [the Lucid Lynx forum]("http://ubuntuforums.org/forumdisplay.php?f=377"). I've asked a mod to move it for you. 

Generally, if you're having problems with something in an unstable beta or alpha release of Ubuntu, you should not try to work around it, but report a bug instead to make the developers aware of the problem. In this case, you should run the command "ubuntu-bug plymouth" from the alt+F2 dialog, or from a terminal, then report a bug. Plymouth shouldn't slow down your boot. In fact, it should speed it up.

---

### Post by lisati on 2010-04-10
> **NCLI said:**
> You're using the development version of Ubuntu, Lucid Lynx. Until it is released, all discussion of it should take place in [the Lucid Lynx forum]("http://ubuntuforums.org/forumdisplay.php?f=377"). I've asked a mod to move it for you. 


Thread moved

---

### Post by dacoolio on 2010-04-10
I checked launchpad for ubuntu bugs and found someone who has submitted a bug report for this already. However, it's been marked invalid because "Obviously when you remove core packages that other important packages depend on, it makes a mess of the system."

[https://bugs.launchpad.net/bugs/531331](https://bugs.launchpad.net/bugs/531331)

Any suggestions?

---

### Post by vininim on 2010-04-10
Different things I would say. There is the "plymouth is slow" issue, and the "plymouth should be optional" one. The first requires diagnosing while the latter is a distro choice that I can't see changing. You can turn off the graphical part of plymouth by disabling kernel-mode setting in the boot options, IIRC.

---

### Post by Didius Falco on 2010-04-10
From /usr/share/doc/plymouth/README.Debian:

> Disabling the splash screen
---------------------------

There are two methods to disable the splash screen.  Both have the
same effect.  Your boot will show such messages as are emitted by
the starting services, and will still be able to prompt if needs be.

 1) Remove all of the plymouth-theme-* packages from your system,
    including the text ones.  Plymouth will remain installed to
    permit boot-time prompts.

 2) Remove "splash" from the kernel command-line.  You can do this
    per-boot, or make it permanent by changing the
    GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub

---

### Post by dacoolio on 2010-04-10
Alright I guess since I already removed "splash" from the grub entry I'll just leave it the way it is. Thanks for the suggestions

---

### Post by RTrev on 2010-04-10
The funny thing is, Lucid boots so fast that I've yet to really understand why they've put so much emphasis on making it pretty.

The best boot process I've seen was when I tried PCLOS a few years ago.  They threw up a transparent image of some kind, a nice light blue with their logo, and behind this one could either watch some simple graphics or hit the Esc key and see the actual boot text.  Best of all worlds.  I keep hoping for something as tasteful and useful for Ubuntu.

I still maintain that there should be a video available showing what the developers say the Plymouth boot process *should* look like.  At least then we have some idea of whether it's working as intended.  All I see is the word "Ubuntu" with what looks like cobwebs all over it (seriously) and some 1980s-looking dots underneath it.  A simple "Please wait..." would be aesthetically more pleasing. <g>

---

### Post by proxess on 2010-04-20
No one wants a "Please Wait..." because no one likes to wait. Even a "Loading..." is better than "Please Wait...".

---

### Post by RTrev on 2010-04-20
Fine, then have it say Loading...

It really doesn't need anything more IMHO.  Watching it now, with screen mode changes, it's just a complete mess and give the impression that something is badly broken (which apparently it is.)

---

### Post by Funnnny on 2010-04-20
I see the plymouth for...like 2 seconds at boot time, it's not really make sense now

---

### Post by wkulecz on 2010-04-20
grub2, plymouth ....

Earth to developers -- Nobody really cares about the boot up unless it don't work!  More speed is better, but any other changes that don't enhance reliability are counterproductive.

---

### Post by RTrev on 2010-04-20
> **wkulecz said:**
> grub2, plymouth ....

Earth to developers -- Nobody really cares about the boot up unless it don't work!  More speed is better, but any other changes that don't enhance reliability are counterproductive.

+1

Exactly!

And to make things worse, whenever a disk needs checking during bootup, the message doesn't help us any.  "Disk 1 of 1" and then a percentage, which never reaches 100% but instead the whole thing disappears at varying percentages -- which leaves the user wondering "Did it finish?  Did it hit an error?  What just happened?"

What's even worse, removing spash doesn't work the way it used to.  I used to get some informative text scrolling by during the boot, but with Lucid I get a blank screen.

---

### Post by emarkay on 2010-04-20
Check the other threads on this - Plymouth is too integral now to be removed - but there will be a way - Linux*** is ***open source, remember!

---

### Post by dino99 on 2010-04-20
> **Funnnny said:**
> I see the plymouth for...like 2 seconds at boot time, it's not really make sense now

maybe you have not seen Joao Pinto post on Planet  :(

---

