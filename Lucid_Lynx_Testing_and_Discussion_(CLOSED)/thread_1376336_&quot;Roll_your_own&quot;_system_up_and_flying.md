---
title: "&quot;Roll your own&quot; system up and flying"
date: 2010-01-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ibidem on 2010-01-09
Hello,
I've done a netboot install of Lucid on my AA1, and love it.
Manual partitioning, manual package selection.
No glitches, but update-grub took a bit longer than it "should" (a few minutes)--nothing new.
I prefer IceWM/PCManFM, so what I selected was more or less
IceWM, xserver-xorg-core (yes, that is being particularly minimalist), roxterm, pcmanfm, alsamixergui (FLTK version of alsamixer, instant startup), leafpad, GIMP, Xsane, Scite, WordGrinder, wicd, pppconfig, wvdial (redundancy, I know... And I don't even have a modem yet!), UCK, wmbattery, guvcview, xpdf, gtkam. Later I added xarchiver (pulls in p7zip, rpm, etc.), xinit (never forget that!) and Firefox (no ubufox).
It works alright, runs *fast* (boot time appears to be around 10 seconds or less), and I can start X in <5 seconds.  Shutdown is ~1 second (sudo halt, password, off).
Good night,
Ibidem

UPDATE:  Sound (realtek "ALC268") is not working

---

### Post by nanog on 2010-01-09
> xserver-xorg-core

xorg is a mess. do we really need to install xserver-xorg-video-cirrus, sis, sisusb, trident, tseng, s3, s3virge, savage, silicon-motion by default on *every* system. and don't get me started on the monolithic kernel that contains every freaking driver ever invented.

---

### Post by Ibidem on 2010-01-09
NO!!...
or should I say, YES!!!
Installing them initially, I guess, makes sense (until you add a hundred (+) lines of logic to your installer)--detection may not work right all the time, different drivers may be useful, etc. -- and what about remastering, moving the HDD to another system, and so on?
I do know of someone with an SiS card--and Linux isn't playing nice with it yet.
For the inveterate tweaker, at least you can remove them or block them.
 I just uninstalled xserver-xorg-video-all as well as almost all the drivers (including ATI, nv, Matrox, and other "common" cards) --kept v4l, intel (using i915 for a 945 now), i740 just because, vesa, fbdev, & vmware (if I do a bit of playing).  That freed about six and a half megs and removed near 20 packages. I don't think 7 megs on hard drive is that bad.
I wonder, though,--does Gentoo make you install the extra drivers?  I know that it can handle only installing parts of libraries.
What that selection (xserver-xorg-core) means is I did not install the other 10+ MB of packages that xorg requires.
There was one problem: I needed xinit.

On the note of "bloat", ubufox is huge (requires all the desktop package management stuff).  It kicks the size of Firefox (installed) to 100 MB, from 20.6 MB.
The Gimp is a 13 MB download.

I had HAL on here, for pcmanfm, but it did not automount as it should.
So now I have usbmount + pcmanfm-nohal
It's interesting that GNOME users now get the same "problem" that I used to have with IceWM.
And Canonical had better ship usbmount by default!

Ibidem

---

### Post by VMC on 2010-01-09
> **nanog said:**
> xorg is a mess. do we really need to install xserver-xorg-video-cirrus, sis, sisusb, trident, tseng, s3, s3virge, savage, silicon-motion by default on *every* system. and don't get me started on the monolithic kernel that contains every freaking driver ever invented.
This has been bugging me for a while now. I wish there were a way to install only drivers on your system and not every driver available. Pinning is just not possible. I have intel video and I will never need the umpteen other drivers. Its a waste of disk space and download time.

---

### Post by Ibidem on 2010-01-11
Sound is now working; it was the standard "mute on boot" issue.
Pulseaudio helped me get it working, but would not recognize mpg123 as an audio player(??).
So I installed audacious.
That means that Lucid Lynx is "fully" working--for the moment.

I've also installed Xiphos (nice as usual), scrot (quick screenshots), and am in the process of downloading OpenOffice.org 3.2.0 RC1.
*If* anyone wants to see any screenshots, ask.

Ibidem

---

### Post by vishalrao on 2010-01-11
good work... ubuntu should support/document more this "roll your own from scratch" model for those who want "net install" or highly customised installations.. i actually went to arch to install a base system to checkout and build kde4.4 from source... couldnt figure out netboot/netinstall with ubuntu myself

---

### Post by xebian on 2010-01-11
> **vishalrao said:**
> good work... ubuntu should support/document more this "roll your own from scratch" model for those who want "net install" or highly customised installations.. i actually went to arch to install a base system to checkout and build kde4.4 from source... couldnt figure out netboot/netinstall with ubuntu myself

If you 'can' roll your own there is no need for 'support/document'.  Netboot install is nothing but alternative install but only a cli install.  It makes no sense that you can build kde from source but could not simply make a few prompted choices in the netboot installation IMHO.

---

### Post by vishalrao on 2010-01-11
oh i see, just a few prompts? then i think i must have screwed up somewhere - probably downloaded the wrong image thinking its the netboot. i will definitely revisit a "net install" attempt later on...

---

### Post by slakkie on 2010-01-11
> **xebian said:**
> If you 'can' roll your own there is no need for 'support/document'.  Netboot install is nothing but alternative install but only a cli install.  It makes no sense that you can build kde from source but could not simply make a few prompted choices in the netboot installation IMHO.

By netboot install you mean the minimal install CD? If so, it is not a cli only install. You can setup your PC as you like (desktop/server/etc) but retreive the packages from the online repo's and not from the CD..

---

### Post by xebian on 2010-01-11
> **vishalrao said:**
> oh i see, just a few prompts? then i think i must have screwed up somewhere - probably downloaded the wrong image thinking its the netboot. i will definitely revisit a "net install" attempt later on...

You should get the mini.iso from the netboot folder in cdimages.ubuntu.com ~~ 12 MB

---

### Post by xebian on 2010-01-11
> **slakkie said:**
> By netbook install you mean the minimal install CD? If so, it is not a cli only install. You can setup your PC as you like (desktop/server/etc) but retreive the packages from the online repo's and not from the CD..

The latest incarnation has that option added where you can select desktop flavors.  But why bother when you can just as well use the regular iso.  You get to this because you want a cli install where you can customize your setup at your own pace/choosing.

---

### Post by xebian on 2010-01-11
> **slakkie said:**
> By netbook install you mean the minimal install CD? If so, it is not a cli only install. You can setup your PC as you like (desktop/server/etc) but retreive the packages from the online repo's and not from the CD..

BTW pls be careful.  netboot != netbook. I know what you meant but others may be confused.

---

### Post by slakkie on 2010-01-11
> **xebian said:**
> The latest incarnation has that option added where you can select desktop flavors.  But why bother when you can just as well use the regular iso.  You get to this because you want a cli install where you can customize your setup at your own pace/choosing.

I only use minimal install CD's. The reason is simple: no need to upgrade after installation because if fetches all the packages from -updates/-security when installing. So you are fully up to date. And the regular CD (liveCD) doesn't allow me to choose packages to install as I please. The alternate CD does too, but I like the minimal CD. It is small and does the job fine.

PS. I've editted the post, so it actually says netboot :)

---

### Post by Ibidem on 2010-01-11
A network install is not a complex process, if you have done a few installs before.
You are well advised to bone up on Aptitude beforehand.
1. Boot mini.iso
OR
boot the netboot kernel & ramdisk
(after extracting in hdx,y root partition reboot;
press c at GRUB prompt
enter these lines:
root (hdx,y)
kernel /linux
initrd /initrd.gz
boot)
2.  Make sure to have ethernet plugged in; wifi does not presently work in this method.
3.  If you speak English, select the locale "C-no localization".
Although it does not allow using another language, it speeds the install up (localization packages are huge).
4. Proceed as indicated by the installer; defaults should usually work, EXCEPT:
you are advised to PARTITION MANUALLY if you are installing multiboot.
5.  When it prompts to select packages to install, remember: Space selects, Enter continues.
If you just press enter here, you'd better have ethernet or a thorough acquaintance with ifconfig.
Default is no packages
I selected to "manually install packages'; multiple options may be selected
6.  If you have selected manually install packages, you will be dumped into Aptitude.
Aptitude is a very powerful, but NOT completely familiar, package manager; here are enough keys to get you started: 
<Control>+T drops down the menu, + selects a package, - unselects, / or \ should be used to search forwards or backwards; Enter will expand or collapse a section, or open a tab with more information; q quits the current tab, exiting if there is only one (it will skip installation); you should finish by pressing "g" (GO), which applies all changes.  The nice thing is that you can review the packages after you press g once; however, you will need to press "g" again to finish.

Make sure to select xorg or xinit & xorg-server-core, as well as your favorite window manger, file manager, terminal, and networking programs (wicd, wifi-radar for wireless; wvdial or pppconfig for dialup), and DO NOT forget "usbmount" if you want automounting; you may also want stuff like the GIMP, a display manager, Firefox, Openoffice.org, Abiword, Gnumeric, Audacious, PulseAudio...
 7. Having selected, reviewed, and installed the packages, quit Aptitude.
Now you reboot.
Unless you installed a display manager or a "*-desktop" metapackage, you will see this prompt:
login:
Login as normal, and run "startx" to enter the GUI.  DO NOT try "sudo startx", as it WILL royally screw up your system.
Hope this helps,
Ibidem

---

### Post by vishalrao on 2010-01-11
ah i get the general idea. i think i will try this once things get a little stable(r) around the alpha 2 release timeframe...

---

### Post by nanog on 2010-01-11
i don't know why we'd want to document this. doing this without a good knowledge of debian gnu-linux and dpkg-apt is asking for trouble. for those who want to have a more minimal install its trivial to install using the file server image -- just replace the kernel with the desktop kernel falvor and add whatever gui (meta)packages you want.

---

### Post by Ibidem on 2010-01-12
> **nanog said:**
> i don't know why we'd want to document this. doing this without a good knowledge of debian gnu-linux and dpkg-apt is asking for trouble. for those who want to have a more minimal install its trivial to install using the file server image -- just replace the kernel with the desktop kernel falvor and add whatever gui (meta)packages you want.

Why netboot?
It is necessary for some installs.  If you didn't notice, I stated that I could not use any standard ISO on my netbook.  It also simplifies life for those, like me, who don't want to install GNOME, Nautilus, Evolution, Mono, KDE, XFCE, Thunar, and so forth. Also, it uses less bandwidth and fewer CDs than downloading an ISO, burning to disk, installing, and then updating.  Additionally, it is much better for installing to large numbers of systems.

Why document netboot?
People will find out that it exists.  If we try to pretend that not documenting it will result in the masses not knowing about it, someone *will* find out that it exists, and then try it and screw up (press enter at package selection, try off network, or whatever).  
Then there are the people who want to do this sort of thing, and assume that they need Arch Linux, or find the (relatively well documented) Fedora installer and assume they can't do it in Ubuntu, thus switching distros because of a misunderstanding.
Don't assume that Arch Linux is always better than Ubuntu for this.  You can't just select what you want when installing, and there are other reasons to select Ubuntu--less manual work, (nominal) support for pre-686 CPUs, etc.
If we document it *properly*, indicating the dangerous points, it results in those who find out about it being more aware of these, and thus being less likely to screw up.

Why document the "roll-your-own" stuff?
1. Refer to the above
2. There are situations where this is needed:
Have you seen GNOME running in 64 megs of RAM, on a 500 MHz CPU?
I have used it.  And I would much rather do the above procedure (2-4 hours estimated) than install Ubuntu-desktop, endure the three-minute boot, run Synaptic to install the desired software (a process that seemed to take forever), logout, switch WMs, and so on.


Not meaning to be argumentative or verbose, but I hope you understand the motivation from this.
Ibidem

---

### Post by nanog on 2010-01-12
the problem is that this kind of minimal install requires a working knowledge of what packages comprise a working x-term and/or x-windows environment. imo, this is a rtfm kind of install. 

"and assume that they need Arch Linux"
actually i've never used arch. minimal installs and roll your own (e.g. kernel and xfree86) are old-school debian and redhat.

---

### Post by Ibidem on 2010-02-15
Well, I've got a 23.76 second boot per bootchart (not great for Lucid--using hard drive, no SSD, AA1; ~12 partitions).
I'm using currently using nodm to autologin; when I update X, I'll disable it at first try.
Keeping back 2.6.32-13 and the latest xorg (seem to be making trouble for others).
I've gotten hibernate and suspend working (pm-hibernate & pm-suspend) and added claws-gtk.
Kicked out a few other programs; I had to add libstdc++5 from Jaunty for the icewm control  center, as well as gvim.
Abiword 2.8 is good news, but so is OO3.2 (final, upstream en_us). 

@nanog: I guess it is rtfm; it also has been (semi-)documented a few places, and users have already installed without X by accident--is that overexposure or underdocumentation?  I guess that's the point we can't agree on.

---

