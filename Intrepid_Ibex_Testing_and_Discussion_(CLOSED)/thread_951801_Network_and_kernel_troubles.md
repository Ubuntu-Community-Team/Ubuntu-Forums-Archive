---
title: "Network and kernel troubles"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jblackhall on 2008-10-18
So up until a few days ago, Intrepid was running great on my desktop.  But somehow in the past few days, things have gone to hell and I'm not quite sure how.  I'm very careful about what updates I install so I make sure I don't remove packages not meant to be removed.  However, I still came across quite a few problems that others don't seem to be having.  I've filed some bugs, but I'd like to list my problems here.  Any suggestions would be extremely helpful.
[LIST=1]
[*]Boot hangs for about 60-100 seconds at ~40%.  After that, boot continues as normal.  This appears to be due to my network cards.
[*]Network Manager icon does not show up in Notification Area.  I believe it's running though.  My connections are wired and unmanaged.
[*]Only 1 of my network cards will work, despite the fact that both are detected.  If I unplug the cable from #1 and switch it to #2, I have no network.  If I re-plug into #1, no network on there either now.  If I boot with #2 plugged in, it doesn't work.
[*]My Internet connection (on the card that works) is connected as soon as I boot up, but after ~5 minutes, it no longer works.
[*]I am booting into 2.6.27-6 by default, even though I have 2.6.27-7 installed.  I have tried reinstalling all parts of the kernel and grub and running update-grub, but it doesn't help.  I can boot into -7 manually by pressing ESC at the GRUB menu.
[/LIST]

I'm very frustrated by all of this, and I can't seem to figure out how to fix it.  Any suggestions are welcome.

EDIT (update):  I'm making progress on this.  It looks like this is at least partially due to a bad Marvel ethernet port.  Disabling the bad port via BIOS allows 1, 3, and 4.  I fixed 5 on my own.  Still only having the NetworkManager bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/282835](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/282835)

---

