---
title: "Xubuntu via mini.iso rocks for old PCs"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by DavidTangye on 2008-01-11
Just a quick note to recommend the mini.iso and Xubuntu desktop installation. I got a 6 year old PC up and running nicely this way.

Essentially this is what I did:

Downloaded the ubuntu mini.iso, burnt a CD, and installed it using the 'cli-expert' option.

Logged in and ran 'sudo apt-get install xubuntu-desktop', plus a couple of extra packages: the ubuntu splash, xubuntu artwork/theme, and gdm packages, so it would boot and give a nice gdm login.

Hacked the /etc/X11/xorg.conf file to use a vesa driver, then later the trident driver without the DRM GL etc stuff, as it seemed to have given trouble previously with the Xubuntu live CD (ie crashes and restarts). Actually, and Live CD only worked in 'Safe Video' mode, and I had saved the xorg.conf file it had generated. I would have Installed from its desktop, but if i tried to do that, it seemed to go away from 'Safe Video' mode for the install, and the CP would crash during the install, hence my switching to the above install with the mini.iso.

The other nice thing, is that you don't download a CD that has many megs of outdated software that is then effectively discarded and upgraded via the 'net post-install. The mini-iso simply installs most of the packages, eg ubuntu-desktop and all its dependents, directly off the 'net repos. So this seems to be to be the best way to go, as long as you have reasonable broadband, eg 512Kb or better ADSL, cable or T1 etc.

---

### Post by pointyblue on 2008-01-15
Hi David,

I'm trying to install Xubuntu 7.10 to an old pc via the mini.iso as well. It actually runs pretty good but it's a little slower than I hoped it would be.

Could you please explain (yes I'm new at this! ;) ) in detail what exactly this means:

> Hacked the /etc/X11/xorg.conf file to use a vesa driver, then later the trident driver without the DRM GL etc stuff

Also, do you have any ideas on how to make Xubuntu as fast as possible?

---

### Post by DavidTangye on 2008-02-12
Sorry about the delay in replying.

If Xubuntu is too slow, you will find that icewm (also available from the mini.iso, ie from the repositories) is faster. The same old pc now boots, in order of speed:
 - Xubuntu (plus some server stuff) from the mini.iso (slowest)
 - Icewm  from the mini.iso in another partition
 - Puppy (fastest)

Rather than tune the systems, I just have them all fairly standard, and boot the system I need. All can share common areas for my files, linked to as /home/me/common in each Xubuntu and Icewm setup, and /root/common for puppy.

For getting the X display to work, I ran 'dpkg-reconfigure xorg-server', on the ubuntu side, which created the /etc/X11/xorg.conf file. It is then clonable for the ubuntu and puppy systems. However the file that Puppy created worked best, so I hacked code from it into the ubuntu equivalents. 'man xorg.conf' explains the file in detail, if you want to hack it.

---

