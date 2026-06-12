---
title: "firefox 3.1 not working anymore"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by giorsat on 2009-04-02
after xulrunner update  shiretoko doesn't start anymore.
Could not find compatible GRE between version 1.9.1b3 and 1.9.1b3.

does anybody know what it means?=

---

### Post by KhaaL on 2009-04-02
I also have this issue. too bad i did update before running shiretoko :D

---

### Post by stoffe on 2009-04-02
I'm finding bugs like this one: [https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/201938](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/201938)

But I'm unable to make any reinstalls or purging of configs that actually work. Could use some help here. :)

---

### Post by melalcoolique on 2009-04-02
It may be related to this:

[https://lists.ubuntu.com/archives/jaunty-changes/2009-April/008671.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-April/008671.html)

---

### Post by stoffe on 2009-04-02
Reported a bug to track the issue: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.1/+bug/353660](https://bugs.launchpad.net/ubuntu/+source/firefox-3.1/+bug/353660)

Seems this happens now and then, judging from what I find in Launchpad. :)

---

### Post by dirtylobster on 2009-04-02
I noticed the same this morning but fortunately 3.0 doesn't seem to crash my Eee PC 1000H anymore so I'm sticking with that.

---

### Post by phill on 2009-04-02
You're right, it's to do with the update to XULRunner-1.9.1 in preparation for 3.5b4 (name update from 3.1b3).

The way to solve it is to go to your local archive, e.g. 
[http://archive.ubuntu.com/ubuntu/pool/universe/x/xulrunner-1.9.1/?C=M;O=A](http://archive.ubuntu.com/ubuntu/pool/universe/x/xulrunner-1.9.1/?C=M;O=A)

and download the earlier release (b3) of the following two packages (7th March date):
[I]xulrunner-1.9.1_1.9.1~b3+build2+nobinonly-0ubuntu1_ARCH.deb
xulrunner-1.9.1-gnome-support_1.9.1~b3+build2+nobinonly-0ubuntu1_ARCH.deb
[/I]
Don't forget to pick the correct architecture for your system.

Install them both with `sudo dpkg -i xulrunner*deb` and firefox-3.1 will run again!

---

### Post by stoffe on 2009-04-02
> **phill said:**
> You're right, it's to do with the update to XULRunner-1.9.1 in preparation for 3.5b4 (name update from 3.1b3).

The way to solve it is to go to your local archive, e.g. 
[http://archive.ubuntu.com/ubuntu/pool/universe/x/xulrunner-1.9.1/?C=M;O=A](http://archive.ubuntu.com/ubuntu/pool/universe/x/xulrunner-1.9.1/?C=M;O=A)

and download the earlier release (b3) of the following two packages (7th March date):
[I]xulrunner-1.9.1_1.9.1~b3+build2+nobinonly-0ubuntu1_ARCH.deb
xulrunner-1.9.1-gnome-support_1.9.1~b3+build2+nobinonly-0ubuntu1_ARCH.deb
[/I]
Don't forget to pick the correct architecture for your system.

Install them both with `sudo dpkg -i xulrunner*deb` and firefox-3.1 will run again!

Ah, awesome, thanks! I tried almost this, but missed that the second package was neede. Thanks a lot!

---

### Post by phill on 2009-04-02
> **phill said:**
> You're right, it's to do with the update to XULRunner-1.9.1 in preparation for 3.5b4 (name update from 3.1b3).


Firefox 3.5 (beta4) has now hit the repos...

---

### Post by BGFG on 2009-04-02
Glad to see I was not the only one with this issue. As Phil said, I'll update and see if the new beta runs with the new xlrunner.

Thanks.

---

### Post by Dominator86 on 2009-04-02
The xulrunner update fails for me with error code 135.

Now even firefox 3.0 won't work anymore. :sad:

Any ideas?

Edit: epiphany is affected too, so which browser can I use until this gets fixed?

---

### Post by BGFG on 2009-04-02
try Dillo or Midori :)

---

### Post by Dominator86 on 2009-04-02
Thanks, but I just found out that firefox 3.5 works (the updates are still broken).

First I thought firefox 3.5 didn't install because I couldn't find it, but then I found out it's actually called 'A Web Browser 3.5'.

Very strange. :confused:

---

### Post by andrek on 2009-04-02
I use this ppa : [http://launchpad.net/~ubuntu-mozilla-daily/](http://launchpad.net/~ubuntu-mozilla-daily/) to get the daily builds of firefox 3.6 alpha and yet it is stable and fine. No errors at all.

---

