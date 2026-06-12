---
title: "How to manually remove old kernels?"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by ratcheer on 2010-10-20
I did a "dirty install" of Maverick over my existing Lucid system. That went very well and I am having no problems with Maverick.

However, this morning, I decided to clean off the old Lucid kernels. In the past, after installing a new kernel on the same Ubuntu release, I have done this by running "aptitude search 2.6.32-24", for example, then running "sudo aptitude purge" for the kernel and header files it found.

Now that I have changed releases, aptitude no longer finds the Lucid kernels installed on my system, even though they still reside in the file system and show up on the grub2 menu. So, how do I manually find  everything necessary to delete for the old Lucid kernels?

Tim

---

### Post by realzippy on 2010-10-20
Use
**apt-cache search** 
instead of
aptitude search
,which is no longer installed by default btw.

---

### Post by sikander3786 on 2010-10-20
Or you can install aptitude if you prefer.

```
sudo apt-get install aptitude
```

---

### Post by ratcheer on 2010-10-20
Oh, I installed aptitude the first thing after installing 10.10. It is just about the only package manager I ever use.

I will try the apt-cache search, though.

Thanks.

Tim

---

### Post by ratcheer on 2010-10-20
Nope, apt-cache doesn't find it, either.

Back to the original question - how to find all the parts of the old Lucid installations, manually?

Tim

---

