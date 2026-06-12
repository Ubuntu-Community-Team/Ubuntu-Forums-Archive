---
title: "ATI Catalyst 8.9 Released, still no support for Xorg 7.4"
date: 2008-09-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bpl07 on 2008-09-17
Looks like intrepid won't ship with a working proprietary driver for ati cards.

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by olskar on 2008-09-18
](*,):(

---

### Post by Sand &amp; Mercury on 2008-09-18
Nice going ATI...

[IMG]http://img528.imageshack.us/img528/60/suicidebp5.gif[/IMG]

---

### Post by eyelessfade on 2008-09-18
I still have the screen corruption with wine. Reverting back to 8.4 *shug*
This is why I have nvidia on my main computer, which also run Ubuntu 8.10.
AMD if you read this. I will _never_ buy a ati card before you gets your drivers at least on pair with nvidia.

---

### Post by thonuz on 2008-09-18
I'm having the same problem on a Toshiba laptop with ATI 3100. An ATI driver automatically installed though, but no compiz on 64. I guess this driver is no good then. Surely there must be a work around for this as going back to 8.4 means no wired or wireless without lots of tweaking.

---

### Post by pro003 on 2008-09-18
new ati driver? is there any difference from previous version?

---

### Post by olskar on 2008-09-18
Well, new fglrxdriver to be correct.

Here is list of changes:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html#194695%22](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html#194695%22)


EDIT:

Or check here for a nicer review of the changes
[http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_89_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_89_linux&num=1)

---

### Post by MadMan2k on 2008-09-18
> **eyelessfade said:**
> 
AMD if you read this. I will _never_ buy a ati card before you gets your drivers at least on pair with nvidia.
well seems like you forgot about the open source radeon drivers which are far beyond what nvidia offers.

Since nvidia will be pretty much ignored when it comes to kernel based modesetting. Ati on the other hand has already something working:
[http://airlied.livejournal.com/62269.html](http://airlied.livejournal.com/62269.html)

---

### Post by pro003 on 2008-09-18
> **olskar said:**
> Well, new fglrxdriver to be correct.

Here is list of changes:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html#194695%22](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html#194695%22)


EDIT:

Or check here for a nicer review of the changes
[http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_89_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_89_linux&num=1)

I asked for some personal experience not links of the release notes, but anyway...I installed it few minutes ago... choppy video is still the main problem for my ubuntu...

---

### Post by olskar on 2008-09-18
They still have a chance to release a driver that fixes these problems, Ubuntu 8.10 is 30:th October and next driver will probably come somewhere between 17:th and 22:th?

---

### Post by eyelessfade on 2008-09-18
> **MadMan2k said:**
> well seems like you forgot about the open source radeon drivers which are far beyond what nvidia offers.


When the ati free drivers are working properly I would buy ati yes. But at the moment not even the closed drivers work. :(

---

### Post by gnomeuser on 2008-09-18
> **eyelessfade said:**
> When the ati free drivers are working properly I would buy ati yes. But at the moment not even the closed drivers work. :(

Not working, strange I have been using them for years to great success. The support is rapidly expanding to more models. 

I am very happy to support a company that actively works to support me. ATI have released specifications and they pay people to work on the free software drivers with the community. I am happy to reward that.

---

### Post by Mazza558 on 2008-09-18
> **olskar said:**
> They still have a chance to release a driver that fixes these problems, Ubuntu 8.10 is 30:th October and next driver will probably come somewhere between 17:th and 22:th?

It's going to be very tight. That leaves a maximum of 2 weeks to make sure the ATI driver actually works. Maybe we won't get fglrx until the actual final release this time.

---

### Post by plun on 2008-09-18
Santa Claus  :)

[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007124.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007124.html)

> Description: 
 fglrx-amdcccle - Catalyst Control Center for the ATI graphics accelerators
 fglrx-kernel-source - Kernel module source for the ATI graphics accelerators
 fglrx-modaliases - Identifiers supported by the ATI graphics driver
 xorg-driver-fglrx - Video driver for the ATI graphics accelerators
 xorg-driver-fglrx-dev - Video driver for the ATI graphics accelerators (devel files)
Launchpad-Bugs-Fixed: 266956
Changes: 
 fglrx-installer (2:8.532-0ubuntu1) intrepid; urgency=low
 .
   * Add debian/kernel-source-patches/fglrx_8.9_2.6.27.patch
     to allow compiling against 2.6.27. (LP: #266956)
   * debian/dkms.conf.in:
     - Use 2.6.27 patch when building against 2.6.27
   * debian/fglrx-kernel-source.install.in:
     - Install patches in kernel-source-patches.


---

### Post by olskar on 2008-09-18
> **plun said:**
> Santa Claus  :)

[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007124.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007124.html)

:confused:

What? How does this work without xorg 7.4 support? Can someone explain? :)

---

### Post by plun on 2008-09-18
> **olskar said:**
> :confused:

What? How does this work without xorg 7.4 support? Can someone explain? :)

I am "nVidia freak" so I don't know  :lolflag:...apparently its a patched installer.

---

### Post by Mazza558 on 2008-09-18
> **plun said:**
> Santa Claus  :)

[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007124.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007124.html)

Yay!

So is this coming very soon?

---

### Post by bpl07 on 2008-09-18
> **Mazza558 said:**
> Yay!

So is this coming very soon?

The installer is being packaged, but that doesn't mean it will work with xorg7.4/xserver1.5.  Here's the bug report, which hasn't been updated:

[https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/247376](https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/247376)

---

### Post by Mazza558 on 2008-09-18
> **bpl07 said:**
> The installer is being packaged, but that doesn't mean it will work with xorg7.4/xserver1.5.  Here's the bug report, which hasn't been updated:

[https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/247376](https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/247376)

So why is it being packaged if it's not going to work?

---

### Post by olskar on 2008-09-18
> **Mazza558 said:**
> So why is it being packaged if it's not going to work?

No, that is not nice, getting our hopes up like that :(

---

### Post by InfinityCircuit on 2008-09-18
They want it to compile against 2.6.27 for people who are using Hardy's xorg in Intrepid.

---

### Post by Nikos.Alexandris on 2008-09-18
Finally, I got pivot working on external monitor under Hardy :D
I also got direct rendering in "clone mode".

ATI X1250, ati proprietary driver 8.9, setting ```
aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"
``` as suggested in [1]

Pivot works best for me using the grandr tool. One thing that is annoying is that when turning off the laptop display and using the full screen rotated "left" external monitor, refreshing (rendering?) is very slow.

[1] [http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_89_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_89_linux&num=1)

---

