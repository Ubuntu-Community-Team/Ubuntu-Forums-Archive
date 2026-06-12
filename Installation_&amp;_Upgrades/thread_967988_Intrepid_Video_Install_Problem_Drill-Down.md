---
title: "Intrepid Video Install Problem: Drill-Down"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by horned0wl93 on 2008-11-02
After listening to much in here about blank screens after upgrading to or installing Ubuntu 8.10, I went to the source and tried to install the drivers, myself.

On the [COLOR="black"][ATI Catalyst web site]("http://ati.amd.com/support/drivers/linux/linux-radeon.html")[/COLOR], there are two drivers that should work ideally on my system. The first targets my specific video card.  The second targets the Ubuntu Intrepid upgrade:

1. ati-driver-installer-8.523.1.1-x86.x86_64.run
2. ati-driver-installer-8-10-x86.x86_64.run

My command to install either package, from the driver's directory:

1. sudo sh ./ati-driver-installer-8-10-x86.x86_64.run --buildandinstallpkg

After the kernel checks the package and declares "all good,"  I get a series 8 rows of dots, and then this:

=================================================
[COLOR="Red"]ATI Technologies Linux Driver Installer Packager[/COLOR]
=================================================
Generating and Installing Package: Ubuntu/Intrepid
Resolving Build Dependencies ...
Reading Package Lists ... Done
Building Dependency Tree
Reading State Information ... Done
E: Couldn't find package  can't
Unable to resolve  can't parse dependency ooobasis30-en_us-res
can't parse dependency ooobasis30-en_us-help
can't parse dependency ooobasis30-en_us
can't parse dependency ooobasis30-en_us-base
can't parse dependency ooobasis30-en_us-binfilter
can't parse dependency ooobasis30-en_us-math
can't parse dependency ooobasis30-en_us-calc
can't parse dependency ooobasis30-en_us-impress
can't parse dependency ooobasis30-en_us-draw
can't parse dependency ooobasis30-en_us-writer

See a pattern here?  Though I can't, for my life, understand why OpenOffice is a required dependency to load a video driver, I tried to apt-get install ooo30-en_us.  Guess what?  "[COLOR="Red"]ooobasis30[/COLOR]" is invalid.  System reads "[COLOR="Red"]ooobasis3.0[/COLOR]" present, and tells me that I have the most recent version. 

Now, if the Intrepid install employs the same ATI package for its video driver install, I can see the problem.

The bigger problem for me?  I dunno how to write a script to fix it... Help?

Cheers;
Ed

---

