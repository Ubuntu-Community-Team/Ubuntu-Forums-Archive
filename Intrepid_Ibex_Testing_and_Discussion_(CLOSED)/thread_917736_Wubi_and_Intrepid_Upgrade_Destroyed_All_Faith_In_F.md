---
title: "Wubi and Intrepid Upgrade Destroyed All Faith In Future of Ubuntu"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by morganevans on 2008-09-12
Hi guys,

I hate moaning, but out of all the years I've been using Ubuntu (since 6.04 I think)  I've never been so dissapointed in an update as with Intrepid Ibex.  Certainly, I'm not a dedicated Linux user, although I have been a programmer since 1983 and have used various OSes in my time.

On my latest visit to Linux, I found I'd done something daft and created four physical partitions on my laptop HD so went for the Wubi approach and installed Hoary fine.

After the usual routine of extracting the Broadcom wireless firmware and installing ATI video drivers, my love for Linux bloomed and I read somewhere than Intrepid Ibex was to be released in October 2008.

Knowing that Ibex was at Alpha 5 stage, I knew I was taking a risk but, in believing that the product was to be ready for distribution within less than two months, a worthwhile one.  How wrong could I have been.

The long (about 2 hours including downloads) update resulted in a lock-up before the laptop could restart and on selecting the new 'experimental' kernel was told that NTFS hadn't shut down properly and that I must run check disk.

I ran check disk and after retuning to the computer, I felt the windows startup procedure seemed to be a lot quicker than when I usually ran with checkdisk.

Rebooting into Windows again, I noticed the checkdisk screen appear again, but flashed up 'cannot access disk directly' (or something along those lines) which was causing cheskdisk to abort.  My instincts proved (at least it appeared) to be true as Linux once again failed to boot using the new kernel.

After much searching I found I could create a recovery disk set for XP which proved to be worthless, so I made a last resort push for Norton Systemworks Basic at $50 to see if I could make a work-around.  Unfortunately, the download server was down so I had to resort to another half hour+ worth of searching and eventually found I could install the XP recovery console directly.

Checkdisk did indeed run and apparently found and fixed a problem with the drive.  Unfortunately, linux still failed to boot and that's when I decided to try an older kernel and bingo, there was actually no problem.

Anyway, that part of the moan over.  I then found out that Xorg 7.4 doesn't support fglrx through DRI, which I didn't mind too much as I thought I could live with the open source ATI drivers.  Unfortunately, Xorg was running like a dog taking around 50% processor usage which only seemed to be worse the when I updated today.  Linux now takes around 7 minutes from GRUB to idle Gnome desktop with a CPU usage hovering around 100%.

The best bit though is that the hardware drivers install utility still allows me to install fglrx which Xorg promptly spits at on reboot.

Oh, and my xorg.conf configuration disappeared, to be replaced by the default.  I re-added the necessary wacom pen-tablet sections and Synaptic touchpad sections to find that the pen-tablet wouldn't 'left-click' on anything and the synaptic touch-click was sporadic at best.

I don't know if sound still worked because I had to wait for about 15 seconds just to get gnome-terminal to start to edit xorg.conf and wasn't prepared to wait for more complex applications.

Surely this isn't an indication of an OS that's merely weeks away from release?  I can cope with these sorts of problems with early Alpha releases (hell, even early Alpha releases of previous versions of Ubuntu were a lot more stable than this)

Thanks to Ubuntu I will not be using Ibex, nor Linux for another year and now have a piece of paid software I'll probably never use.

The thing is, I know Linux is a good OS but it just shows how poorly the OS is supported in practically every aspect and I'm sorry, but there's just too little structure and not enough focus and too much duplication of effort for the OS to ever throw the shackles off and become a serious desktop alternative to Windows or OS X.

I know I'll get flamed for it, but it's the same way I've felt about Linux for years and I'll never change that opinion until someone takes more than just the base OS and a couple of server applications seriously.

---

### Post by badactress on 2008-09-12
"Knowing that Ibex was at Alpha 5 stage, I knew I was taking a risk"

Whether it's Alpha 2 or Alpha 62 it's still Alpha! You have to expect it to destroy your hard drive, kill your lawn & run over your neighbours dog.. then if it doesn't that's a bonus :)

