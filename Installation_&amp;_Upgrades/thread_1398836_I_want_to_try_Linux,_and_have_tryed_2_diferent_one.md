---
title: "I want to try Linux, and have tryed 2 diferent one's and neither work."
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by DonutFUN on 2010-02-05
I want to try out a Linux on my PC (dual boot, and put it on my other hard drive) , the two I've tried are Ubuntu and Gentoo, and I'll post the error messages i get here:
Ubuntu:
"init: rc-default main process (3355) terminated with status 127"

Gentoo
It just comes up to the "livecd ~ # _" (underscore flashing to show being able to type)
and I've tried the "nano /etx/X11/xorg.conf" to as I've found on the internet and it doesn't work.
also a little higher it has a red star (as opposed to green like the rest) saying:
"ERROR: cannot start nfsmount as rpc.statd could not start"

The other problem being that I am out of blank CD's, and can't afford to buy any more at this time, so that's what I'm stuck with.

---

### Post by amsterdamharu on 2010-02-05
If you have a 1G usb stick you can use unetbootin to "boot" from the usb.

You might try to run the live cd "try ubuntu", does that not start? If that starts but install doesn't work maybe try the alternate iso to install ubuntu, or use the install on the desktop when running live cd.

---

### Post by DonutFUN on 2010-02-05
well the thing is i have no more blank CD's, and my computer doesn't like booting off of USB stick, (I've tried), and when i say doesn't like, i mean just doesn't.

---

### Post by amsterdamharu on 2010-02-05
I just rememberd that unetbootin can boot the iso off your harddisk as well. Without destroying what is already on the harddisk of course.

---

### Post by DonutFUN on 2010-02-08
I've also gotten as far as installing Ubuntu via inside windows XP, and it still just comes to the same error.

I have an Intel Pentium 4 2.93 GHZ processor, with 2.49 Gb Ram, and I do have 2 Hard drive's, (I can't quite format either clean because I don't have anywhere to put the stuff) and I have a Radeon 9250 (if that helps even)

any ideas? or even just any other distro's i could try? preferably being able to install from inside XP, because I have daemon tools, so i can load the disk and install to my second hard drive that way, but I'm out of cd's, and my computer can't boot from a usb drive, maybe an sd card though

---

### Post by SeanHodges on 2010-02-08
> **DonutFUN said:**
> I want to try out a Linux on my PC (dual boot, and put it on my other hard drive) , the two I've tried are Ubuntu and Gentoo, and I'll post the error messages i get here:
Ubuntu:
"init: rc-default main process (3355) terminated with status 127"

Gentoo
It just comes up to the "livecd ~ # _" (underscore flashing to show being able to type)
and I've tried the "nano /etx/X11/xorg.conf" to as I've found on the internet and it doesn't work.
also a little higher it has a red star (as opposed to green like the rest) saying:
"ERROR: cannot start nfsmount as rpc.statd could not start"

The other problem being that I am out of blank CD's, and can't afford to buy any more at this time, so that's what I'm stuck with.

This question suggests the problem lies with your graphics card:

[https://answers.launchpad.net/ubuntu/+question/77032](https://answers.launchpad.net/ubuntu/+question/77032)

If you try taking your Radeon graphics card out of your PC, and see if Ubuntu then boots correctly, then the solution might be to add a blacklist setting to the boot options (as suggested in that link). 

If the problem doesn't go away immediately, you may need to re-install Ubuntu with the graphics card removed so the change is recognised. If you have installed Ubuntu from Windows, then you should be able to do this in the Add/Remove programs.

Try booting without the graphics card first to see if this is the case, and let us know.

---

### Post by amsterdamharu on 2010-02-08
I suggested unetbootin because something might be wrong with your CD drive since 2 installs failed from CD. (pref post makes sense too with the unsupported video card)

Unetbootin will take files out of your iso and put them on C: then when you reboot you'll get a menu, choose unetbootin and the install CD will start from your harddisk.

Did you create a partition for Ubuntu? If not then use unetbootin to start live CD mode (think it's try ubuntu in the menu after unetbootin menu). Here you can resize your windows partition to make some space for ubuntu and then install it. Thre is an icon in the desktop saying install ubuntu when you run live CD.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Mark Phelps on 2010-02-08
Sorry, but your Radeon is not supported with ATI drivers in Ubuntu anymore.  However, Ubuntu should detect it and load the open source drivers by default.  Just don't try downloading and forcing the installation of ATI drivers -- that will totally hose up your display.

---

### Post by DonutFUN on 2010-02-08
When I get home I'll try try without the Radeon, I have it and my internal display both turned on (so i can have 2 monitors and my T.V. all at once) so i can just change the priority one to the Intel internal video adapter and try then.

---

### Post by DonutFUN on 2010-02-08
So it is the Radeon, so how do I get it to load the drivers? and also do you know of any way that I can load Gentoo without another cd (since I am out of cd's)

---

### Post by amsterdamharu on 2010-02-08
Dont know about the radeon driver. To answer your question about the cd (for the 3rd time):
[http://ubuntuforums.org/showthread.php?t=1398836#7](http://ubuntuforums.org/showthread.php?t=1398836#7)

---

### Post by DonutFUN on 2010-02-09
I got it booted and installed and it works, I just have to go into the bios every time to change the primary video adapter the the onboard, all I need to know now is how to get my readeon 9250 to work with linux

---

### Post by amsterdamharu on 2010-02-09
Mark Phelps noted "```
Just don't try downloading and forcing the installation of ATI drivers -- that will totally hose up your display. 
```"

I have no experience with it maybe under system -> administration -> hardware drivers

You're videocard is switched off when you boot Ubuntu so it'll probably never detect it, are you sure now you've installed it it wouldn't boot with the card enabled?

Here is some more stuff I found on the Internet:
[https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI)
Old article though.

In my Ubuntu 10 there is still a package called xserver-xorg-video-ati the article above mentioned and the description says:

> This driver for the X.Org X server (see xserver-xorg for a further description)
provides support for the ATI Mach64, Rage128, Radeon and FireGL series.
It provides the 'ati' driver wrapper which loads one of the 'mach64', 'r128'
or 'radeon' sub-drivers depending on the hardware. These sub-drivers are

---

