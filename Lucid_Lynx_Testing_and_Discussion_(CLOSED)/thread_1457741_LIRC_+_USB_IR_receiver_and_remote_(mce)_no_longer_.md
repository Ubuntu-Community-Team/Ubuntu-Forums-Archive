---
title: "LIRC + USB IR receiver and remote (mce) no longer working after upgrade!"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Lepy on 2010-04-19
I have a USB IR receiver/remote combo that I had working perfectly under 9.10 (mythbuntu), even though it did require some modification (see this thread for details: [http://forum.xbmc.org/showthread.php?t=66527](http://forum.xbmc.org/showthread.php?t=66527)).

I recently upgraded the computer using these devices to 10.04 and the original symptoms returned: namely that the first button press on the remote causes the usb receiver to light up and stay lit instead of flashing in time with any following button presses. 

Modifying the source lirc files (which had my remote working fine for months w/ directions from the thread above) results in the light staying lit up and no output through irw or any on-screen action. This happens when using the remote that came with the receiver or another mce remote.

lsusb gives this info:
ID 1784:0011 TopSeed Technology Corp.

Any ideas?

---

### Post by jbman on 2010-04-19
I have had no luck with the new kernel and my usb IR. I have a twinhan one, which works as a keyboard.

On 10.04 B2 I get it loading the modules ok, however when i press the remote nothing comes up on the screen.

I was wondering if it could be xorg or something else since its meant to be coming up as a keyboard.

I ordered a mce type usb IR hoping to get a remote working with my system. I am now worried I will have a simlar problem that you are having as well.

I started a thread about this last week with no response, so its good to know I am not the only one having IR issues with 10.04

---

### Post by Lepy on 2010-04-19
I won't rule out a kernel issue. The computer with the problem is an old laptop that won't boot with 2.6.32-21-generic without modified intel drivers, and even then still has crazy graphical issues. 2.6.31-21-generic is working much better...besides the IR issue.

I wouldn't worry too much about the new mce remote you have coming. It will probably work. Another system I have (with an mce remote and receiver that worked out of the box on 8.04 - 9.10) has had no troubles in the 10.04 upgrade process.

The remote I'm having issues with is mce but isn't referenced in the standard lirc package, hence I have to modify the source to get it working (in 9.10 at least).

I submitted a launchpad bug in hopes that this receiver can be fixed or included in the basic lirc package: [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/566422](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/566422)

---

### Post by Lepy on 2010-04-20
My problem has been remedied by building the latest lirc cvs.

---

