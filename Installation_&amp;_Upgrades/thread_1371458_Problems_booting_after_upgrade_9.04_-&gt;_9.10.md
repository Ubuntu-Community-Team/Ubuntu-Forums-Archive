---
title: "Problems booting after upgrade 9.04 -&gt; 9.10"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by markowe on 2010-01-03
Hi, posted on more-or-less the same subject in "Beginners" but too much beginnery stuff going on in there to get a solution, hope someone can help a relative beginner here. I recently decided to resist the temptation to upgrade to Windows 7 (from the god-awful Vista) and to make a new and concerted effort to wean myself onto Ubuntu. However, after upgrading from my existing 9.04 to 9.10 (using update manager, not a fresh install) I have issues during boot, several long delays which take boot time to a good (or rather bad) 6 minutes. These seem to be the offending items, but it is all a bit over my head:

```
[    2.925915] a4tech 0003:09DA:0006.0003: input,hidraw2: USB HID v1.10 Mouse [A4Tech USB Optical Mouse] on usb-0000:00:1d.7-2.4/input0
[    3.001286] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f7aae40f47c]
[  182.573766] PM: Starting manual resume from disk
[  182.573771] PM: Resume from partition 8:6
[  182.573775] PM: Checking hibernation image.
[  182.573984] PM: Resume from disk failed.

```3 full minutes doing SOMETHING. Am I right in thinking it's taking an inordinate amount of time to attempt to resume (I am not trying to resume, even tried turning off hibernation as it doesn't work anyway)? not sure what to do about it in any case.

The other problem seems to be here:

```
196.908957] Registered led device: iwl-phy0::TX
[  196.934078] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  199.380227] ppdev: user-space parallel port driver
[  310.586109] CE: hpet increasing min_delta_ns to 15000 nsec
[  367.996993] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  368.026998] [fglrx] Maximum main memory to use for locked dma buffers: 1885 MBytes.

```Couple of minutes gone there too - ATI driver causing problems? Tried uninstalling and reinstalling that to no avail. Actually the problem here seems to be the appearance of a TTY login prompt during boot, which eventually goes away and the GUI appears, no idea where that came from.

Any help much appreciated, I DO so want to get away from Vista. Also don't really want to have to do a fresh install of Ubuntu as I had got things just the way I wanted.

Oh, here is a link to my bootchart, unfortunately I'm not up to deciphering it: [http://www.itsgottabered.com/media/mark-laptop-karmic-20100103-3.png]("mhttp://www.itsgottabered.com/media/mark-laptop-karmic-20100103-3.png")

Many thanks.

---

### Post by markowe on 2010-01-04
Egads, things way too busy here! Any help..? :(

Even if someone can just point me in the right direction - how do I go about debugging, or reconfiguring bootup, editing individual items etc? Maybe I can figure things out myself.

---

### Post by markowe on 2010-01-10
That's the good thing about forums, even when no-one replies, you end up solving the problem yourself! To recap, after upgrade to Karmic, my Toshiba Satellite Core2Duo was taking an age to boot (about 6 minutes), the splash screen was not appearing and it seemed to be getting stuck on attempts to resume (even though I had not previously hibernated - hibernation wasn't even working).

Well, problem solved - updated the kernel to linux-image-2.6.31-17-generic and all problems solved: regular boot now goes direct to splash screen like it's supposed to, takes 26 seconds to login screen (not 6 minutes!) and even hibernate/resume works properly now. What the heck that was all about I don't know, but I am happy. So always worth getting the latest kernel if you're having problems.

Over and out.

---