You can't criticise alpha releases for not working. When it's released and it still has those problems then you can shout and scream and demand your money ba.. oh.. wait.. they gave it to you completely free didn't they!? B*stards!! :p

I assume you've reported all these problems so the development team are aware and can attempt to fix them before release date? 
:)

---

### Post by DrMelon on 2008-09-13
You did read the terms and agreements, didn't you?

It's an alpha. It's not stable. It's not even in Beta yet.

You can't blame anyone but yourself. You took it in your own risk, as clearly described in the EULA.

---

### Post by ago on 2008-09-13
Alphas are good, just remember to report the bugs ;)

[https://bugs.edge.launchpad.net/wubi/+bug/268123](https://bugs.edge.launchpad.net/wubi/+bug/268123)

---

### Post by allquixotic on 2008-09-13
Most of the troubles you described (the high CPU usage, slowness of X, and fglrx not working) are totally out of the hands of Canonical. X.Org development has taken a turn for the worse of late, with political boundaries between corporate stakeholders severely impeding development. The few aspects of X.Org 7.4 which are genuine improvements across the board are immediately negated by its weaknesses. It is the worst X.Org release in history, if you ask me.

First of all, fglrx and DRI are completely and utterly disjoint. They have nothing to do with one another. One does not use or interact with or operate at the same time as the other.

Roughly speaking, fglrx and DRI are incompatible attempts to solve the same problem (provide a hardware-accelerated OpenGL library implementation), with differences along these lines:

1. License. fglrx is closed source and you operate under a EULA from AMD when you run it. The onus is **completely** on AMD to keep up with open source development by making their driver work with new releases of Xorg and the kernel; by failing to do this in a timely fashion, Intrepid Ibex will very likely be released without fglrx support. This isn't a knock on Linux; complain to AMD if this software is important to you. This is exactly the same situation as it would be if Skype released their new Windows version, with tons of new features, but left Linux users in the dust for months. If AMD truly wished to please its customers and keep current, they would do as NVIDIA has done successfully, and dedicate enough developers to the fglrx project so that they can closely follow X.Org 7.4 development, and have a driver ready that's compatible with it **on the same day it's released**. NVIDIA can do it; if AMD can't and you don't like that, consider switching graphics card vendors.

2. DRI is an open source project that provides hardware-acceleted 3d graphics (via the OpenGL API) for **tons** of different graphics cards. From Intel to AMD to Nvidia to SiS to Matrox to antiquated 3dfx cards, DRI has a much more difficult and ambitious design goal than fglrx: to tie together vendor hardware, which differs very dramatically under the hood, in increasingly general levels of software wrappers that correctly abstract the basic concepts, thus preventing developers from writing a complete top-to-bottom solution for every new graphics chip that comes down the pipe.

The difficulty in DRI development of late has been in a political war between, for example, the TTM memory manager from Tungsten and the GEM memory manager from Intel. One way to describe this dichotomy is "TTM works for everybody, but puts the system through so many hoops that it's also very slow for everybody." "GEM works quite well for Intel and other integrated graphics, but falls down with discrete graphics and advanced features like anti-aliasing and texture from pixmap." The result is, sadly, thousands of development hours toward DRI have been wasted by Intel and Tungsten trying to conceptualize a memory manager that will work; meanwhile, the only usable DRI memory manager that distributions are brave enough to package is the old-fashioned memory manager that uses the AGP aperture. Both sides recognize the flaws and difficulties with this old design, but currently, it's the only thing that "just bloody works".


I share many of your frustrations about the state of X.Org today, but you should by no means aim at Canonical about these issues. They are faced with a rather bleak position of either (a) being criticized for being outdated and inflexible by sticking with X.Org 7.3 [just so fglrx will continue to work], or (b) going with X.Org 7.4, which breaks a lot of things for a lot of people.

Until there emerges a clear victor in the "memory manager cold war" (as I like to call it), the whole X.Org and DRI stack will both be unstable, lacking of features, working on a lower variety of hardware, and slow. Unfortunately, the memory manager is such a low-level piece of DRI that it also heavily impacts the way developers write their 2d DDX, which accelerates 2d operations; that means you must continue to suffer slow 2d performance as well as slow 3d performance until this blows over.

Sorry I don't have any solutions for you, but reporting bugs against Ubuntu will do *very* little towards solving this major political schism in the graphics stack.

Sean

---

