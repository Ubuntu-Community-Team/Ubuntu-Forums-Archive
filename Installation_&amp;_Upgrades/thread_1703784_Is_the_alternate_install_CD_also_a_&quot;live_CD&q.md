---
title: "Is the alternate install CD also a &quot;live CD&quot;?"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by Fraoch on 2011-03-09
Long story short - I'm looking to run a live CD so I can alter my existing 10.10 x64 installation.  The standard desktop install CD results in a graphically corrupted window (a grainy grey field).  The alternate install CD does get me to its text menu, but the shell I open operates on the ramdisk the install CD creates, not the existing hard drives.  I can't seem to get the alternate install CD to do anything to my existing file system.

I'm using the x64 alternate install CD off a USB key.

Short story long - I'm trying to convert from ext3 which I've inherited from upgrading all the way from Warty, to ext4.  I see instructions on how to do it and the best way is using a live CD, so I need to see the existing file system from the live CD via a shell.

As my 10.10 install is working just fine, I'm getting less and less inclined to mess with it at this point, so I may just abandon it.  But I understand ext4 is much faster than ext3, plus I always learn a lot when I go through things like this, so this is just a question before I give up.

Thanks!

---

### Post by oldfred on 2011-03-09
The standard desktop install CDs are the liveCDs. The alternative install is a text only installer.

Often the issue is video card related. Usually liveCD works since it uses a default basic video driver to start with. On my system I had to use nomodeset with my nVidia card.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by YesWeCan on 2011-03-09
No the alternate CD is not a live CD.
I am sure you have already tried this but with the live CD choosing the nomodeset boot option often avoids graphics issues.

[edit] oldfred you beat me to it. :)

---

### Post by Fraoch on 2011-03-10
Thanks for the very quick responses.  Yes, I have an nVidia card, and nomodeset worked perfectly.

There's another issue - some of my drives are in RAID using mdadm, and of course the live CD can't see those.  But that's a matter for another thread.:)

---

### Post by YesWeCan on 2011-03-10
You just need to install mdadm while you are running from live CD. The live CD does not have this installed by default.

---

### Post by Fraoch on 2011-03-10
> **YesWeCan said:**
> You just need to install mdadm while you are running from live CD. The live CD does not have this installed by default.

Thanks again.  I did get that far, but my mdadm.conf is on one of the mdadm-administered partitions so I'm copying it to a regular partition in order to use it.

I believe I can reassemble my mdadm partitions without doing this, but I want to be careful.

---

### Post by Fraoch on 2011-03-10
I made a little progress but haven't got it completely yet, so I'll continue [here]("http://ubuntuforums.org/showthread.php?t=1704258").

I'll mark this thread as solved.

Thank you!

---

