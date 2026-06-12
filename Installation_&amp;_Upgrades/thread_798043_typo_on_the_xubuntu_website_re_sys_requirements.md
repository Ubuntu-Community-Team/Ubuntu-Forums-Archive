---
title: "typo on the xubuntu website re: sys requirements?"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by liquid boy on 2008-05-17
from the xubuntu website
> ...The Alternate Install CD only requires you to have 64 MB RAM...
..Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.

is that a typo? why would you be able to install it on a system with 64mb ram, but not be able to use it (minimun 192mb) that doesn't make sence.

i'm wanting to install xubuntu on an ibm netvista machine, with 
900mhz, 128mb ram

is that going to be possible (i'm assuming i'll need the alternate install)?

---

### Post by Sef on 2008-05-17
> ..The Alternate Install CD only requires you to have 64 MB RAM...
..Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.
is that a typo? why would you be able to install it on a system with 64mb ram, but not be able to use it (minimun 192mb) that doesn't make sence.

No it is not.  You can run xubuntu on systems with 64 mb ram.

> i'm wanting to install xubuntu on an ibm netvista machine, with
900mhz, 128mb ram

is that going to be possible (i'm assuming i'll need the alternate install)? 

Yes, it is possible to install with the alternate cd.  If you manually partitition it can be tricky if you have not done it before, but if you install it to the whole disk, it is easy.  And yes, xubuntu will run on 128 mb ram.

---

### Post by Thirtysixway on 2008-05-17
The alternate CD is different than running xubuntu.  The alternate cd uses a text installer, which requires a lot less ram.

---

### Post by Herman on 2008-05-17
I have read elsewhere that the 'Alternate' CD can perform an install in a computer with as little as 32 MB of RAM. I haven't tested it yet in a computer with such a small amount of RAM as that myself yet, but I believe that would probably be true.
It probably would be okay if all you need is a command line system, (with no desktop).

I have tested out the 'Alternate' CD in a computer with 64 MB of RAM and the installation worked fine. I installed a command line system and then added the IceWM desktop, which worked very well.
I added fluxbox desktop and that worked well too.
EDIT: Here is a link about that, [Windows98SE+Ubuntu Gutsy Gibbon]("http://users.bigpond.net.au/hermanzone/p2.htm")
Then I added the XFCE (Xubuntu) desktop, but that was pretty slow until I added more RAM.

The Xubuntu desktop is very nice, and Xubuntu is made to run faster in computers with less RAM, say in the range between 128 MB (or less), to 256 MB or more.

Gnome is slow in a computer with 256 MB of RAM, but I have installed Ubuntu lots of times in a computer with 128 MB of RAM and it works okay, but it is very slow. 

Some computers with 128 MB RAM work as well as others with 256 MB, maybe the size of the CPU cache makes a difference, or the bus speeds and so on. RAM is very important, but it's not everything. There are other factors to consider too.

You should shine a light inside your computer case and try to find out what motherboard you have, google it and get the motherboard manual for it. Read your motherboard manual and see if it is possible to install more RAM. If so, find out what kind you need and how much you can install. You may be able to get new memory module for it fomr somewhere.  Sometimes you can get one cheap from an old broken computer someone is throwing out if you ask freinds and relatives, if you're lucky enough to find one with the kind of RAM module you need.

It should be fine to install Xubuntu with the 'Alternate' CD in a PC with 128 MB of RAM, and it should work okay.

---

### Post by RedSquirrel on 2008-05-17
> **liquid boy said:**
> from the xubuntu website


is that a typo? why would you be able to install it on a system with 64mb ram, but not be able to use it (minimun 192mb) that doesn't make sence.

i'm wanting to install xubuntu on an ibm netvista machine, with 
900mhz, 128mb ram

is that going to be possible (i'm assuming i'll need the alternate install)?

If they say minimum 192 MB RAM and *strongly* recommend 256 MB, you may find Xubuntu runs too slowly for you. You could give it a try and see how it goes (installing with the alternate CD of course). If it's not fast enough and you can't upgrade the RAM, I would recommend a minimal installation. Some examples:

