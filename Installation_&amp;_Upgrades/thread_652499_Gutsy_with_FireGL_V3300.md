---
title: "Gutsy with FireGL V3300"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by Bob Pendleton on 2007-12-28
Hi, we started out with Dapper Drake, 6.06 LTS, using fglrx to drive a FireGL V3300 board hooked to two 24" Dell LCD monitors.  We loved the results, good resolution, and a large multi-screen desktop.  Now we followed the upgrade path Dapper to Edgy to Feisty to Gutsy, but we're unable to drive the video board at hi-res (can only get 1600 x 1200) or dual-head.  We've read a lot of web posts and tried to use the restricted-module version of the fglrx driver, but the computer just hangs.  The vesa driver has insufficient performance - no dual head capability.  The ati driver is similarly bad.  Has anyone used the direct download ATI driver instead of the one available through apt-get?  The latest has a date of 20 Dec 07, but we've been hesitant to deviate from the approved Ubuntu upgrade procedures.  So we'd be very grateful for any suggestions.  Bob and Bryan.  :confused:

---

### Post by buntunub on 2007-12-28
The latest ATI driver has FireGL support. Use ENVY and grab it. Or just run the install script off the downloaded version from the ATi website.

---

### Post by Bob Pendleton on 2007-12-29
Thanks, buntunub.

We were unfamiliar with ENVY and went to the website of Alberto Millone but were unable to install the debian package and were unable to extract the gzip, too.  Here's the error message:

Archive:  envy_0.9.9-0ubuntu4.tar.gz
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of envy_0.9.9-0ubuntu4.tar.gz or
        envy_0.9.9-0ubuntu4.tar.gz.zip, and cannot find envy_0.9.9-0ubuntu4.tar.gz.ZIP, period.

If you are Alberto Millone can you help us install your app?

Thanks

---

### Post by Partyboi2 on 2007-12-29
The deb package is the easiest way to install envy. What happened when you tried to install envy via the .deb package?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Bob Pendleton on 2007-12-29
Thanks,  we discovered some missing dependencies, installed them, and the ENVY install went forward.  We appear to have used ENVY to install the fglrx ATI driver, and are left with the task of enabling dual head.  Also, we're not sure how to recognize our 1920x1200 resolution capability.

But we're a whole lot further along, and ought to be able to tweak the system successfully from here.  Thanks very much for the pointer to ENVY.  It sure is a good tool!

Bob and Bryan:)

---

### Post by Bob Pendleton on 2007-12-30
Thanks to all.  After getting the fglrx driver installed with ENVY, it remained to edit /etc/X11/xorg.conf to add the hi-res mode and to enable dual heads by adding the 1920x1200 resolution to the Screen Section and by adding

	Option		"DesktopSetup"	"horizontal"
	Option		"Mode2"	"1920x1200"
	Option		"DesktopSetup"	"LCD,DVI,AUTO"
	Option		"EnablePrivateBackZ"	"yes"
	Option		"Hsync2"	"65"
	Option		"VRefresh2"	"60"

to the Device Section.  Not sure if all these options are necessary, as we don't have access to documentation for fglrx.  We simply copied these lines from earlier forum posts.  They had worked for us with 6.06.

Again, your quick responses appreciated!:)

---

