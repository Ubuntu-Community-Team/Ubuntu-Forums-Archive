---
title: "Install on Sun M40 workstation"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by unkilbeeg on 2010-08-04
A few years back, Ubuntu announced a "[partnership]("http://www.ubuntu.com/partners/sun")" with Sun Microsystems, and explicitly listed the Ultra 40 Workstation is compatible with the then current version of Ubuntu.  I installed that version (8.04) on my Ultra 40 M2 workstations, and everything worked very well.  I later upgraded them to 8.10 and then 9.04, with good results.

Well, now I'm trying to jump to 10.04, and I'm having no luck.

A fresh install seems to hang at GRUB (as near as I can tell.)  I get a quarter screen of magenta (the top 1/4 of the screen turns magenta) and then ...  nothing.  Hang.  I've tried re-installing with the full graphical install, and got this hang from the Live CD.  Using the "alternate install" CD in text mode, everything seemed to install fine, but the first reboot hangs immediately.

Suspecting GRUB 2, I moved to another machine and decided to try an in place upgrade rather than a fresh install.  I figured that the upgrade would retain Grub 1, and I'd have a better chance.  

So far, "better" is a good word.  Only a little better, though, unfortunately.  The upgrade from 9.04 to 9.10 seemed to work OK, but upon reboot, I got a message telling me that it was waiting for the partitions to mount.  <ESC> gets you to a recovery console, which is great.  I can mount all the partitions by hand, and they seem to mount, sort of.  "df" doesn't see them, but you can access all files on all partitions, so they really are mounted.  When you exit the recovery console, however, you go back to waiting for them to mount.

Have the changes to Ubuntu left the Sun Workstations behind?  Do I need to switch to another distro, or put Solaris 10 back on these things?  Or are we going to be stuck on Ubuntu 9.04 in our "Advanced Unix Lab?"

---

### Post by unkilbeeg on 2010-08-05
Well, for what it's worth, Fedora 13 does exactly the same thing.  

Sidux, however does not, despite using the technology I thought was the prime suspect.  It does appear to use GRUB 2, yet it boots with no problems.

<shrug>  I've set my customizations up for Ubuntu, and it would be simpler for me if I could get Ubuntu to work.  However, sidux is at least Debian based, so it'll be a lot easier to shift over to than Fedora would have been.

A distro without a "rolling release" would be better for my purposes.  I run Gentoo on my own machines, so I know the advantages (and *disadvantages*) of that method.  Great for an individual, much less fun if you have a bunch of them to support.

---

