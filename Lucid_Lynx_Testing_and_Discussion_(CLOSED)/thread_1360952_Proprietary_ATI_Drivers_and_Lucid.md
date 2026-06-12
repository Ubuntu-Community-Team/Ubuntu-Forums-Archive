---
title: "Proprietary ATI Drivers and Lucid"
date: 2009-12-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by PGHammer on 2009-12-21
I'm going to make it plain if you even have a thought about the proprietary ATI drivers with Lucid (even those from the repos).

Don't.

The drivers from the repos don't match up with the current kernel well (in fact, there is no DKMS module available), and downloading the 9.12s and building them yourself results in the same issues.  Therefore, if you must have 3D or any sort of game-worthy 2D, stick to Karmic for now.

While Lucid *is* faster than even Karmic in terms of 2D, it's still not 3D, and therefore still not worth testing at this point if either 3D or gaming is a must.

---

### Post by zika on 2009-12-21
> **PGHammer said:**
> I'm going to make it plain if you even have a thought about the proprietary ATI drivers with Lucid (even those from the repos).

Don't.

The drivers from the repos don't match up with the current kernel well (in fact, there is no DKMS module available), and downloading the 9.12s and building them yourself results in the same issues.  Therefore, if you must have 3D or any sort of game-worthy 2D, stick to Karmic for now.

While Lucid *is* faster than even Karmic in terms of 2D, it's still not 3D, and therefore still not worth testing at this point if either 3D or gaming is a must.Did You try Lucid with FOSS drivers from xorg-edgers (ppa)? Alone or with 2.6.32-996 (drm-next) or with 2.6.33-{999,rc1} it gives very good 3D as far as I've tried. I'm not a gamer so I might be wrong.

---

### Post by PGHammer on 2009-12-21
> **zika said:**
> Did You try Lucid with FOSS drivers from xorg-edgers (ppa)? Alone or with 2.6.32-996 (drm-next) or with 2.6.33-{999,rc1} it gives very good 3D as far as I've tried. I'm not a gamer so I might be wrong.

No; I have not.  Xorg-edgers seems heavily biased toward HD48xx and above, and I have HD3450 (for now).  Maybe after I upgrade the GPU hardware (or Lucid moves further into the process) I might be willing; however, for now (if you need 3D), I'd still recommend sticking to Karmic.

I will say that Lucid's 2D driver performance is faster than Karmic has ever been (and that is any build of Karmic).

---

### Post by zika on 2009-12-21
> **PGHammer said:**
> No; I have not.  Xorg-edgers seems heavily biased toward HD48xx and above, and I have HD3450 (for now).  Maybe after I upgrade the GPU hardware (or Lucid moves further into the process) I might be willing; however, for now (if you need 3D), I'd still recommend sticking to Karmic.

I will say that Lucid's 2D driver performance is faster than Karmic has ever been (and that is any build of Karmic).I'm using it on ATI HD3650. Never turned back once I've installed it before Karmic testing ... Even in rough times without 3D. Now it is very fast.

---

### Post by PaulInBHC on 2009-12-21
I'm running a Radeon 7000 64mb with xorg-edgers. Don't think it's biased. But what do I know.

---

### Post by andrek on 2009-12-22
It's not entirely ubuntu's lucid fault, same happens on Arch linux. The reason of the failure is xserver version 1.7 which doesn't seem to work with fglrx drivers. I do have working ubuntu lucid box with ati proprietary drivers - I just had to downgrade all the xserver-related packages to the karmic ones.

---

### Post by YosefKaro on 2009-12-22
Everything was working just fine for me right up to Alpha 1 then my machine would only boot up into low-graphics mode.  My graphics is an ATI Radeon X1200.

-Yos

---

### Post by Gina on 2009-12-22
I have a pre-Alpha install on my P4 with ATI Radeon X740XL graphics which I've upgraded with **sudo apt-get update && sudo apt-get upgrade** and up-to-date.  I still have about a dozen packages held back but Lucid is working - I'm using it now :)

---

### Post by PGHammer on 2009-12-22
> **Gina said:**
> I have a pre-Alpha install on my P4 with ATI Radeon X740XL graphics which I've upgraded with **sudo apt-get update && sudo apt-get upgrade** and up-to-date.  I still have about a dozen packages held back but Lucid is working - I'm using it now :)

