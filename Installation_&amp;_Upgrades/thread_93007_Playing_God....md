---
title: "Playing God..."
date: 2005-11-21
forum: Installation &amp; Upgrades
---

### Post by guyomarj on 2005-11-21
On one side: an old, but still breathing Dell Latitude D233ST laptop ([here are the specs]("http://support.dell.com/support/edocs/systems/pmojav/specs.htm")). On the other side: Ubuntu 5.10 install CD.

Is there anything I can do to bring back this old folk to life?

---

### Post by aysiu on 2005-11-21
Those specs are too hard to weed through.
Bottom line: how much RAM does it have? How much hard drive space?

---

### Post by guyomarj on 2005-11-21
Sorry, I was a bit lazy. Here you are:

[LIST]
[*]Mobile Intel Pentium  II microprocessor 233 MHz
[*]4.3 G hard drive
[*]64-MB RAM
[/LIST]

---

### Post by briguy on 2005-11-21
The 64MB RAM will be an issue, it will run very slowly if at all.  If it's that or the dustbin, give it a go and let us know how it works out :) .

---

### Post by aysiu on 2005-11-21
Yes, 64 MB is going to hurt, but if you use XFCE4 instead of Gnome, it should be okay.

---

### Post by auburn on 2005-11-21
It looks like it's aproximately a 300mhz cpu with 64mb ram. But it might have upto 256mb of ram. It's a good machine in my opinion. But I dont' think I'd recommend running ubuntu on it. 

If anybody wants to disagree, please do...

I'd run win98 (if you must). or debian with xfce of fluxbox or some other non-kde, non-gnome desktop. It's simply not going to start firefox very quickly and I think openoffice will *really* suck on it. But debian has tons of lightweight apps to try...ie abiword, gnumeric, or xmms. For browsers, if not firefox, than maybe dillo? I think I would run firefox anyway.

A good starting point is to try the different desktops with a knoppix cd.

edit:
oh, 233. Well I run debian with fluxbox on a 200mhz box. It's impressive...but not modern.

---

### Post by aysiu on 2005-11-21
Ubuntu can run XFCE and Fluxbox, too.
If you want to run Ubuntu, you can--just use a lightweight desktop or window manager.

If you want something else, Damn Small Linux is built for modest specifications.

---

### Post by auburn on 2005-11-21
Aysiu, just because I dont know, why would you want to run ubuntu if not for it's gnome desktop? I'm under the impression that the essence of ubuntu is the highly optimized gnome.

---

