---
title: "ALPS Touchpad and Warty Problem"
date: 2004-11-13
forum: Installation &amp; Upgrades
---

### Post by hunkybill on 2004-11-13
Hi,

I installed Warty 4.1 on my new Toshiba A70 notebook which has the ALPS Synaptic touchpad. Unfortunately, this touchpad does not work with XFree86. After reading all about it, it looks like I need a custom kernel with the ALPS patch?

Can anyone inform me as to the best approach to get the synaptics driver working with this patch. The driver code supplied is a few versions behind the latest, and to install the latest, it needs the X developer libs which are not in the repositories (main or universe).

I don't really want to rebuild X from source, nor do I want to build a custom kernel. Can someone inform me if I truly do need to go through all this hassle? When I look at the XFree logs, it tells me the synaptic module loaded, and the driver loaded too, but then it tells me it could not find a synaptic device, after checking 3 or 4 nodes. Hence the touchpad does not show up as a device... 

Any input most appreciated!!

---

### Post by daniels on 2004-11-13
[QUOTE=hunkybill]I installed Warty 4.1 on my new Toshiba A70 notebook which has the ALPS Synaptic touchpad. Unfortunately, this touchpad does not work with XFree86. After reading all about it, it looks like I need a custom kernel with the ALPS patch?[/QUOTE]Custom kernel, and custom xfree86-driver-synaptics, yes.

> Can anyone inform me as to the best approach to get the synaptics driver working with this patch. The driver code supplied is a few versions behind the latest, and to install the latest, it needs the X developer libs which are not in the repositories (main or universe).First, type 'apt-get build-dep xfree86-driver-synaptics', then 'apt-get source xfree86-driver-synaptics'.  That will give you an unpacked tree for the Synaptics driver at its current version that you can patch and rebuild.

> I don't really want to rebuild X from source, nor do I want to build a custom kernel. Can someone inform me if I truly do need to go through all this hassle? When I look at the XFree logs, it tells me the synaptic module loaded, and the driver loaded too, but then it tells me it could not find a synaptic device, after checking 3 or 4 nodes. Hence the touchpad does not show up as a device...Yeah, you can get away with just building the Synaptics driver (which is very small) separately.  I wanted to include support for ALPS and cPad touchpads in Warty, but didn't get to it until far too late in the release process, sadly.

---

### Post by hunkybill on 2004-11-14
Hi,

Thanks for the reply!

> First, type 'apt-get build-dep xfree86-driver-synaptics', then 'apt-get source xfree86-driver-synaptics'. That will give you an unpacked tree for the Synaptics driver at its current version that you can patch and rebuild.

This is great news, but now begs the question: From which repository? The first command completes with notice that the packages (libx11-dev for ex.) is not available, but referred to... and secondly, the get sources command seems to grab the driver already installed (ie) 0.13.3-1 while the latest version is 0.13.6...

Is there a repository I need to setup in the apt-get sources list that will setup a build of this latest version? 

If however the build tree created in the above quote is in fact the right one, the next step would be for me to simply run the make on the 0.13.6 code I have installed on my machine?

Thanks Again!!!

---

### Post by daniels on 2004-11-14
[QUOTE=hunkybill]This is great news, but now begs the question: From which repository? The first command completes with notice that the packages (libx11-dev for ex.) is not available, but referred to... and secondly, the get sources command seems to grab the driver already installed (ie) 0.13.3-1 while the latest version is 0.13.6...[/QUOTE]You may need universe for the development packages, but I dunno, they should be in main.  What's the exact error message?

> If however the build tree created in the above quote is in fact the right one, the next step would be for me to simply run the make on the 0.13.6 code I have installed on my machine?I don't know whether or not that has the X includes bundled, sorry, but it's worth a shot.

Cheers,
d

---

### Post by hunkybill on 2004-11-14
[QUOTE=daniels]You may need universe for the development packages, but I dunno, they should be in main.  What's the exact error message?

I don't know whether or not that has the X includes bundled, sorry, but it's worth a shot.

Cheers,
d[/QUOTE]

Thanks!

Well, long story short... I noticed the commands suggested above did in fact create a new directory for synaptics driver 0.13.3. I tried the make command in that directory to see what it would do. No go. No development tools. No gcc with Warty 4.10. So I did an apt-get install build-essential, and now had gcc installed and all the necessary build tools (or so I thought!!).

make blew out with a ton of errors. I guess it was wishful thinking to follow the threads of other like minded Ubuntu folks and try the maual approach. Maybe a missing tool is the problem, or some sort of missing link to libraries??? an Xinclude directory contains a ton of X11 code, but the errors seem to be about something else.

Might be possible for me to continue this, but I doubt it is worth the effort. I tried installing build tools from scratch using apt-get install autoconf for example, but that refused to work at all... seems the Warty universe contains nothing of the sort.... So, I am left puzzled. Might be easier just to build a Debian system from scratch at this rate!! 

Sigh...

---