I didn't say that ATI graphics won't work *at all* with Lucid, as that's certainly not true.  I'm saying that Catalyst for Linux won't work with an as-shipping Lucid (or even an updated Lucid) because of various differences that are PenguinCatalyst-unfriendly.  For instance, I'm using 2.6.33rc1 (newer than alpha-1 kernel that the devs deliberately skipped; it's in kernel PPA) but with radeon driver from xorg-edgers PPA.  I haven't dared try the 3D (HD3450 with anything but PenguinCatalyst has always had issues); however, the 2D performance is the fastest I've ever seen (not merely faster than the old 2D from Karmic, but faster than PenguinCatalyst as far back as Intrepid Ibex, let alone Jaunty).  I may yet try the 3D and see what happens (though I'm expecting it to fail).

---

### Post by Zel Rai on 2009-12-29
Hmm actually on the 3D end, applications that support Mesa-glx seem to have decent enough frame rates with the Xorg drivers.  

Also of note, there appears to be no noticeable difference in frame rate on 2D SDL apps. I tested about a half dozen small SDL games between Karmic with the proprietary drivers and Lucid with the Xorg and found the frame rates to be about the same.

As for hardcore 3D apps, VMWare Player, amd Wine software that require 3d, I've had -zero- luck.

---

### Post by Pipps on 2010-01-01
I have attempted to perform the panel update to the automatically suggested 'ATI/AMD proprietary FGLRX graphics driver', today. It failed. I could not reboot subsequently. I had to reinstall Lucid.

On the basis of PGHammer's kind advice, would it be correct to conclude that installation of the ATI/AMD drivers should not even be attempted?

---

### Post by QIII on 2010-01-02
I wouldn't even bother with the ATI/AMD drivers for now, unless you want a lot of frustration.

I've been working with this issue with Lucid to no avail.  It's not a bug in Lucid.  It's a simple matter of a driver that does not play well with the current X server.  Yet.

At this point, I was able to hand-roll an xorg.conf that gets my monitors in the right places with the right resolutions, but no 3D without an ATI driver.

Similar things happened when I first started testing Karmic.   Lucid is only in testing.  It is not a final release, and it will take a bit of work for ATI/AMD, X, Gnome and Canonical to get all married up.

So I wouldn't despair.  ATI made a concerted effort to get out a version of Catalyst that would work with Karmic before the final release.  Since Ubuntu is so popular, I imagine they will do the same this time.

However, one must remember that ATI/AMD is trying to take money and they have to consider the cost of creating the drivers against their bottom line.

---

### Post by Pipps on 2010-01-02
Thank you for the reassurance.

Though would AMD really seek to take commercial advantage as a result of Linux users simply wishing to collectively obtain (via the Ubuntu repositories) the drivers in a superior (ie Linux) format?

---

### Post by QIII on 2010-01-02
AMD/ATI has come a long way in the last year in supporting Linux.  They have really made a concerted effort.  They got tired of looking at nVidia's back side and decided to catch up.

For Karmic in particular, they pulled out all the stops to create Catalyst 9.10 specifically to get it in the Karmic repos.  It wasn't until after that (an Alpha, by the way) that they made the drivers available for public Linux consumption.

The question is this:  If 98% of your customers use your hardware on machines running Windows, where do you think you are going to put 98% of your driver development effort?  What makes good business sense?

nVidia saw the opportunity and moved into the Linux support world early on.  AMD/ATI sniffed at the "upstart" OS.  No more.

---

### Post by Pipps on 2010-01-02
That is fascinating news and incredibly encouraging to hear! Thank you! :)

---

### Post by QIII on 2010-01-02
Encouraging for those of us already sold on Linux -- especially when I can test the development version because I am an old hand and still remember how to write an xorg.conf file from scratch.

Not so encouraging, perhaps, for someone who tried an early Alpha of Karmic and decided, based on the AMD/ATI driver issue, that Ubuntu was a disaster (and will forever have that opinion).

Sigh.

---

### Post by markbuntu on 2010-01-08
Well, noobs should not be using alphas anyway since they are prone to creating all sorts of disasters. 

Anyway, ati is a little slow getting drivers out that work with new kernels and new xorgs. I think they are a little taken aback at the speed of development with linux, ie new kernels and display managers every 6 months or less instead of every three or four years that is the windows and mac development cycles. Nvidia also has trouble keeping up sometimes and they give zero support for the foss noveau driver.