### Post by drs305 on 2010-10-20
I recommend Ubuntu-Tweak. Here is a short thread about removing kernels:
[http://ubuntuforums.org/showthread.php?t=1587462]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by ratcheer on 2010-10-20
> **drs305 said:**
> I recommend Ubuntu-Tweak. Here is a short thread about removing kernels:
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

Thank you. I am looking at it, now.

Tim

---

### Post by psusi on 2010-10-20
If you don't have the packages installed, but rather just have leftover files from a previous install, then the package manager can not help you.  You will need to delete the leftover files manually.

---

### Post by ratcheer on 2010-10-20
No luck, apparently. I installed the latest stable version of Ubuntu Tweak, started it, selected Clean Packages, then Clean Kernels, then Unlock and entered my password. It does not show the Lucid kernels as available for removal, i.e., nothing is displayed.

Tim

---

### Post by ratcheer on 2010-10-20
> **psusi said:**
> If you don't have the packages installed, but rather just have leftover files from a previous install, then the package manager can not help you.  You will need to delete the leftover files manually.

That is what I have been asking. Where do I find all the old files so I can remove them, manually?

Tim

---

### Post by psusi on 2010-10-20
> **ratcheer said:**
> That is what I have been asking. Where do I find all the old files so I can remove them, manually?

Tim

In /boot and /lib/modules.

You might open synaptic and click on a kernel that you DO have installed, and look at the files it consists of.

---

### Post by ratcheer on 2010-10-20
Ok, it looks like I found most everything.

I ran find / -name '*2.6.32*' > temp.list

then, ls -l `cat temp.list`

This shows /boot, /usr/src/linux-headers-2.6.32-24, /usr/src/linux-headers-2.6.32-24-generic, /usr/src/linux-headers-2.6.32-25, and /usr/src/linux-headers-2.6.32-25-generic.

i assume it is safe to delete all this, then update grub? Not everything in /boot, just the Lucid stuff.

Tim

---

### Post by drs305 on 2010-10-20
> **ratcheer said:**
> i assume it is safe to delete all this, then update grub? Not everything in /boot, just the Lucid stuff.

Tim

Yes it is.

---

### Post by ratcheer on 2010-10-20
Excellent. I deleted everything as per my last post, above, ran update-grub, and rebooted. The grub2 menu now has only the Maverick kernel and, best of all, my system still works.

Thanks very much, everyone!

Tim

---

### Post by realzippy on 2010-10-20
> **ratcheer said:**
> Nope, apt-cache doesn't find it, either.

Back to the original question - how to find all the parts of the old Lucid installations, manually?

Tim
??
```
$ apt-cache search 2.6.32*
linux-backports-modules-alsa-2.6.35-22-generic - Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots.
linux-backports-modules-alsa-2.6.35-22-generic-pae - Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots.
linux-backports-modules-net-2.6.35-22-generic - Linux ethernet modules for version 2.6.35 on x86/x86_64
linux-backports-modules-net-2.6.35-22-generic-pae - Linux ethernet modules for version 2.6.35 on x86
linux-backports-modules-wireless-2.6.35-22-generic - compat-wireless Linux modules for version 2.6.35 on x86/x86_64
linux-backports-modules-wireless-2.6.35-22-generic-pae - compat-wireless Linux modules for version 2.6.35 on x86
linux-ec2-doc - Linux kernel specific documentation for version 2.6.32
linux-ec2-source-2.6.32 - Linux kernel source for version 2.6.32 with Ubuntu patches
linux-headers-2.6.32-305 - Header files related to Linux kernel version 2.6.32
linux-headers-2.6.32-305-ec2 - Linux kernel headers for version 2.6.32 on x86/x86_64
linux-headers-lbm-2.6.35-22-generic - Header files related to linux-backports-modules version 2.6.35
linux-headers-lbm-2.6.35-22-generic-pae - Header files related to linux-backports-modules version 2.6.35
linux-image-2.6.32-305-ec2 - Linux kernel image for version 2.6.32 on x86/x86_64
linux-wlan-ng - utilities for wireless prism2 cards
libdigest-sha-perl - Perl extension for SHA-1/224/256/384/512
linux-wlan-ng-firmware - firmware files used by the linux-wlan-ng driver
linux-wlan-ng-source - linux-wlan-ng driver
rfkill - tool for enabling and disabling wireless devices
prism2-usb-firmware-installer - firmware files for the prism2_usb kernel driver
linux-doc - Linux kernel specific documentation for version 2.6.35
linux-headers-2.6.35-22 - Header files related to Linux kernel version 2.6.35
linux-headers-2.6.35-22-generic - Linux kernel headers for version 2.6.35 on x86/x86_64
linux-headers-2.6.35-22-generic-pae - Linux kernel headers for version 2.6.35 on x86
linux-headers-2.6.35-22-virtual - Linux kernel headers for version 2.6.35 on x86/x86_64
linux-image-2.6.35-22-generic - Linux kernel image for version 2.6.35 on x86/x86_64
linux-image-2.6.35-22-generic-pae - Linux kernel image for version 2.6.35 on x86
linux-image-2.6.35-22-virtual - Linux kernel image for version 2.6.35 on x86/x86_64
linux-source-2.6.35 - Linux kernel source for version 2.6.35 with Ubuntu patches
linux-tools-2.6.35-22 - Linux kernel tools for version 2.6.35-22
linux-tools-common - Linux kernel specific tools for version 2.6.35

```

---

### Post by psusi on 2010-10-20
> **realzippy said:**
> apt-cache search 2.6.32*

Wrong command.  The shell replaces "2.6.32*" with the list of files in the current directory that start with "2.6.32" and that is what you are asking apt-cache to search for.

---

### Post by VMC on 2010-10-20
This topic is brings up a kind of how to do it using one-liners. For example:
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

You can find several topics on the web. Here is the above [discussion]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/").It discusses each command as it builds on another. A good read. Also some good comments.

---

### Post by jcwinnie on 2011-03-24
More issues with TGT (The Grub Transition), perhaps?

Anyway, using root privileges, I edited /boot/grub/menu.lst deleting all the kernels listed that were 2.6.32. I knew that the newer kernel worked for me.

NOTE: Make sure you leave the memtest, which is  at the bottom of the list. 

Then I copied and pasted a 2.6.35 entry that I knew worked (both standard and recovery modes), then changed the older ending (for me 2.6.35-22) to a later version that I knew was installed. 

I did this up to the latest 2.6.35-28 (as of the date of this post), then saved menu.lst and re-booted. Now I am running the current kernel. 

This approach is a carryover from earlier Ubuntu versions; so, if you updated and did not do a fresh install, then this approach might work. Good Luck, Jim!

---

### Post by KegHead on 2011-03-24
Hi!

I agree with Ubuntu Tweak.( I've used it for years!)

It works everytime for me!

KegHead

---

