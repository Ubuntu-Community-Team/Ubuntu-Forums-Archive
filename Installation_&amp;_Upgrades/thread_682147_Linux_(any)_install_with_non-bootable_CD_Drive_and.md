---
title: "Linux (any) install with non-bootable CD Drive and Win 95"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by KayTi on 2008-01-29
Help! 

I'm trying to kill a Toshiba Portege 3020CT win95 install (I don't need the win95) - but I can't seem to access the bios to get it to boot from the PCM/CIA attached CD-ROM. This is one of those ultralight portables from about 8 years ago, ancient, I know. I ONLY need it to have ABIword and a working USB port to be my writing station, moving files off via USB drive. Working NETGEAR Wireless card would be lovely too, but that's on my nice-to-have list, not part o my musts. 

But this "can't boot from CD" is killing me. There's a floppy drive around here somewhere, but the computer can't access the internet so to put anything ON the floppy I first have to burn it to CD. I'm killing a lot of plastic trees with my CD use right now. 

I posted on the Hardware forum here, but I have a feeling I misunderstood the purpose of the HW forum, as it fell down to page 4 of posts with no replies today. :( Poor me. ;) 

Any help here? Copying my post to the HW forum below in case there's more useful details. 

Thanks in advance. Feel like an idiot. What else is new?

KayTi

==
Can anyone help me figure out a good linux install for a very ancient Toshiba Portege 3020CT running Win 95? 

My goal is to have a very small, lightweight computer that I can use to write. It doesn't *have* to connect to the internet, though it would be handy if it would via a NETGEAR Wireless card. If it doesn't connect, I need the USB port to work so I can move files off the laptop. Right now the USB port does not recognize my 2G flash drive, nor my crappy little 512M SanDisc one. I can completely kill the drive, I don't care about what's on it right now. I do *NOT* need dual-boot. Win95, ptouie! 

It's main problems are:
1) Very low RAM (96M) - I could possibly upgrade, but this is an old POS computer, I don't want to invest much. If it takes the type of RAM I have hanging around here, I think I have a 256M chip...somewhere.
2) I can't get it connected to the Internet via that NETGEAR wireless card. It needs drivers, the bane of my existence.
3) It uses an external CD drive connected via a PCM/CIA slot.
4) Because of 3) - it does not boot from the CD drive. It has an option to boot from floppy or HDD. Let's be honest - who has a floppy drive anymore? (to create a boot disk from some other computer seeing as how I can't get online with this one.)
5) I cannot find any way to alter boot settings. There is no boot.ini file at the root of C (though I created one as I explored some options.) It's Win 95, I feel like I'm trying to speak a foreign language, I've been on XP too long (ah yes, right THERE is the use case for going to linux if I ever heard one!)

I would like nothing more than to type Format C:\ but I fear that doing so will render the currently useful external CD drive useless. I can move files onto the machine through the CD drive, but which files? I've downloaded an ubuntu distro (from here ) - both the regular version and the alternate version. But all the directions for installing seem to require an ability to alter the boot menu. PLUS, I really don't give a ... whatever about the Win95 install, I'd rather wipe the whole drive and have the space for linux (it's about a 6G drive, for what it's worth.) 

I appreciate any help you folks can offer. I feel like I'm flexing muscles that haven't seen use in decades as I try to do this. 

Regards,
KayTi

---

### Post by hums07 on 2008-01-30
I also look for a similar way to install Ubuntu, i.e. unbootable yet accessible CD ROM drive and poor internet access. I have searched this forum and wiki but have no luck.

I think you need to invest buying PCMCIA ethernet card. It costs well below $20 at Amazon. Then if you have good internet access, you can try to install via UNetbootin, [here]("http://lubi.sourceforge.net/unetbootin.html").

BTW, 6 G drive is large enough to keep your Win95 untouched and has Ubuntu with fluxbox installed. Fluxbox is very good for machine with 96 MB and I doubt you will be able to run Xubuntu. Hopefully, you will be able to use your USB port (if it is still working), do your writing with Abiword and browsing the net with Epiphany.

---

### Post by hums07 on 2008-01-30
This fact may interest you:
"Some distributions, such as Fedora, CentOS, openSUSE, Slackware, Mandriva, and Arch Linux, allow you to use packages from your hard drive as the installation media" (quoted from Unetbootin web page).
And among those distros, Arch Linux is the light weight.

---

### Post by dgray_from_dc on 2008-01-30
Can it boot from a floppy?  If so, this might help [http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/)

I think it's a program that boots from a floppy, then allows you to boot from CD or any other detected drives.  I have something similar, but this is all I could find.

---

### Post by apaciq on 2008-01-30
Googled your particular laptlop on how to access the bios...
read the bottom portion...
hope it helps..
[http://www.driverforum.com/harddrive/295.html](http://www.driverforum.com/harddrive/295.html)

---

### Post by KayTi on 2008-01-30
Thanks! There's a bunch of ideas to try here. And yes, last night I did break down and dig out the floppy drive, which it is bootable to. I even made a win95 boot disk (knew I was keeping that cache of 3.5" floppies for some reason.)

The only issue is that to get things TO the floppy I have to burn them to CD from my other machine. I'm wasting a lot of CDs!

I'll let you know what I learn. Thanks again.

---

