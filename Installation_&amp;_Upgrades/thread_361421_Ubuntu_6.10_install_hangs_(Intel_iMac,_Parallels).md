---
title: "Ubuntu 6.10 install hangs (Intel iMac, Parallels)"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by macpilot145 on 2007-02-14
Hello folks.

I have Parallels installed on my iMac and have been running XP on it.  I am interested in trying out Linux to see what it offers.

I downloaded the Ubuntu 6.10 image and burned it to CD.

I get to the point in the install where you see a dialog box that is titled "Installing System" and the status is "Loading module aec62xx for IDE chipset support" and it just hangs at that point.

Is there something I am doing wrong?  Are there any walkthroughs that give detailed specifics regarding Parallels as far as what options to select, etc?

Any help is greatly appreciated!

Thanks!

---

### Post by clith on 2007-02-15
As mentioned in [the Parallels forum](http://forums.parallels.com/thread5614.html), you need to reduce the RAM allocated to the virtual machine to 512 MB in order to install Ubuntu 6.10.

---

### Post by rabbashanks on 2007-02-19
I had this problem.  The workaround I found was to point the installer at the downloaded iso rather than at the CD itself.  Also, I had to boot into Ubuntu live, and then use the GUI installer - trying to install directly failed at CD ROM detection.

I was using a Macbook Pro running tiger, and Ubuntu Feisty Fawn 7.04

Hope this helps.

---

### Post by ronnietx on 2007-02-23
I am having this same problem. I am using an Intel dual processor mother board. 
Anyone know of any work arounds or at least how to get it past this point so it will boot from the harddrive?
Running demo straight from the cd works fine, just can't get it to install to the harddrive.
I am looking for an alternative to the ms small biz server and was hoping ubuntu was it, anyone have suggestions?

---