For Debian:
[http://ubuntuforums.org/showpost.php?p=4978783&postcount=2](http://ubuntuforums.org/showpost.php?p=4978783&postcount=2)

For Ubuntu:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by liquid boy on 2008-05-18
thanks for the answers. i have installed ubuntu a few times (all from alternate cds, as my computer only has 256mb ram)

i'm wondering why they say 192mb as the minimum, or am i reading it wrong?

---

### Post by NightwishFan on 2008-05-18
The live cd needs more ram than the installed system would use I believe.

---

### Post by Herman on 2008-05-18
> i have installed ubuntu a few times  (all from alternate cds, as my computer only has 256mb ram) Yes, me too.
I also use the Ubuntu 'Desktop' Live CD for installing with in computers with 256 MB of RAM. 
> The live cd needs more ram than the installed system would use I believe. I think so too.
Normally, the 'Desktop' Live CD will barely boot (if at all), in a computer with only 256 MB of RAM if there isn't a swap area already made on the hard disk, which is normally the case for new users first setting up a dual boot, who only have Windows.
One trick is to use GParted LiveCD, (which requires very little RAM), to make a swap area on the hard disk first, and then run the Ubuntu 'Desktop' LiveCD and perform the installation.
I installed Ubuntu Ultimate Edition in a friend's machine only a few nights ago in that way, and the machine has only 256 MB of RAM.

Another idea I have read about but have yet to try myself, is to use a USB flash memory stick formatted as a swap area to improve the performance of the Live CD until an installation can be performed. 

> i'm wondering why they say 192mb as the minimum, or am i reading it wrong?      I don't think there is any clear cut-off lines, where you can say something will work or not work. It seems to me it's more a matter of how much importance the user places on speed.
Even Gnome (Ubuntu) will run on 128 MB of RAM if you prefer to have all the applications that come bundled with it and you don't mind if it takes a long time for programs to open and for files to load. It still works, you just have to be willing to wait a bit longer every time you want to do anything. Gnome Partition Editor probably won't work, but almost everything else should work okay.

Xubuntu (XFCE) works better than Ubuntu (Gnome) or Kubuntu (KDE)  in older or moderately specced computers.
Fluxbuntu (fluxbox), or Icebuntu (IceWM) very fast in moderate PCs and will work in even lower specced machines.
(I'm not sure if there's actually such a version as 'Icebuntu', but there is a Fluxbuntu, I think).

And, as I mentioned eariler, a lot depends on other factors like CPU cache and things like that. Some machines have a video card that has it's own RAM too, whereas other machines use system RAM for everything.
Modern video cards might have 256 mb or 512 mb of ram or more - more than many people have in their whole computers just for the graphics! 
An older PC with a video card might have 16 or 32 MB of RAM in the video card, and that makes a difference in a PC with say 128 or 256 MB of system RAM.

So, I don't think whoever placed that figure at 192 MB really meant to imply that that was the exact cut-off point, but rather, a guide just to give people an idea of what might provide satisfactory  performance, give or take  a hundred MB or so.

---

### Post by ugm6hr on 2008-05-18
> ...The Alternate Install CD only requires you to have 64 MB RAM...
..Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM. 

I can't remember exactly where those quotes are - but they are 2 separate (and different) statements.

The first relates to Xubuntu AlternateCD - which will work with 64MB RAM (albeit slowly).

The second relates to *running* (with 192MB) or installing (with 256MB) with the Live/DesktopCD.

So - it is not a typo.

Getting back to your issue - 192MB RAM will run Xubuntu, although don't expect blazing speed.  I used it on a 128MB machine, and find it usable, but not great.  Think similar speed to XP.

There are lighter options out there - but most preconfigured versions are still Gutsy-based (rather than Hardy 8.04).

---

### Post by NightwishFan on 2008-05-18
Try debian for a fast system.

---

### Post by liquid boy on 2008-05-18
sweet, thanks. that clears it up heaps.

---

