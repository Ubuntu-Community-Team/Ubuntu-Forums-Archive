---
title: "32-bit or 64-bit installation? Other options? What would you do?"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by sunkssss on 2008-10-26
Hello all

I've never been able to get an Ubuntu installation to work on my computer (except for one which got stolen the week after I had it setup :roll:) and I now have a brand new computer that I've built, but it seems I've made some poor decisions when I bought on a tight budget. I have a Pentium Dual Core E2200 @ 2.2Ghz and an Nvidia 8600GT with 1GB Ram and an rtl8187L chipset based wireless adapter. Now when I had Ubuntu 32-bit installed I was able to get my wireless working through ndiswrapper and I was able to find some workarounds for my 8600GT and some glitches it was causing from poor driver support, but performance was terrible. Compared to the multitasking I was able to achieve in Windows XP 32-bit Ubuntu couldn't even seem to start the race. I then decided to install the 64-bit version of Ubuntu, and the system does seem much snappier, but I cannot get any drivers working through ndiswrapper for my wireless, and I don't even know if my 8600GT will be supported fully yet. 

I guess my question is.... what would you do if you were in my situation? What are my options? Would you try and go back to 32-bit operation and try to tweak the system so that it performed adequately? Is that even possible? I'm a noob in the Linux world, but if I'm ever able to get the thing working that would hopefully change. But as of now, some divine force doesn't seem to want that to happen.

---

### Post by Spaceman9 on 2008-10-26
8600 GT and Nvidia driver problem [http://ubuntuforums.org/showthread.php?t=782819&highlight=Nvidia+8600GT+installing+drivers](http://ubuntuforums.org/showthread.php?t=782819&highlight=Nvidia+8600GT+installing+drivers)

or

Linux Mint 5 [http://www.linuxmint.com/](http://www.linuxmint.com/)

Mandriva 2009 [http://www.mandriva.com/](http://www.mandriva.com/)

---

### Post by mikewhatever on 2008-10-26
I'd also try another distro, unless you can figure out what causes the problems. Linux Mint would not be my first choice, since they appear to be based on Ubuntu, but there are many others. I am not much of an expert to recommend, but I'd try OpenSuse and Mandriva.

---

### Post by sunkssss on 2008-10-26
Does Mandriva have better driver support? Because it's essential that I be able to set up my wireless. Do you think the 8.10 release will have better driver compatibility? If so, I'll be very excited to try it out. Also is the Mandriva 2009 64-bit supposed to be in excess of 4.0Gb? That's a lot larger than the 32-bit release, by about a whole 3.0GB!

Also there is another thread that discusses the issue with this wireless driver:

[http://ph.ubuntuforums.com/showthread.php?t=911581](http://ph.ubuntuforums.com/showthread.php?t=911581)

Another thread says Kubuntu will work with this driver:

[http://ge.ubuntuforums.com/showthread.php?t=888120](http://ge.ubuntuforums.com/showthread.php?t=888120)

Which is better than? Kubuntu or Mandriva?

---

### Post by Spaceman9 on 2008-10-26
From the release notes for 8.10 [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

nVidia "legacy" video support

The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration. 

Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade.

Ok, the Kubuntu vs Mandriva thing. At the end of the day the better one is the one that runs on your hardware.




Not all distros work with all hardware. Sometimes you just have to keep trying untill you find one that works.

8.10 might have what you need but it might not too. Mandriva (based on RedHat) works better with some old hardware. Sabayon is based on Gentoo. OpenSUSE is based on it's own project. Sidux is based on Debian just like Ubuntu and Linux Mint.

It took me a year and a half of trying different distros and updates of distros to find one I could live with. 

I just thought of something. PC-BSD supports nVidia much better than ATI. PC-BSD is based on FreeBSD. You could try PC-BSD if you don't mind the advantages of FreeBSD.

---

### Post by sunkssss on 2008-10-26
I'm downloading the Mandriva 2009 64-bit release right now, and will give it a go. Otherwise I may give PC-BSD a try since I would like to have good nVidia support, yet I ultimately need a system that works with my wireless adapter, even at the expense of graphics performance (since I won't be relying upon Ubuntu for gaming and photo editing, not for now at least). So many cd/dvds! There should be a goodwill for mailing all these discs to when the user has no use for them anymore, or perhaps an exchange service where you trade discs.

---

### Post by mikewhatever on 2008-10-26
> **sunkssss said:**
> Does Mandriva have better driver support? Because it's essential that I be able to set up my wireless. Do you think the 8.10 release will have better driver compatibility? If so, I'll be very excited to try it out. Also is the Mandriva 2009 64-bit supposed to be in excess of 4.0Gb? That's a lot larger than the 32-bit release, by about a whole 3.0GB!

There is no such thing as better or worth driver support, simply because most drivers are device specific and not generic. The interesting question is, will Mandriva work better on your hardware. I don't know, but there is a chance it will, as well as Ubuntu 8.10. You may want to do some research on your specific hardware compatibility before downloading.

---

