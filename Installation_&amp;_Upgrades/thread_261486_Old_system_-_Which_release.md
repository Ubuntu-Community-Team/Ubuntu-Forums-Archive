---
title: "Old system - Which release?"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by willyram on 2006-09-20
Hi all!
I have an old desktop at home: AMD K6-2 500MHz, 256Mb RAM, but with a new IDE 80Gb HDD.
I've just installed Breezy as I had the CD at hand. After some browsing through the forums and previous linux experiences, I've made a server install, then installed xfce (4.2.2). Tried to install xdm but got some problems, tried WDM, different kind of problems, ended with GDM and good so far (although I would like to use either XDM or WDM to use the less resources as possible).
I really want a fast system but have the software as current as possible (as performance permits). 
So far the system is work really nice. Right now, my XFCE flies (not as much as with a Sarge, but nevertheless responds nicely and I like the 4.2.2 version much more than the 3.90 on Sarge). 
But I am wondering if doing a similar install (ie: server + my_selection_of_lightweight_sw) of dapper or even edgy would make sense, to catch up.
I am wondering if the new kernel, the new X, the new XFCE, the new Firefox/Switfox and Thunderbird (if possible I prefer it over sylpheed) will indeed run with better performance or they are built with an assumption of being used on more powerfull hw than the one I have and so I will end up having a slow, sluggish system. I've read that this software is going through major overhauls, but I wonder if the new compilers optimize for the type of system I have.
Any thoughts, ideas, suggestions?
Thanks! Willy

---

### Post by wpshooter on 2006-09-20
My first question would be why are you installing Breezy when Dapper Drake 6.06.1 LTS version is available for download & installation ?

Thanks.

---

### Post by willyram on 2006-09-20
Seems I've tried to make a long story short, but it seems I've made it much too short....

So, let me answer:

1. As I said, I had the CD at hand and could not wait to download the dapper.
2. Later, I indeed downloaded dapper, and tried to install it, but ended with the "Waiting for root file system" thing and after trying for a while (1 day) couldn't get to solve it (the UUID fix didn't worked out) so I resorted back to Breezy and it installed flawlessly ("server mode").
As part of dealing with this process, I've tried Etch, but I ended with an unusable system, so so slow, I was wondering if I had did anything wrong (which perhaps that was the case). 
And Etch seems looks a lot like dapper and edgy, so here comes my question. 
Also, as I couldn't install dapper first-hand, I was wondering if giving a try to edgy knot 3...
pd: Of course I've reformated everything between installs, just in case.

---

### Post by wpshooter on 2006-09-20
Here is what I would do.

This is assuming that you have nothing on the computer that you need to keep or backup.

I would go to this site and download the killdisk wiping program and I would wipe the hard drive.

[http://www.download.com/3000-2092-10188745.html](http://www.download.com/3000-2092-10188745.html)


I would download and BURN (not copy) both the DESKTOP (sometimes referred to as the live CD edition) and also the ALTERNATE cd versions of Dapper Drake 6.06.1 LTS.  Make sure your are getting 6.06.1 and not just 6.06.  P.S. - I recommend using CD-RW media for this.

After you have wiped the hard drive, then make sure your CD is the first boot device in BIOS and boot to the DESKTOP cd version and then make sure that the very first thing you do is to run the verification/integrity test on the CD from the initial boot screen menu.  Once the verification has been made and PASSED, then go back to the menu and choose the installation choice.  When you get to the desktop, click on INSTALL icon then proceed with the installation.  If by some chance the DESKTOP CD version does not work then WIPE again and then try the ALTERNATE CD version.

Good luck.  Write back if you have more questions.

---

### Post by Zed on 2006-09-20
If you have a Breezy install CD, do a server install. Then [upgrade Breezy to Dapper](http://ubuntuforums.org/archive/index.php/t-87262.html). Then:

```

apt-get install xubuntu-desktop

```

This will get you a working XFCE environment without the headache of figuring out all the packages you need to work up from a server install. Xubuntu should be fine with your hardware. 

[Fluxbuntu](http://fluxbuntu.org/) is a new derivative designed to work well with old hardware; you may like to try it, but it's only at its first alpha release -- use at your own risk.

---

### Post by willyram on 2006-09-20
Thank you very much for your suggestions. I will proceed with them and report back as feedback what I find.
Cheers, Willy.;)

---

### Post by jISh on 2006-09-20
I'd do a server install of Ubuntu and then install openbox or fluxbox and work from there. That's what I have on my laptop 677MHZ Pentium 3/128MB RAM. Boots in around 2 minutes and is quite zippy (except Firefox).

---

### Post by DJiNN on 2006-09-21
Failing that, if none of the above is what you seek, you could always give [Zenwalk]("http://www.zenwalk.org") a try. It's very modern, but isn't bloated & is very fast even on older systems. If you then install Fluxbox or OpenBox and use that as a WM, you should have a pretty zippy little machine. 

Good luck, whatever you choose to do.

---

### Post by willyram on 2006-10-19
Hi guys, I ended installing Breezy and although it works, when I want to _really_ work with it (many tasks open) it starts to slow down a lot. Do you had any experiences in using Suse Linux with this hardware? I've been told it's a very mature and polished distro.

---

### Post by DJiNN on 2006-10-20
> **willyram said:**
> Hi guys, I ended installing Breezy and although it works, when I want to _really_ work with it (many tasks open) it starts to slow down a lot. Do you had any experiences in using Suse Linux with this hardware? I've been told it's a very mature and polished distro.

Suse is mature & polished, but it's also quite a heavyweight, and if you're still using the same hardware then i wouldn't hold out much hope. :) I don't think it's made for the "Lightweight" kind of setup.

On the other hand, you could give [Fluxbuntu]("http://www.fluxbuntu.org") a try..... It's based on Ubuntu (Server install basically) and uses Fluxbox as a WM. It's lightweight, fast, and hopefully will breathe some life into your machine. :) 

Other than that, try [Zenwalk]("http://www.zenwalk.org") if you get a chance..... it really is a fast little distro, even on old machines. I use it here on an old P3 700mhz machine & it's fantastic! :)

---

