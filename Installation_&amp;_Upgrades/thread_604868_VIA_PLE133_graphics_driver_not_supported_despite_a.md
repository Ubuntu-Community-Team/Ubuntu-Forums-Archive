---
title: "VIA PLE133 graphics driver not supported despite availability of driver source?"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by girto on 2007-11-06
I installed Ubuntu 7.10 (my first Ubuntu) and it recognized the graphics device as Trident Microsystems CyberBlade/i1, noting that VIA PLE 133 (VT8601A) drivers (source and binary) for Fedora core 1&2 and Red Hat 9.0 exist on the VIA website. The performance is noticeably slow.

Is it possible to compile/install the right VIA drivers? I can supply the links to the drivers if needed.

---

### Post by nickmcg on 2007-11-09
I looked at this problem some time ago, and was not able to get anywhere.
This probably just demonstrates the extent of my ignorance :)

Nick

---

### Post by nickmcg on 2007-11-11
First problem - the sources on viaarena are for xfree86, not xorg, so they won't compile

---

### Post by girto on 2007-11-14
> **nickmcg said:**
> First problem - the sources on viaarena are for xfree86, not xorg, so they won't compile

True! But since xorg is a fork of xfree86, can't the sources be modified one way or the other in order to make them compile?

---

### Post by mulder_edu on 2007-11-15
If you can get that to work, I'd like to see it happen myself.  The Trident Cyberblade drivers suck.  It's not just slow, DVD play back often doesn't work at all (at least for me), or it will play with streaks on the screen and green blurs.:mad:

---

### Post by girto on 2007-11-15
> **mulder_edu said:**
> If you can get that to work, I'd like to see it happen myself.  The Trident Cyberblade drivers suck.  It's not just slow, DVD play back often doesn't work at all (at least for me), or it will play with streaks on the screen and green blurs.:mad:

I wish someone with the xfree/xorg knowledge could guide me through the required changes. I am willing to do the hardwork myself once I understand what is to be done.

---

### Post by nickmcg on 2007-11-15
The solution could be as simple (!) as modifying the makefile, as that's what seems to be seting the paths to the include files.
From past experience, this is a nightmare (or yet another illustration of my lack of knowledge).

It might be worth getting the xfree86 sources and the xorg sources for one of the later graphics adaptors, and looking to see what the differences are - if I get a chance, I'll look at it, but I'm tight for time a the moment.

Nick

---

### Post by girto on 2007-11-15
I have located instructions to compile the Unichrome drivers (which do not work with the PLE133) with XOrg. They are remarkably similar to the instructions to compile the PLE133/Xfree86 drivers.

I tend to think that the makefile is generated automatically through imake and the IMakefile. I tried to follow the instructions, but I failed to locate the XOrg sources that include a config/imake directory.

Maybe you have some tips.

> Getting and installing the Unichrome driver.

1. Unpack the latest Xorg sources [example directory /usr/local/src/]. Will be referred to as XORG-TREE

$ cd XORG-TREE/xc/programs/Xserver/hw/xfree86/drivers/

2. Get the the unichrome driver via CVS:

$ cvs -z3 -d:Pserver:anonymous@cvs.sourceforge.net:/cvsroot/unichrome co xfree86

3. Remove the one supplied by Xorg, because it is probably outdated and link to the new one:

$ rm -rf via
$ ln -s xfree86 via

4. This is probably the difference with XFree - in building the Makefiles:

$ cd XORG-TREE/xc
# make Makefiles

If the above fails, I suggest you start building Xorg by issuing the command

# make World

It will start the building of the Makefiles instantly, but later on we would need also some dependencies from the Xorg build. The build takes quite some time, but we do not need to wait the whole time. Pause the build process after some time (Ctrl-Z or Ctrl-S) and in another terminal window try step 5. If it fails, resume the build process (% or Ctrl-Q) and wait some more time. I know that is a hack, but we rarely have the time for the whole build process o finish.

