---
title: "How to make sure I have the latest kernel on Ubuntu 14.04"
date: 2014-12-20
forum: Installation &amp; Upgrades
---

### Post by amazingDentist on 2014-12-20
I have Ubuntu 14.04.1 on my Lenovo G50-70 laptop, installed over the OEM Windows 8.1 OS.
The first big problem I noticed was the unstable WIFI, and came to find out through web searches that my laptops Realtek rtl8723be adapter was incompatiable or something.
So I tried a few workarounds and quick fixes, but none of them worked.
Eventually I found a tutorial for manually installing kernel version 3.16 on Ubuntu 14.04, which had come default with version 3.13 (I verified this using command line **uname -r** in Terminal.
Kernel version 3.16 installed succesfully and now I have fully working WIFI with no dropouts or abrupt connection losses.
Finally, no more having to reboot the computer to get back online.

My question though is how do I make sure my new 3.16 kernel is up to date?
I currently have *3.16.0-031600-generic* installed, and so far so good, everything seems tip top.
But I noticed on [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline) that there are versions 3.16.1 through 3.16.7 available.
Do I need to update to the latest one (13.6.7)? Is it stable, with additional improvements?
I'm a linux noob, keep that in mind. 

If it ain't broke don't fix it? Or should I try to get the latest 3.16.7?

---

### Post by grahammechanical on 2014-12-20
Please post the present output of

```
uname -a
```

Keep in mind that you are already ahead of the pack. Ubuntu 14.04 is not scheduled to offically get the Linux 3.16 series kernel until 14.04.2 is released sometime in the early part of the new year. Ubuntu 14.10 already has the 3.16 kernel but at the moment the next release of Ubuntu (15.04, code named Vivid Vervet), still only has kernel 3.16. It is due to get kernel 3.18 sometime soon. This is my output.

> uname -a
Linux sdb8-Roll-Dev 3.16.0-24-generic #32-Ubuntu SMP Tue Oct 28 13:07:32 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux




> lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid




Moving any further ahead will put you in the realm of kernel testing. But it is your choice. Here are 2 threads by those who like to install the very latest kernels but not on their daily work Ubuntu, I am sure.

[http://ubuntuforums.org/showthread.php?t=2254925](http://ubuntuforums.org/showthread.php?t=2254925)

[http://ubuntuforums.org/showthread.php?t=2255835](http://ubuntuforums.org/showthread.php?t=2255835)

Create another partition and install 14.10 or even Vivid Vervet. But keep a stable, unexciting install of 14.04 LTS  just in case things break during the development cycle. They sometimes do.

Regards.

---

### Post by amazingDentist on 2014-12-20
> uname -a
Linux 3.16.0-031600-generic #201408031935 SMP Sun Aug 3 23:36:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

Yep, I very well may be ahead of the pack.
I just wanted to fix my WIFI as quickly and painlessly as possible without having to do anything to extreme.
Did a .deb installation in Terminal that looked a little something like this:

> cd /tmp

$ wget \

kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600_3.16.0-031600.201408031935_all.deb \

kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb \

kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-image-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb 

> sudo dpkg -i linux-headers-3.16*.deb linux-image-3.16*.deb

Followed by a simple reboot.
Then I crossed my fingers and waited. 
It all loaded up fine though, no crashes or error prompts of any kind.
Still haven't tested everything yet, but in the mean time the WIFI seems to be fixed. 
It doesn't lose connection and require constant reboots anymore, so that's good.

Would you recommend not messing with updated versions like 13.16.7?
I definitely don't want to be an unofficial "tester", I just want the latest stable versions of whatever this OS has to offer.

---

### Post by amazingDentist on 2014-12-22
During startup I'm now getting **xxxxxxxxxxx KVM is disable by BIOS** errors, with a bunch of digits where the x's are. (sorry didn't copy them down, not enough time before the OS boots up.
Everything loads up fine. Is there a safe way to get rid of these messages though? Or is there a way to fix this?

---

### Post by fantab on 2014-12-23
Just ignore the message. KVM [Kernel-based Virtual Machine] can be enabled and disabled from your BIOS. If the feature is enabled then you don't get that message.
Its innocuous.

---

