---
title: "[SOLVED] Can't create a working Boot disc"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by TheKramer on 2008-11-25
So, I've always used Windows (or DOS back in the day), and I finally decided to try out Ubuntu, only I can't.

I'm moderately computer savvy (build my own computers... although this isn't one of my builds I'm installing on, do a little computer programming, etc.), but I'm just having no luck here.  Here are the things I've tried.

1) I've tried both versions (8.10 and 8.04).
2) I've tried multiple download sites (all U.S. and relatively close to me).
3) I've downloaded using multiple browsers to download (IE, Firefox, and Chrome).
4) I've downloaded onto 2 different computers (a desktop and a laptop, both pretty new).
5) I've burned the CDs using two different drives.
6) I've used 3 different burning software packages.
7) I'm using checksum and they check out fine.
8) I've burned using multiple speeds (including the slowest available on each drive/software combo which happened to be 10x and 12x, I believe).

So far only of the many CDs I've created actually worked (the rest just tried to boot and had an error or just loaded back into Windows without booting).

The one that booted showed an error when I ran the check on it.  I tried to install off it anyway, but it failed on the partition step (may have been my fault, I didn't have a mouse hooked up, and I think I miss hit a key).  Next time I tried to boot, it booted, but when I hit install there were some graphical glitches and then it eventually blackscreened and froze.  When I hit some keys, the drive seemed to start spinning again, but it stayed blackscreened.

I'm really frustrated and have no idea what to do from here.

The only thing I could think of was a faulty CD drive.  I'm currently installing a game, and it seems to be installing fine (and I've had no indications that there is anything wrong with the CD drive).

Any thoughts or suggestions?

I'm about ready to give up and just go back to Windows and forget Ubuntu ever existed after all of this hassle.

---

### Post by TheKramer on 2008-11-25
Just a quick update.

I managed to completely a game off of a CD and play it (I only played for maybe 5 minutes) to see if the CD drive seemed to still be working.  No problems at all.

Using the one boot disc that actually partially worked, I've now made it through all of the preliminary steps, and I'm actually 5% into the system install.

I'm still worried, though, as the built in boot disc check (that you can select after it boots up) found 1 error.

If this actually installs, am I home free?  Or is that "1 error" likely going to haunt me?

Oh, and by the way, it is 8.10 that I'm currently installing.

Thanks in advance!

---

### Post by Partyboi2 on 2008-11-25
Have you tried installing using the[[COLOR=Blue] alternate[/COLOR]]("http://releases.ubuntu.com/intrepid/") cd? If you think there is a problem with your cdrom then you could try using [[COLOR=Blue]unetbootin[/COLOR]]("http://lubi.sourceforge.net/unetbootin.html") which does not require the use of a cdrom.


Edit: If you are getting errors when you use the check cd for defects option and your md5sums match then try burning at x4 or less

---

### Post by TheKramer on 2008-11-25
Thanks for the advice.

My current install just came up with this error (at 27% into the install):

[Errno 5] Input/output error

It says it may be due to a faulty CD/DVD disk or drive.


None of my software packages seem to give an option to burn at only 4x speed, but I'll look again.

Thanks for the links to the alternate cd and unetbootin.  I don't know much about them, but I'll take a look right now.

---

### Post by TheKramer on 2008-11-25
This is a family member's computer, so I didn't know all of the specs.  I checked and it has 256mb of RAM.  That meets the minimum requirements for 8.1, but would I be better off installing 8.04 for them?

I ask because the alternate cd link seems to be saying 256mb might be right on the border for usability.

---

### Post by TheKramer on 2008-11-25
Well, it ended up putting me into Ubuntu (even with a partial install), but the system is slow and most things won't open.

I don't think I have any more time to mess with this tonight, but I'll post updates tomorrow when I get a chance to take another crack at this.

---

### Post by TheKramer on 2008-11-25
Ok, I haven't gone to sleep yet.  :P

I'm wondering if this system is too old to even run Ubuntu.

Here are the basic specs:
CPU: AMD Athlon XP 1700+ running at 1466mhz
RAM: 256MB
Video: ATI Radeon 8500LE with 64MB of video RAM
HDD: 60GB

It was running Windows 98 ok.

Can I manage to install and run Ubuntu 8.10 on this system?  Or should I install an older version?  Or should I install Kubuntu?

Any thoughts would be appreciated.  I did look at the minimum requirements, but it seems like I'm ok with the CPU and video card, but maybe a little short on RAM.  I'll try scrounging around my old parts for some extra RAM tomorrow, though.

---

### Post by awam66 on 2008-11-25
Hi
I have found on a friend's laptop that 256Mb is really not enough. The best option would be to add more memory. This would make a huge difference to the speed. You could also try "Fluxbuntu" which is a cut down version but works quite well on low memory systems.

---

### Post by Partyboi2 on 2008-11-25
> **TheKramer said:**
> Ok, I haven't gone to sleep yet.  :P

I'm wondering if this system is too old to even run Ubuntu.

Here are the basic specs:
CPU: AMD Athlon XP 1700+ running at 1466mhz
RAM: 256MB
Video: ATI Radeon 8500LE with 64MB of video RAM
HDD: 60GB

It was running Windows 98 ok.

Can I manage to install and run Ubuntu 8.10 on this system?  Or should I install an older version?  Or should I install Kubuntu?

Any thoughts would be appreciated.  I did look at the minimum requirements, but it seems like I'm ok with the CPU and video card, but maybe a little short on RAM.  I'll try scrounging around my old parts for some extra RAM tomorrow, though.
Try installing [[COLOR=Blue]xubuntu[/COLOR]]("http://www.xubuntu.org/")

---

### Post by TheKramer on 2008-11-25
Thanks again, guys!

I'm going to either dig up some RAM and try Ubuntu again, or I'll try Xubuntu.  

I'm marking this thread solved, and if I have new problems as I progress, I'll start a new, more specific thread.  

Thanks again!

---