5. Compile the driver:

# cd XORG-TREE/xc/programs/Xserver/hw/xfree86/drivers/via
# make
# make install

---

### Post by nickmcg on 2007-11-16
I've downloaded the current trident driver sources ```
apt-get source xserver-xorg-video-trident
``` and the contents of the src directory are later versions of the via sources.
I would be very surprised if the older versions were faster than the newer ones.

Nick

---

### Post by girto on 2007-11-16
> **nickmcg said:**
> ```
apt-get source xserver-xorg-video-trident
```


Just for info: Does specifying source and a binary get the associated source package?

I am currently downloading the xorg cvs tree:
[http://www.neowin.net/forum/index.php?showtopic=204593]("http://www.neowin.net/forum/index.php?showtopic=204593")

Once done, I will follow the instructions above and see. Note however that i will be using the PLE133 driver source from via's website:

[http://www.viaarena.com/default.aspx?PageID=420&OSID=15&CatID=1810&SubCatID=108]("http://www.viaarena.com/default.aspx?PageID=420&OSID=15&CatID=1810&SubCatID=108")

---

### Post by nickmcg on 2007-11-16
I don't know about the apt-get source - I stumbled across it in another thread and it seems to work.

let me know if you get it to work (the newer driver doesn't need the full xorg tree to compile)

Good luck!

---

### Post by girto on 2007-11-16
Where you successful with the newer driver version? Any noticeable improvements?

Compilation of the via PLE133 driver failed unfortunately. Could be something trivial though. Expert advice is definitely needed.

---

### Post by nickmcg on 2007-11-17
The sources I'm looking at are the ones that produce the binary that's shipped, so there's no difference, although there seems to be some experimental code in there.

Nick

---

### Post by girto on 2007-11-17
After perusing the xorg driver sources, I found out that the via XFree86 driver has already been converted to xorg with the implication that the current drivers might be the fastest we may see in Linux :(

---

### Post by nickmcg on 2007-11-18
I think you're right.
I built the binaries from the source, but it made no difference :(

There's quite a bit of code in there that's effectively commented out, but I don't know what it would do.

---

### Post by ashtree on 2007-12-26
I know - it's the BUG!!!!!!!!!!!!!!!!!!
compile and install Trident drivers in this case is the wrong false way coz viaarena gives the k/ple133 driver which calls S3 Savage XFree86 X Server Version 1.00-15.
 And the second reason - now I cannot watch any video on ubuntu, coz it's ugly slow - only on ms-xp (which drivers for my GA-6VEML motherboard  integrated video calls xxs3xx.dll  too(!!!!). 
So I think its the fact -  that xorg autoconfigs to Trident Cyberblade / i1 on come VIA-GA motherboards for some bug.
and now  after some   hardly days-and-nights empty work 
I really need some instructions to make xorg driver from Xfree86 
(if it possible - for S3 Savage XFree86 X Server Version 1.00-15) 
or some new ubuntu K/PLE-133 Drivers!!!

---

### Post by ashtree on 2007-12-27
strange fact is 
after manual compiling and installation of latest opensourse savage  xorg drivers(xf86-video-savage-2.1.3) and many attempts to configure xorg.conf with 
dpkg-reconfigure xserver-xorg

I 've get the result with the old  same trident driver - but now i succesfully checked-up  " use kernel-mod framebuffer"

(before i try to do it - but  in the  result after startx i've  get sync error from the display)

may b success  reasoned by installation of VIA openchrome or some other  packages or libraries
i've installed to compile savage

but  now i'm happy- coz have an abylity to normally  watch dvd and divx  on 8mb 4xAGP via-integrated   trident under ubuntu.

hope it'll b helpfu 4 somebody else
and may b somebody explain the shortest way to make 8-mb 4xAGP VIA-integrated PLE133 faster enough to watch video

---

### Post by coreyfro on 2008-03-19
hey hey, trying to do the same, any pointers?

---

