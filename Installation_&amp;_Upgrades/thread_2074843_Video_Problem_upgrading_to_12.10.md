---
title: "Video Problem upgrading to 12.10"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by wide-load on 2012-10-22
I upgraded from 12.04 to 12.10 and now I can't use Ubuntu.  When I log in it goes to my desktop.  The Xsensors app is in my startup folder and it is huge on my screen. I get no App launch bar at the left hand side of the screen and no bar at the top.  I read another thread that had similar problems.  They suggested that you right click in the desktop and drill down to third party drivers and select a different video driver.  However when I go there there are no additional drivers listed.

My MB is a Gigabyte GA-785 with an integrated ATI Radeon 4200 HD video card.

I tried going to a command prompt and going to Failsafex mode and that doesn't work.  After I answer the question about remounting in read write mode I get a message that says "FSCK from util-linux 2.20.1
/dev/sda1: clean"

Then it stalls and goes nowhere else.

I'm not a techie no I need some step by step help here.

---

### Post by Mark Phelps on 2012-10-22
I have a similar setup and like you, 12.10 will not boot properly for me.  

Unfortunately for you, Canonical STILL will not provide any "restore" or Rollback" capability to get your old version back.

Sorry, don't have a solution at present -- I'm looking for one, too.

---

### Post by wide-load on 2012-10-23
Looking at another thread that talked about this same issue, I found a fix.  The following code was suggested.

sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx

I tried it.  The first one didn't do anything in my situation.  The second one did.  I now have a full desktop, running 12.10.

Editorially I would say I don't think 12.10 was tested very thoroughly before it was released.  There are many people on the forum that seem to be having this issue.  I can't believe it wasn't caught before release.  I had made a LiveDVD for 12.10 Beta and ran it.  I did not have this problem when I ran it.  It was only after I upgraded my system that things went south.

---

### Post by Mark Phelps on 2012-10-24
Also found a solution that gets me a working desktop ...

add "rootdelay=90" to your Linux kernel parms.

I tried that and I got to a working desktop.  I also experimented with different settings and found I could reduce the value to 45 and still have it work.  Anything less gave me a command line.

Hope this helps some of you who are not getting to a desktop.

---

