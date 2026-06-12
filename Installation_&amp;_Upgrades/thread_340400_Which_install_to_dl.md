---
title: "Which install to d/l"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by Tinkerbelle on 2007-01-17
I have finally had enough of Suse after 8 years partly due to their sellout to M$ and partly due to the nanny knows best attitude to upgrading via YAST or YOU](*,) 

Ubuntu has been recommended, despite my dislike of Gnome, and I want to install it and see if I like it, I expect I will switch to Kubuntu but I want to force myself to try Gnome again.

The problem I have is in deciding which d/l to grab, I have narrowed it fairly simply to one of the AMD 64 set. I have the desktop live cd for my partner to try on her winblows system but that does not run as live, grey screen even in safe graphics mode and thus no chance of instlling from it and I'm not sure if I need to bother with it for my Linux box.  

What is the alternate cd? There does not seem to be much descrition of what it is or why I would want it. Or perhaps I should grab the dvd image, it should at least have most of the packages that I want in one place but once again it is not fully described so I don't know.

tbh I'm not sure if (K)ubuntu is the right distro for me, it seems to be directed to new converts and maybe to 'safe' for me, I like to install most packages from source and I spend a lot of time in terminals as user and root, maybe rethinking my working methods will be good, maybe not.

---

### Post by Sef on 2007-01-17
> What is the alternate cd?

The alternate cd is a text based installer.  It will often work when the Live CD fails.  To read about installing using the alternate cd, read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").  If you aren't dual booting, just skip the FAT32 partition and XP info.

If you install Ubuntu and decide you don't like it, you can change over to Kubuntu with a few commands and pasting.

---

### Post by aberry5555 on 2007-01-17
If your wife's pc uses an ATI card then the reason it wont boot up in to live cd is the standard graphics drivers for ATI don't work properly, delete the splash and quiet entries from the boot and add break=bottom, then when you get a command line use nano to change the xorg.conf file, changing the driver from ATI to "radeon" (if thats the case) or "vesa".

---

### Post by Pobega on 2007-01-17
If her card isn't ATI it might just be a bad burn, I'd always give it 3~4 tries on minimum speed before worrying.

And if you feel comfortable with KDE over Gnome why don't you just burn Kubuntu? It's not like there is too much of an advantage to using Ubuntu over KDE, as far as I know (I may be wrong, though).

I've never seen any problems with the alternate install CD, so if you want to be sure that you will be able to boot into the install (Without LiveCD problems). Just make sure you remember that space is select, enter is continue, and tab is switch area in the installer; I messed up a Debian Sarge install two months ago because I didn't know that, and I really messed up my friend's computer.

---

### Post by Tinkerbelle on 2007-01-18
Many thanks for the tips guys, yes the win machine has an ati card so I'll try the ideas suggested just as soon as I can kick her off the box :D

I will persist for now with ubuntu as I do have some dislikes with KDE that seem to be better resolved in Gnome but I have never really persisted in running Gnome yet and I want to give it a fair trial. I will in any case need some dev libraries from both for some apps that I run.

I must admit I am a bit wary of using a windows based install cd to upgrade from Linux to Linux but I'll try it first on the winblows box, if I screw it it it doesnt matter, it needs to be reinstalled every 3 months anyway. :D

---

### Post by Pobega on 2007-01-18
> **Tinkerbelle said:**
> Many thanks for the tips guys, yes the win machine has an ati card so I'll try the ideas suggested just as soon as I can kick her off the box :D

I will persist for now with ubuntu as I do have some dislikes with KDE that seem to be better resolved in Gnome but I have never really persisted in running Gnome yet and I want to give it a fair trial. I will in any case need some dev libraries from both for some apps that I run.

I must admit I am a bit wary of using a windows based install cd to upgrade from Linux to Linux but I'll try it first on the winblows box, if I screw it it it doesnt matter, it needs to be reinstalled every 3 months anyway. :D

Well if you don't like KDE and are not sure about Gnome you can always try out Xubuntu; It's my personal favorite.

---

### Post by Tinkerbelle on 2007-01-18
Don't you just love Linux, there is always another alternative :D

Just throw another variable into the mix.

---

### Post by Tinkerbelle on 2007-01-19
> **aberry5555 said:**
> If your wife's pc uses an ATI card then the reason it wont boot up in to live cd is the standard graphics drivers for ATI don't work properly, delete the splash and quiet entries from the boot and add break=bottom, then when you get a command line use nano to change the xorg.conf file, changing the driver from ATI to "radeon" (if thats the case) or "vesa".

Nice idea - only nano will not run from this point in the boot as there are missing libraries, I forget which now but it doesnt matter I have given up with this POS. At the risk of starting a flame war I am going to get a real distro not some half assed windows based installer that doesnt even work as a live cd, there is no way I am even going to try it on my working Linux box.

There may well be a large and active community here, the distro certainly needs the help, but I am looking for a distro that just works which would then not need so much community support.

Thanks and goodbye.

---

### Post by tuxcantfly on 2007-01-26
> I am going to get a real distro not some half assed windows based installer

Ubuntu IS a "real" distro; the "half-assed windows based installer" you speak of is an unofficial third-party project. Just use the real installation method for now; the windows-based installer is an alpha-quality prototype that may have some issues, and is under heavy development at [http://www.ubuntuforums.org/showthread.php?t=338279](http://www.ubuntuforums.org/showthread.php?t=338279) If the live cd doesn't boot, try using an alternate installation cd.

---

### Post by Pobega on 2007-01-26
The Windows installer is neither created or supported by the Ubuntu development team. The best way to go about installing is to use a CD ISO image and boot from that, using the alternate CD.

Also, good luck finding a distro better than Ubuntu. Debian has a mailing list (Which is slow and I despise), Gentoo has forums (Most of the people there aren't overly friendly), and everything else has tiny communities; Nowhere else will you find a distro that works out of the box, has an awesome community, and huge repositories.

Unless of course you can get apt commands working in Windows, then by all means go back to your "real" operating system.

---

