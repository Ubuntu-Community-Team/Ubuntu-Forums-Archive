---
title: "RAM requirements for older releases?"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by chellrose on 2011-05-20
I'm planning to install an old release of Kubuntu on my brother's ancient desktop, which has 256MB of RAM.  I'm thinking of either 5.10 Breezy, 6.06 Dapper, or 6.10 Edgy.  Will any of these run with such a small amount of RAM?

He has no net connection and will mostly use it for playing Kolf, so I'm not too worried about security/updates/etc.

Thanks! :D

---

### Post by sidzen on 2011-05-20
With only 256MB RAM, KDE or Gnome will definitely be onerous to the system.  A base install of an LXDE (*i.e*. lubuntu) distro may be all it could handle. 

Suggest upping RAM to at least 512MB, if possible.  

Depending on other components of the system in question, especially CPU and FSB, you may want to look at something other than the 'buntus.  :(

---

### Post by linuxinstalledfromhdd on 2011-05-20
Crunchbang 9.04 works well in tight RAM situations. 

[http://crunchbanglinux.org/wiki/downloads/9.04.01](http://crunchbanglinux.org/wiki/downloads/9.04.01)

---

### Post by chellrose on 2011-05-21
Thanks for the info.  I'm not familiar with Lubuntu, does it come with some kind of desktop environment?  I tried installing Debian 3 (which I've used successfully in the past with 256MB RAM), but it only installed the terminal prompt -- no DE -- and that won't work well for him.

I'll look into the CrunchBang link.  Does that one have a desktop environment?

Thanks again.

---

### Post by sidzen on 2011-05-21
Please see 
[http://www.osnews.com/story/20598/6_of_the_Best_Lean_Linux_Desktop_Environments](http://www.osnews.com/story/20598/6_of_the_Best_Lean_Linux_Desktop_Environments)

---

### Post by wandalalakers on 2011-05-21
I recently burned a copy of antiX for computers that I will donate if they can't handle xfce or lubuntu. I burned the 486 version.

[http://distrowatch.com/table.php?distribution=antix](http://distrowatch.com/table.php?distribution=antix)

antiX is a fast, lightweight and easy-to-install linux live CD distribution based on MEPIS and Debian's testing branch for Intel/AMD x86-compatible systems. antiX offers users the "Magic of MEPIS" in an environment suitable for old computers. The goal of antiX is to provide a light, but fully functional and flexible free operating system for both newcomers and experienced users of Linux. It should run on most computers, ranging from 64 MB PII systems with a pre-configured 128 MB swap partition to the latest powerful boxes. 128 MB RAM is the recommended minimum for antiX while the installer needs a minimum of 2.2 GB hard disk space. antiX can also be used as a fast-booting rescue CD.

486 antiX
[http://distro.ibiblio.org/mepis/released/antix/antiX-M11-486.iso](http://distro.ibiblio.org/mepis/released/antix/antiX-M11-486.iso)

686 antiX
[http://distro.ibiblio.org/mepis/released/antix/antiX-M11-686.iso](http://distro.ibiblio.org/mepis/released/antix/antiX-M11-686.iso)


Quick Tips

Login as 'demo', password = 'demo'.
For root access, password = 'root'. Please do not login as root. It is totally unnecessary.

[IMG]http://i1-linux.softpedia-static.com/screenshots/antiX_1.jpg[/IMG]

Use 'sux' rather than 'su' when opening GUI apps as root in a terminal.
Sudo is not configured by default. antiX is not Ubuntu!
To boot from floppy, I suggest SmartBootManager.
antiX can also boot from an .iso file on a hard-drive. Boot from iso on hard-disk This is very fast.
antiX can also be installed as a livecd to usb. Using a live-usb-cd is very fast.
This site is under construction. For questions, comments, please use the antiX forum or the antiX forum on MepisLovers
There is also a lot of information suitable for antiX in the MEPIS wiki.
Link to full list of applications used in antiX. antiX-M11 antiX-M11-base antiX-M11-core

---

### Post by mörgæs on 2011-05-21
The only thing you should never consider is installing an unsupported release of Ubuntu.

Here is a list of light alternatives:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by chellrose on 2011-05-21
Thanks for all of the suggestions!  I'm going to give AntiX a go, and if that doesn't work I'll try one of the other alternatives.  I'll post an update once I get something installed...

---

### Post by tgalati4 on 2011-05-21
Be sure to install at least a 256 MB swap partition.  That will make the installation of older Ubuntu's proceed (although slowly).  I disagree with the notion that unsupported Ubuntu versions are not useful.  You just need to enable the backports repository and change to "old-releases" from "archive" in /etc/apt/sources.list.

The familiarity and stability of old Ubuntu LTS releases should not be overlooked.

---

### Post by mysteriousdarren on 2011-05-21
IMO I would switch to a recent release of ubuntu and put lxde on it. I have six machines that have nearly the same system specs and they fly with it. Just turn off the services that are not needed and optimize the boot too.

---

### Post by mörgæs on 2011-05-21
[COLOR=Black]@tgalati4:[/COLOR]

Yes, the old ones are stable, but one can not expect that all security bug fixes are backported. Some of them are, but if a number of holes are left unfixed (or not even investigated, which is likely) we are aiming for trouble.

---

### Post by chellrose on 2011-05-21
Thanks everyone.  I installed AntiX and it seems to work well.  I don't have a lot of time (moving soon), or else I'd give some of the other suggestions a go.  I'll mark this one solved for now...

Thanks again. :D

---