### Post by aysiu on 2005-11-21
[QUOTE=auburn]Aysiu, just because I dont know, why would you want to run ubuntu if not for it's gnome desktop? I'm under the impression that the essence of ubuntu is the highly optimized gnome.[/QUOTE] The essence of Ubuntu is humanity towards others--it's Linux for human beings. It's not Gnome-specific (that's why we have Kubuntu, too). In fact, I use Ubuntu not because it's this phenomenal distro (I think Mepis is "better," actually--at least for me). I like Ubuntu because of its community--supportive, responsive, friendly.

If someone wants good support, she'd be better off using Ubuntu with XFCE4 than Damn Small Linux. That's just my opinion. Of course, Ubuntu with XFCE4 takes a bit more configuring at first than Damn Small Linux (which is designed for small RAM).

---

### Post by auburn on 2005-11-21
[QUOTE=aysiu] because of its community--supportive, responsive, friendly.
[/QUOTE]

Well, I agree with that... The community is the number one reason why I love ubuntu too. Thanks for telling me about damn small linux... And I see it's debian based too.

---

### Post by guyomarj on 2005-11-21
Thanks for your suggestions. I'll give a try to Ubuntu and XCFE. Then, if I have to, I'll switch to a distro like Damn Small Linux.

---

### Post by adam.tropics on 2005-11-21
Somewhere along the line it's really gonna come down to what you hope to use it for? If you can get that to specifics, then i reckon you'd have a better chance of success.

Out of curiosity though, how long since linux only actually required 64mb ram? presumably, there wouldn't really be anything wrong if you could find one, in installing a more 'generationally challenged' linux. If ubuntu is your preference then could an older version of debian be one approach?

My thought being that in times gone by linux was still pretty functional, so why not run a slightly dated version at full pelt, rather than trying to stretch the hardware into meltdown and still crawl ? !

---

### Post by guyomarj on 2005-11-21
[QUOTE=adam.tropics]
Out of curiosity though, how long since linux only actually required 64mb ram? presumably, there wouldn't really be anything wrong if you could find one, in installing a more 'generationally challenged' linux. If ubuntu is your preference then could an older version of debian be one approach?
[/QUOTE]

I agree with you. The fact is that Ubuntu is the distro that made me like Linux again. So I wanted to try this one first on the laptop. But I'm not narrow minded :) and if I have to, I'll try other distro. If you have any specific suggestion...

I don't know yet what I want to use it for. Maybe browse the Internet and check my mail in a café at first, edit some LateX documents and play FarCry with some friends.

I'll tell you what he is capable of :D

---

### Post by ygarl on 2005-11-21
Heck, most the time I run Windowmaker or FVVM anyways - and you don't get much more lightweight than that!

You could do the Server install, then manually install ICEWM, Windowmaker, FVVM, Fluxbox, Blackbox, etc... 
Those work pretty well!

Good luck!
I have Mandriva installed on a similar spec desktop machine (my next project is Ubuntu-ise the old one! Mwahahahah!)

---

### Post by nihilocrat on 2005-11-21
[QUOTE=aysiu]Yes, 64 MB is going to hurt, but if you use XFCE4 instead of Gnome, it should be okay.[/QUOTE]

Screw that, use blackbox/fluxbox. :p 

But seriously, it should be okay with XFCE4. The box will probably be slow, and you will want to 'optimize' it a bit by not installing too much glitz. As long as it has a CD-ROM drive, you are golden.

A few years ago I got a Pentium I 120mhz with about 48 meg of RAM (or around that) and a 500 meg (!) hard drive to run Debian woody smoothly with a blackbox desktop and just a few desktop apps. There wasn't really any space for media left over on the drive, though...

[QUOTE=guyomarj]play FarCry with some friends.[/QUOTE]

Uh... on that laptop? Everything else sounds kosher, but that's definitely not going to happen.

---

### Post by guyomarj on 2005-11-21
No FarCry??? Crap... anyone for Dopewar online ? :D

I'm currently installing XFCE. Server install went well.

---

### Post by dubz on 2005-11-21
64 MB is going to be fine.just dont overload thegraphics portion like everyone is saying.fluxbox is a good option.many livecd's use it.

If it were up to me i wouldnt even install a X Server.but thats just me.

---

### Post by Karlos on 2005-11-21
try VECTOR LINUX
it's a slackware based distro built especially for machines with less resources
[http://www.vectorlinux.com/]("http://www.vectorlinux.com/")
i've tried it
it's good ... as is all the slackware stuff ... and ubuntu!!

---

### Post by minor ubuntoid on 2005-11-21
Just to let you know, I've got a dell Latitude CP M233ST, which I think is pretty similar to your machine, and I have it running Debian with the twm window manager. Open Orifice and Firefocks are both happy but take about 8 minutes to start up. For this reason, I do most of my work without X, and am seldom out of emacs.

Good luck though!

---

### Post by guyomarj on 2005-11-28
It's alive, alive!!!!!!!!

Ubuntu server install + Fluxbox... nice and easy.

---

### Post by adam.tropics on 2005-11-28
So how's it running? I've not tried fluxbox, but have heard good things. Plus it looks like you could always increase the memory if need be. The spec says 128 or 256 max, so you have a little roomto move.

---

### Post by guyomarj on 2005-11-28
[QUOTE=adam.tropics]So how's it running? I've not tried fluxbox, but have heard good things. Plus it looks like you could always increase the memory if need be. The spec says 128 or 256 max, so you have a little roomto move.[/QUOTE]

It's running well. I've tried Blackbox, and Fluxbox is as fast and much more user friendly as far as I'm concerned.

What I have done:
[LIST]
[*]Ubuntu server Install
[*]apt-get x-windows-core
[*]apt-get xterm
[*]apt-get fluxbox
[*]Drop 'exec startfluxbox' in my .xsession
[/LIST]

Fluxbox is configured through files. You can install fbconf, a frontend fo Fluxbox configuration, if you don't want to mess with text files. The native Keygrabber is also very intuitive.

The packages I use ( from [Damn Small Linux]("http://www.damnsmalllinux.org/") and [this post]("http://ubuntuforums.org/showthread.php?t=42873&highlight=low+ram")):
[LIST]
[*]Browser: Dillo, Lynx and Firefox
[*]FileManager: EmelFM, mc
[*]Mail: Sylpheed
[*]Viewer: xpdf
[/LIST]

If you have other suggestions about light applications, tell me. I haven't find yet a Word Processor. I've heard about FLWriter from Damn Small Linux, but I didn't find it on Ubuntu repositories...

---

### Post by adam.tropics on 2005-11-28
Again, not tried it, but what about AbiWord?

GNU/Linux, BSD, Solaris (2.6, 7,8,9,10), AIX, HP/UX (10.20, 11.0), OSF/1, Tru64:

   >  * GTK+ 2.2 or newer (2.2.4 recommended)
    * At least 16MB RAM (embedded systems probably won't require more than 8)
    * Any processor that supports any of these operating systems (which is effectively, any processor)
[URL="http://www.abisource.com/download/"]
http://www.abisource.com/download/[/URL]

---

### Post by guyomarj on 2005-11-28
Yeah, but I want to avoid as possible any Gnome dependences. And it [seems]("http://ubuntuforums.org/showthread.php?p=219828&highlight=abiword#post219828") that Abiword need some Gnome libs.

---

### Post by rmestre on 2006-05-04
Just wanted to drop a note althou late. I have the exact same comp., I am running the latest distro of Ubuntu in its entirely. And it is amazingly fast, much much faster than the win 98 that came with it. And believe it or not the person I got it from was running xp on it!

Anyway it works flawlessly with full Ubuntu, except the onboard audio chipset is not supported, then again its not supported in any linux distro I tried.

If you got sound to work please let me know how...thanks! :)

---

