---
title: "Raid"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by eportuguesas on 2012-12-26
Hi. I'm a noob in ubuntu.

I try to install linux in my pc with raid and some guys tell me that linux dont accept RAID... 

What the easiest way to put this work with raid and detect my windows8?

---

### Post by darkod on 2012-12-26
Depending which version you want to install.

For fakeraid (bios raid) you need to use the Alternate Install CD. It's a different ISO image than the standard desktop live cd. The installer is text based, but it has better support for raid.

But in the latest 12.10 version, there is no alternate ISO to download. Only up to 12.04 LTS. If you want to install the 12.04 LTS, you can get the alternate ISO.

For 12.10 there is no alternate ISO, but you should be OK installing from the live cd, and if grub2 doesn't install at the end, you can add it later. Just make sure you get enough information about the procedure, so you know what to do if it comes to that.

---

### Post by ronparent on 2012-12-28
Further information on installing 12.10 to a fakeRAID (and this is not probably a good venture for a noob).
 
Unlike for prior versions of Ubuntu, I couldn't do it. The failure to install grub also terminated the install process and left it in a state in which I couldn't isolate a solution to make it runnable. I finally resorted to simply copying a 12.10 install from a usb stick to the RAID. You need to install dmraid and edit fstab of the now RAID install to cite the uuid of the raid partition you copied it to. Then after doing an update-grub on the usb stick to boot into the RAID install you can easily grub-install once booted to the RAID drive leaving you able to boot either win 8 or Ubuntu. As you can see it is all simple and fast once you work it out but no job for a noob without patient and explicit guidance.

---

