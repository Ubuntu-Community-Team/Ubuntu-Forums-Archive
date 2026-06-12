---
title: "netbook is very slow"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by tamedcynic on 2010-08-07
I tried loading Kubuntu Netbook on my HP Mini 210 (I'm a teacher.  I have a class set and this is my test one to see which Linux distro works best). It is running painfully slow.  I click and wait for minutes before something goes.  Is this common? Did something go wrong on the installation?  Is there a better option?

---

### Post by varunendra on 2010-08-08
As per HP's site, your netbook should have 1.66 GHz. processor with 1GB RAM. It should be more than sufficient for Kubuntu. There seems to be something wrong with the installation.

(I am running Ubuntu Studio 9.10 with most of the compiz effects enabled on a PC with 512MB RAM, and it is running faster than XP Pro. used to)

Running a Live session from a Live USB flash disk would be the best option to try a *buntu distro before installing it.

To create a Live USB disk, you can try [Unetbootin]("http://unetbootin.sourceforge.net/") or follow instructions on this page: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) (follow step 2).

---

### Post by tamedcynic on 2010-08-08
I tried using the Startup Disk Creator and then loading that.  I've always had great luck with Ubuntu.  I used Xubuntu on really old computers before and I used Ubuntu Studio last year with desktops, so I was a little surprised by this.

---

### Post by varunendra on 2010-08-08
> **tamedcynic said:**
> I tried using the Startup Disk Creator and then loading that.  I've always had great luck with Ubuntu.  I used Xubuntu on really old computers before and I used Ubuntu Studio last year with desktops, so I was a little surprised by this.

I thought you were new to ubuntu :).

All I can say is that I had recently (within 2 months) tried Kubuntu on VMware (devoting 512MB RAM on a Core2 Duo 2.8 GHz PC) and its speed was same as normal Ubuntu (I guess the loading time was more, but working speed was same.)

---

### Post by tamedcynic on 2010-08-08
I am new, in terms of knowing the way the systems really work.  I run Ubuntu on my Toshiba laptop and it works great.  Super-fast! 

I can't figure out why the installation is going so poorly.  I tried using the Startup Disk Creator.  Should I have used something else?

---

### Post by linux18 on 2010-08-08
> **tamedcynic said:**
> I am new, in terms of knowing the way the systems really work.  I run Ubuntu on my Toshiba laptop and it works great.  Super-fast! 

I can't figure out why the installation is going so poorly.  I tried using the Startup Disk Creator.  Should I have used something else?
if its bad to the point where you want to reinstall you can back up all of you data off the computer and reinstall using unetbootin and try linux mint, arch, xubuntu, or my distro (link in sig, 32-bit version coming tomorrow) which are all much faster than kubuntu.

---

### Post by varunendra on 2010-08-08
> **tamedcynic said:**
> I can't figure out why the installation is going so poorly.  I tried using the Startup Disk Creator.  Should I have used something else?
Installing from Startup Disk is same as installing from CD. There is no difference in the final installation.

However, if the live session (booting from the startup disk) too is running slow, then it may be some hardware compatibility issue. Try a different version then. If the speed in the live session is ok, then something might have gone wrong during installation. In that case, you may try reinstalling it.

By the way, which version of Kubuntu are you trying (name of the ISO file)? And what is its kernel version (output of command **uname -a**)?

---

### Post by tamedcynic on 2010-08-08
I'm trying Ubuntu Netbook now.  It feels a little sluggish with the  initial startup.  Not sure what the issue is.

---

