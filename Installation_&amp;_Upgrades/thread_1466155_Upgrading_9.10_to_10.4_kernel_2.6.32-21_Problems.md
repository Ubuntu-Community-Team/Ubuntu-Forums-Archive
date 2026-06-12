---
title: "Upgrading 9.10 to 10.4 kernel 2.6.32-21 Problems"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by fusa on 2010-04-30
When trying to boot to kernel 2.6.32-21 after upgrading from 9.10 to 10.4 I am unable to boot Ubuntu.  It boots fine with kernel version 2.6.31-21.  This occurs even when using the recovery option for kernel version 2.6.32-21.  I do see errors about ext4 not being a recognized file system, even though it worked fine with 9.10 and with the 2.6.31-21 kernel.  I would include log files but am not sure how to since I am completely unable to use the computer after the kernel version is selected in grub.

---

### Post by madmax1735 on 2010-04-30
the new ubuntu 10.4 shifts to kernel modesetting 

if your machine has intel graphics use 

i915.modeset=1 

as an option in grub boot menu

---

### Post by fusa on 2010-04-30
It uses an AMD graphics card, with no on-board video.  Would this or a similar option help?

---

### Post by fusa on 2010-04-30
I was able to boot by adding radeon.modeset=1 to /etc/default/grub.  

But one problem I am having is I get the message "press S to skip mounting, or M for manual recovery" shortly after grub starts booting Ubuntu.   Is there a way to get rid of this?  I have a couple of network drives mount at boot in fstab, sometimes they are booted, sometimes they are not.  Either way I would prefer Ubuntu to complete booting without intervention.

I checked fstab, some of the mount points changed, and after correcting them, I no longer receive this message.

---

### Post by emas80 on 2010-04-30
Hi! I got the same message,  "press S to skip mounting, or M for manual recovery".

But my situation is a little different, I has been using a vanilla recompiled 2.6.33 kernel (without initrd) for months with 9.10 and with Beta 2, but when I installed some updates last tuesday everything broke up and since then I can no longer boot with that kernel, boot sequence stops after that message. 
If I press M, then a root console appears and my data on root partition (that is correctly mounted... it seems strange as it claims that "/ cannot be mounted"!). But my home, that is encrypted and on another partition, is not there..
The system worked PERFECT just before I rebooted. 

Everything is fine with Ubuntu kernel 2.6.32, also after I recompiled it (but with initrd this time). I did not tried using 2.6.32 without inirtd, maybe I will try this weekend.

I think that something is not working pretty well after that update.

---

### Post by FishRCynic on 2010-05-01
add

,nobootwait

to the drive lines in fstab

eg.

defaults,...,nobootwait

and see if that helps

---