ATI does have people on their payroll exclusively dedicated to both the proprietary and foss linux drivers along with people at novell working on the radeonhd driver but they have a large backlog of work with the older cards and a lot of work with the new generations of cards flying out of the ati pipeline. Progress over the last year has seen very encouraging with the foss drivers and the prop drivers as well.

---

### Post by zika on 2010-01-08
[Maybe this would be interesting reading...](http://www.phoronix.com/forums/showthread.php?t=21294)

---

### Post by woodnymph on 2010-01-09
i was running lucid fine until yesterday's update .. screen would not turn off at shutdown, machine froze and had to hard power off.  any fix ideas?

ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

---

### Post by lavinog on 2010-01-11
> **woodnymph said:**
> i was running lucid fine until yesterday's update .. screen would not turn off at shutdown, machine froze and had to hard power off.  any fix ideas?

ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

Do NOT install the proprietary drivers for the 200M.
It isn't supported by fglrx.

Does the problem persist after a reboot?

---

### Post by woodnymph on 2010-01-12
> **lavinog said:**
> Do NOT install the proprietary drivers for the 200M.
It isn't supported by fglrx.

Does the problem persist after a reboot?

i have not manually installed any drivers, only what ubuntu includes in updates .. ati, radeon.

actually, i had to de-select all the fglrx packages just to get my resolution back to normal.  got a better way?  am i upside down? .. issue is in lucid only, my hardy box is great.

---

### Post by lavinog on 2010-01-12
> **woodnymph said:**
> 
actually, i had to de-select all the fglrx packages just to get my resolution back to normal.  got a better way?  am i upside down? .. issue is in lucid only, my hardy box is great.

How was lucid installed?  Was it updated from a previous release or was it a fresh install?

---

### Post by zika on 2010-01-12
> **woodnymph said:**
> i have not manually installed any drivers, only what ubuntu includes in updates .. ati, radeon.

actually, i had to de-select all the fglrx packages just to get my resolution back to normal.  got a better way?  am i upside down? .. issue is in lucid only, my hardy box is great.While "de-selecting fglrx packages" did You remove fglrx from Your kernel?

---

### Post by woodnymph on 2010-01-12
> **lavinog said:**
> How was lucid installed?  Was it updated from a previous release or was it a fresh install?

it was a fresh install.

> **zika said:**
> While "de-selecting fglrx packages" did You remove fglrx from Your kernel?

no, just the packages in synaptic .. howto from kernel?  thats new ground for me .. 

also. how would i revert to karmic packages?

---

### Post by zika on 2010-01-12
> **woodnymph said:**
> no, just the packages in synaptic .. howto from kernel?  thats new ground for me ..```
man modprobe
```First, list modules to see if fglrx is loaded. Then just remove it. You shoud have used proprietary script that comes with fglrx to remove it. I suspect You have fglrx module still in kernel.

---

### Post by woodnymph on 2010-01-12
> **zika said:**
> ```
man modprobe
```First, list modules to see if fglrx is loaded. Then just remove it. You shoud have used proprietary script that comes with fglrx to remove it. I suspect You have fglrx module still in kernel.

i dont see anything in the kernel of fglrx

---

### Post by zika on 2010-01-13
> **woodnymph said:**
> i dont see anything in the kernel of fglrxThen You're OK, without fglrx leftovers...

---

### Post by flasa4 on 2010-04-11
I am new on ubuntu i have Ati 4670 but if i install ati drivers from ubuntu repositories ubuntu dont work at all, then i had to erase xorg.conf on /etc/X11 and i have ubuntu working again, why the ati drivers dont work on ubuntu lucid beta2?

---

### Post by napsy on 2010-04-12
Official ATI driver don't support the latest X.Org yet that comes with every new distribution. We, the users, have to be satisfied with the unofficial opensource drivers which are not bad at all but still lack real optimization and full 3D support.

---

### Post by forcecore on 2010-04-15
I just installed Lucid on my desktop pc but can anyone has information when comes Lucid driver or maybe some beta driver at least, i want to test Unigine Heaven on my 3870. Current open driver is fine for multimedia and other but proprietary driver can only handle Unigine.

---

### Post by Ric_NYC on 2010-04-15
I don't know if I changed something... I believe "flglrx" is installed without asking you first.

I noticed it was installed when I started to have problems with hibernating and suspending my laptop. I had problems with it since Jaunty. So I removed it in Karmic.



I'm not buying anything with ATI video cards in the future.

Some ATI cards and fglrx don't get well together.

---

