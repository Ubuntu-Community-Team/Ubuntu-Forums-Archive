---
title: "Serious Nvidia graphic bug?"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by craigyjack on 2008-10-06
Hey guys,

Thought I would post this up here and get some feedback before I filed a bug, because frankly, I am not sure what to file in the bug report.

I upgraded ubuntu 8.04 to ubuntu 8.10 via update-manager -d, and I got some errors and a graphical mess-up after rebooting into the new 8.10. I thought it was my fault because I forgot to uninstall the nvidia proprietary drivers (via envyng) before upgrading. So I dlded the kubuntu 8.10 beta live cd, and was going to use that to reinstall. When booting off the live cd or installing via the live cd, I get this same graphical mess-up.

All I get after the loading splash screen is a flashing screen with vertical gray and green bars. This happened both via upgrade and off the live cd, so it leads me to believe there is a problem with the new nvidia drivers in 8.10. I redlded the live cd for ubuntu 8.04 and it works fine with no graphical mess-ups.

lspci shows my graphics card as: nVidia Corporation NV43 [GeForce 6800 GS] (rev a2)

Could someone give me some direction on what I need to do to get more info for this bug and be able to post a bug report for it, because I would like this issue to be looked into.

Thanks,
Craig

---

### Post by craigyjack on 2008-10-06
After some more forum searching, I am assuming this is similiar to the problems people are having with the new kernel. If i install kubuntu 8.04 and then upgrade to the 8.10, will the old kernel still be there in grub so I can boot up with the old kernel?

---

### Post by aimpau on 2008-10-06
I think so. Make sure when upgrading the kernel, choose the "install maintainer's" something option, so that you would still have the previous kernel in the grub.

Thanks for bringing up this topic since I'm using an nVidia graphics chip. You'd better bring this up in launchpad since you can elaborate on the events.

[Bookmarked]

---

### Post by craigyjack on 2008-10-06
Nope. Even when using the old kernel (2.6.24-19) with intrepid ibex I still get a screen full of vertical lines, flashing with grey and many colors. This leads me to believe it is definitely a nvidia graphics problem in 8.10, and not a new kernel problem.

---

### Post by aimpau on 2008-10-07
Hmmm...that's really wierd, since the only way for a hardware to communicate with the OS is through the kernel. Are you using ubuntu? Have you tried k/xubuntu?

---

### Post by Sef on 2008-10-07
> Nope. Even when using the old kernel (2.6.24-19) with intrepid ibex I still get a screen full of vertical lines, flashing with grey and many colors. This leads me to believe it is definitely a nvidia graphics problem in 8.10, and not a new kernel problem.

I wonder if the problem is with the NVidia driver on your system.   Uninstall it and see if the problem still exists.

---

### Post by dabl on 2008-10-07
> **craigyjack said:**
> 

 When booting off the live cd ... I get this same graphical mess-up.



The Nvidia driver isn't installed when you boot off the Live CD, so this is _not_ an Nvidia driver problem.

For my 9600GT, it is necessary to boot the 8.10 Live CD using F4 "Safe Graphics" mode.

After installing, video won't work on a normal boot.  I have to boot Recovery Mode, then use "Fix X" which sets it to a VESA display, then it works just fine.

The 177.78 beta driver, downloaded from [[COLOR="Green"]**here**[/COLOR]](http://www.nvnews.net/vbulletin/showthread.php?t=120052) runs just fine on my system.

---

### Post by beartard on 2008-10-07
Also I've never been able to get the 177.76 driver to work at all, where 177.73 works fine.  Certain nvidia cards work perfectly with whichever nvidia driver.  Others seem to only work with certain versions.  This is a problem that's been going on since the beginning of Intrepid.  Welcome to it!  ;)

---

### Post by craigyjack on 2008-10-07
Thanks. I just went back and installed kubuntu 8.04 right now. I have filed a bug report for the problem - [https://bugs.launchpad.net/ubuntu/+bug/279251](https://bugs.launchpad.net/ubuntu/+bug/279251).

I tried using the Fix X option once to no avail. I will try booting up in safe graphics mode and see if I can get it to install without the nvidia stuff, and manually install the nvidia driver. I hope the issue gets resolved before the final release through, I really like the envyng integration into the OS they have going.

---

### Post by aimpau on 2008-10-07
> **craigyjack said:**
> Thanks. I just went back and installed kubuntu 8.04 right now. I have filed a bug report for the problem - [https://bugs.launchpad.net/ubuntu/+bug/279251](https://bugs.launchpad.net/ubuntu/+bug/279251).

I tried using the Fix X option once to no avail. I will try booting up in safe graphics mode and see if I can get it to install without the nvidia stuff, and manually install the nvidia driver. I hope the issue gets resolved before the final release through, I really like the envyng integration into the OS they have going.

That's the great thing I learned about linux. You can fix linux with linux. Try fixing windows w/ windows...:D

I'm checking out the new beta drivers for nVidia. If mine works, then it's probably a matter of drivers for video **chips** and video **cards**.

---

### Post by nanog on 2008-10-08
envng has been replaced by dkms. perhaps thats why you had problems.

---

### Post by aimpau on 2008-10-08
I thought dkms was only for kernel building so as not to reboot after installing a new kernel?

---

### Post by sloggerkhan on 2008-10-08
dkms is what makes it so you don't have to reinstall proprietary graphics drivers after kernel updates.

---

### Post by craigyjack on 2008-10-11
I believe envyng is still used in ibex. The envyng website says it works in conjunction with dkms:

"D) What happens if I upgrade Ubuntu to a newer release (e.g. from Ubuntu 8.04 to Ubuntu 8.10)?

Nothing bad should happen, since EnvyNG is 100% compatible with Ubuntu.

E) What shall I do to enable the required repositories on Ubuntu?

You will have to enable Ubuntu's "universe" and "multiverse" repositories. Have a look at this page to see how you can do it (read where it says Enabling Extra Repositories on that page): Enabling Extra Repositories

F) What happens if the kernel is upgraded (e.g. via system updates)?

You won't have to do anything at all. DKMS will automatically install the module for your new kernel. NOTE: make sure that the kernel headers (linux-headers) for that kernel are also installed. "

---

