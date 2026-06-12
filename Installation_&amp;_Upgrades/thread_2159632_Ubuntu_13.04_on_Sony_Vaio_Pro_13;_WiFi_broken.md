---
title: "Ubuntu 13.04 on Sony Vaio Pro 13; WiFi broken"
date: 2013-07-03
forum: Installation &amp; Upgrades
---

### Post by ooddiittyy on 2013-07-03
Caveat: I know nothing (Jon Snow) about Linux, other than very minimal exposure to both Mint and Ubuntu on desktop systems.


Just got the new Sony Vaio Pro 13 and, due to an underabundance of forethought wiped Windows and installed Ubuntu 13.04. Wireless, I am now aware after browsing a number of forums, doesn't seem to be playing nice with the newer hardware. There is [this]("http://ubuntuforums.org/showthread.php?t=2153589&p=12714830#post12714830") thread which mentions a bootstrap fix for it in Fedora 19, but I am not familiar enough with Linux to know whether that would be viable in Ubuntu.


Does anyone have any n00b-friendly advice that might help? I would greatly appreciate it. Worst-case I can always reinstall Windows, but I think we're all aware of how worst of a case that would be.

---

### Post by MikeCyber on 2013-07-04
I've installed two days ago 13.04 and my wifi works in Unity. Haven't seen it in Gnome...but only two days. Anyway works perfectly out of the box with a Asus Z87-Pro. I needed grub-repair for 
this UEFI board. Asus even seems to support Linux, hence I'm very happy with that.

---

### Post by ooddiittyy on 2013-07-04
> **MikeCyber said:**
> I've installed two days ago 13.04 and my wifi works in Unity. Haven't seen it in Gnome...but only two days. Anyway works perfectly out of the box with a Asus Z87-Pro. I needed grub-repair for 
this UEFI board. Asus even seems to support Linux, hence I'm very happy with that.

Thanks for the response, but I wasn't suspicious of Ubuntu itself being the problem, just trying to figure out whether anyone has a workaround for the drivers for whatever wireless hardware Sony included in the Vaio is all.

---

### Post by MikeCyber on 2013-07-04
First of all I would update. Google and maybe even try 13.10.

---

### Post by darksaboteur on 2013-07-05
ooddiittyy: check out [https://spicious.com/sony-vaio-pro-11-with-ubuntu.html](https://spicious.com/sony-vaio-pro-11-with-ubuntu.html)
It is for the Vaio Pro 11 but the steps are the same as the WiFi is the same card.

---

### Post by ooddiittyy on 2013-07-12
> **darksaboteur said:**
> ooddiittyy: check out [https://spicious.com/sony-vaio-pro-11-with-ubuntu.html](https://spicious.com/sony-vaio-pro-11-with-ubuntu.html)
It is for the Vaio Pro 11 but the steps are the same as the WiFi is the same card.

Thanks for this; I saw that page awhile ago, but it's a bit over my head as far as self-compiling kernels goes...also, he only manages to boot in BIOS mode rather than UEFI, which seems like more of an effort than I currently want to invest. I really appreciate the help, though; I'm unfamiliar with the flow of development for the different distros, but does anyone have any general recommendations for where to watch for compatibility updates for Ubuntu, i.e. somewhere I could peruse to to determine when the UEFI installation on the Vaio Pro might be fully supported?

---

### Post by anewbie on 2013-08-05
I'm curious have you tried again? According the comments in that thread it sounded like the most recent kernel has the appropriate patches to fix the issue....

---

### Post by ooddiittyy on 2013-08-06
> **anewbie said:**
> I'm curious have you tried again? According the comments in that thread it sounded like the most recent kernel has the appropriate patches to fix the issue....

I have read similar things, but I've also heard that there are still some issues related to the pstate drivers for the CPU clockspeed...I'm currently just running Linux inside a virtual instance, but eventually I will try a real install. Kind of hoping that someone with more experience will guinea pig it for me first. :)

---

### Post by pgrim91 on 2013-08-23
I'm very interested in getting this laptop, but the difficulty users are having getting Ubuntu on it is making me think otherwise.  Has anyone followed the spicious article/instructions and can say how long it takes to get up and running?

---

### Post by Toufik on 2013-09-12
Get the latest 13.10 image, wifi should work. If unsure, get the latest kernel here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-saucy/) : copy linux-headers*amd64.deb, linux-headers*all.deb and linux-image*amd64.deb on a thumb drive so you can install them on your vaio.

---

