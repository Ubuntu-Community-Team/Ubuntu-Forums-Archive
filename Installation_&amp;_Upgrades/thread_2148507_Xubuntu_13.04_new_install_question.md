---
title: "Xubuntu 13.04 new install question"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by motorcity909 on 2013-05-25
Hi all

I've been using Xubuntu since Feb 2012 but recently my hard drive failed so I've installed a new one today and installed Xubuntu 13.04 and have spent the past few hours installing applications and copying my music & photos etc across.  All fine.

Howevere, I just did a reboot and instead of the nice Xubuntu blue screen, I saw a terminal style screen with various commands running, followed when booting by a plain text "Xubuntu 13.04" with three dots beneath, rather than the nice spinning circle.  It reminded me of my first Ubuntu install back in 2009.

I hope this explanation is okay.  I guess I could film it if needed!

Have I done something wrong?

Above and beyond the vanilla install I have added - 

Ubuntu One, Tomboy Notes, Google Earth, Guayadeque, Libre Office and switched to the Nvidia 3.10 driver.

Many thanks for any help
Dave

---

### Post by Merrattic on 2013-05-25
Probably to do with the video driver

Have you rebooted a few times, usually sorts itself out in my experience ?

---

### Post by motorcity909 on 2013-05-25
I went back to the Nouveau driver and on re-boot got the nice Xubuntu screen.

So should I stay with that driver?  

What advantage (if any) does the Nvidia driver give me?  I'm not a gamer, no Steam or anything.

---

### Post by Merrattic on 2013-05-26
Given the driver comes from Nvidia it "should" be better |) however this is not always the case. If it all works OK with the Nouveau driver then stick with it ?

---

### Post by motorcity909 on 2013-05-27
I've ended up using the Nvida 310 driver.  Downside is when the computer boots or re-boots, there is a horrible looking terminal-style screen with various code shown ("battery checked - ok"), whereas the Nouvea driver gave the nice Xubuntu blue screen with the spinning circle.

However, with the Nvidia driver, window rendering is noticably smoother but more importantly the GPU temperature is much lower - around 40 degrees - whereas with the Nouvea it was 50+ even idling.

Cheers
Dave

---

### Post by fitzhugh on 2013-06-04
That information displayed is quite helpful when needed. Don't dispair, though, you can hide it. Instead of giving you my own instructions, typos and all, try following these:
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

If I recall correctly, you want to add:
quiet
to the list (or lack thereof) of kernel parameters.  If you google things like
kernel parameters, ubuntu boot options, linux boot quiet nosplash nomodeset, etc you'll find more info. As with the stream of info you don't want, knowing how to do this can be a great help - when needed.

The best list I've found is the pdf at the very bottom of [https://wiki.archlinux.org/index.php/Kernel_parameters](https://wiki.archlinux.org/index.php/Kernel_parameters)
It's for archlinux but is likely similar. I'm sure there are other lists, that's the one I had bookmarked.

hope this helps.

---

