---
title: "Natty upgrade and live CD hangs on sandy bridge"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by guillemsola on 2011-04-29
Hi,

I have an i5 sandy bridge PC with a gigabyte H67M mobo. I have been running maverick amd64 till yesterday. On maverick graphic acceleration didn't work so I decided to upgrade.

After upgrade my computer hangs during bootup (with ubuntu logo on screen). I cannot see messages on screen, wasn't ESC key for that?

Live CD seems to boot but also hangs computer after loading purple login wallpaper before login dialog is shown.

To me it seems a graphic card regression issue since intel mobo graphic card wasn't working fine on maverick too.

Also tried to manage with fail-safe graphic mode but this also hangs computer.

So I'm stuck here. What should I do next? is there any log where I can see errors during last bootup from maverick live-cd?

Thanks in advance

---

### Post by granjerox on 2011-05-02
Same problem here. Same MOBO same Micro. In maverick i got it working with kernel 2.6.37 and special intel drivers from intel-edge repo. But since i tried to upgrade .... i'm literaly out of linux.

---

### Post by guillemsola on 2011-05-02
Yes, same happened to me. :confused:

I guess is something related to intel video driver, because I can make system work in console mode but never do a startx even in fail-safe mode.

Once xserver starts system froze and nothing else works. Cannot se other consoles, not PetSis + RSEIUB....

Don't know if maybe a newer kernel will do the trick or PPA intel drivers for natty are available.

It's very annoying a brand new computer with no linux!

---

### Post by mebunto on 2011-05-02
Yes, me too I have the GA-H67MA-UD2H mb with an Core I7 processor.  I can just about manage to achieve a successful installation however I get a variety of hangs and crashes when I try to use it.   I'm not getting many ideas back from "the community" which is very frustrating as 11.04 was supposedly fixing the problems that we had with 10.04 - but at least 10.04 runs even if it doesn't exploit the chipset properly.  (see my other thread on this forum)

---

### Post by guillemsola on 2011-05-02
I'm a regular linux user since 2005 an never seen a regression like this.

I'm planning filling a ticket on launchpad but I guess that those drivers arw developed by intel so maybe intel video mailing list should be a better place. But probably those guys prefer tests with latest kernel.

Unfortunately I don't have spare time right now.

---

### Post by lammy on 2011-05-03
Hi all, quite new to all of this and have found the same thing:
using I7 Core with onboard GPU and Gigabyte H67MA-D2H.
Found that by going through the upgrade process from 10.10 I could at least get into safemode with reasonable graphics.
Would be interested to know if you have had any further luck with this.

---

### Post by granjerox on 2011-05-03
The only way I've succeeded untill now to get direct rendering and Compiz working is in Ubuntu 10.10 (Maverick) with kernel 2.6.37 this way. In Natty nothing at all :(

kernel :[ http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.37.6-natty/")

```
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/linux-image-2.6.37-02063706-generic_2.6.37-02063706.201103281005_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.37.6-natty/linux-image-2.6.37-02063706-generic_2.6.37-02063706.201103281005_amd64.deb")
sudo dpkg -i linux-image-2.6.37-02063706-generic_2.6.37-02063706.201103281005_amd64.deb

``````
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-add-repository ppa:jools/sandybridge
sudo apt-get update
sudo apt-get upgrade
```

```
sudo apt-get install libgl1-mesa-dev  libva-glx1 libdrm-intel1 libdrm-dev
```

```
lsb_release -a && glxinfo |grep render && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Desktop GEM 20100330 DEVELOPMENT 
2.6.37-02063706-generic
```
I've tried with kernel 2.6.38 with no luck.

---

### Post by guillemsola on 2011-05-03
> **granjerox said:**
> The only way I've succeeded untill now to get direct rendering and Compiz working is in Ubuntu 10.10 (Maverick) with kernel 2.6.37 this way. In Natty nothing at all :

At least is a way to recover your system.

I can still boot with 2.6.37 because I did an upgrade rather than a clean install.

---

### Post by mebunto on 2011-05-03
I've done most of that too - I don't think I've got the mesa drivers, although I spent quite some time trying to find them, and I'll check/install if necessary.
I agree 10.10 is fine and my machine is stable and performs well; I like to keep the latest releases, just for curiosity's sake and I'm glad that I didn't trash the 10.10 with this new release, and instead just got a new HDD.
My real frustration is that there seems to be no useful information whatsoever on this subject.  I can't find the appropriate bug reports, nor can I find a way of getting some decent information to report a bug myself.  I would have hoped for something by now.
By the way, the H67 motherboard is fantastic, I run two monitors (one at 2560x1600) even though I have to boot with a single monitor then connect an active displayport-DVI adaptor once logged in, due to an obscure startup error supposedly fixed in 11.04.  Everything on a single motherboard, just what I wanted!  Getting 11.04 working would be the icing on the cake.

---

### Post by corevalue on 2011-05-04
Microstar CR720 laptop, i5 processor, no installed OS. Hangs on the splash screen as other have noted with Natty. Keyboards doesn't respond so ctrl-alt-del doesn't work.

---

### Post by mebunto on 2011-05-04
I've noticed a few updates coming through by going to recovery console.  But when I reboot it's still not working.

---

### Post by bnice7 on 2011-05-07
I'm in sort of stuck in the same boat -- i5 2500k sandy bridge CPU, Asus H67 mobo, still running maverick.  I had edgers drivers installed but when I tried to upgrade to 11.04 I uninstalled them because I thought they were what was causing me to get "could not calculate upgrade" errors.  Now I can still boot into 10.10, but only into a pink screen with unusable graphics.  Still can't calculate upgrade to 11.04.

---

### Post by guillemsola on 2011-05-07
You probably installed more than the xorg-edgers ppa? So that's the reason your system could not calculate upgrade...

Anyway don't upgrade to 11.04 with this mobo or you're system will freeze on xorg boot.

I guess that 10.04 with ppa's is the only option right now.

---

### Post by granjerox on 2011-05-17
any news?

---

### Post by guillemsola on 2011-05-19
> **granjerox said:**
> any news?

and future seems bad too...

[Intel Sandy Bridge On Ubuntu 11.04 Is Still Troubling]("http://www.phoronix.com/scan.php?page=article&item=intel_snb_natty&num=1")

[Whoops, Intel SNB Is Borked At The Last Minute In Linux 2.6.39]("http://www.phoronix.com/scan.php?page=article&item=intel_2639_borks&num=1")

---

### Post by guillemsola on 2011-06-21
After some time I did some more test and expected if some bug fix from ubuntu solves something. Until now no success.

I have tested with newest ubuntu kernels, 3.0 is the latest one I could install, newer ones have some dependencies that natty doesn't provide. Again no success, ubuntu still hangs when desktop power up.

Tested also with newest xorg drivers, because as far as I know intel graphic card doesn't work very well with oldest drivers. Again no success.

I have seen that I can boot in safe mode, so there is something that regular version loads that completly freezes system. Is there any log I could see after a freeze? Maybe I need to boot from an external system to prevent logs being rewrite on next bootup?

Also tried fedora 15 and now has become my linux distro on this sandy bridge computer. Fedora 15 works quite well with sandy bridge despite that graphic acceleration doesn't work so there's no gnome 3 experience.

Regards

---

