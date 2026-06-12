---
title: "Kernel 2.6.27-7"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by plun on 2008-10-10
Up and running with no problems  :guitar:

Noticed a DKMS service which was up and running...never seen it before


All details for this kernel:

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008342.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008342.html)

.

---

### Post by executor on 2008-10-10
> **plun said:**
> Up and running with no problems  :guitar:

Noticed a DKMS service which was up and running...never seen it before


All details for this kernel:

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008342.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008342.html)

.

Up and running with no problems her to :)

---

### Post by zoomy942 on 2008-10-10
how can i get it?

---

### Post by jfernyhough on 2008-10-10
If it's not picked up by a System Update, go into Synaptic, update, do a search by name for 27-7 and install linux-image-2.6.27-7-generic, linux-headers-2.6.27-7, linux-headers-2.6.27-7-generic, and linux-restricted-modules-2.6.27-7-generic.

Also running 27-7, all fine.

---

### Post by plun on 2008-10-10
> **zoomy942 said:**
> how can i get it?

It seems to be repo mirror delays for the moment.

I asked a US-user about the same within another thread.

---

### Post by plun on 2008-10-10
> **jfernyhough said:**
> If it's not picked up by a System Update, go into Synaptic, update, do a search by name for 27-7 and install linux-image-2.6.27-7-generic, linux-headers-2.6.27-7, linux-headers-2.6.27-7-generic, and linux-restricted-modules-2.6.27-7-generic.

Also running 27-7, all fine.

The meta package is out...:confused:

I got it automagic...

Perhaps

```
sudo apt-get install linux
```

---

### Post by n6yga on 2008-10-10
No-go for me here in Kalifornia. Synaptic comes back with nada when searched for 27-7


Mark.

---

### Post by dabl on 2008-10-10
Not automatically picked up here in Ohio, either, when I ran upgrade a couple hours ago.  Synaptic shows it available -- I'm going for it!   :guitar:

---

### Post by plun on 2008-10-10
Its strange, this is build record

[https://launchpad.net/ubuntu/+builds?build_text=linux-meta&build_state=built](https://launchpad.net/ubuntu/+builds?build_text=linux-meta&build_state=built)

This is "clearance"

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008448.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008448.html)


Works just fine :)

---

### Post by shane19174 on 2008-10-10
The update just showed up here in Germany...

---

### Post by Kevbert on 2008-10-10
If you want to update it just do a 
```
sudo apt-get dist-upgrade
```
Works fine for me.

---

### Post by Eversmann on 2008-10-10
I have the update there too at the moment (i'm using the general address, not the country one (spanish mirror gives a problem).

On my desktop pc works great. On my advent 4211 netbook broke my wifi (rtl8187se, compiled from a wip driver), no more wireless signal to it.

---

### Post by beartard on 2008-10-10
Have to report that this is the first kernel revision that I've been able to use an nvidia 177 driver for (as opposed to 173).  One more major bug to go and my system will be good to go for release!  ;)

---

### Post by dabl on 2008-10-10
Well I haven't crashed it in 2 hours of screwing around -- I guess maybe it's OK.  Got Nvidia driver 177.80 installed, Firefox plays Youtube. No audio on BBC, but hey that's semi-normal ...

```
dabl@ibex:~$ uname -a
Linux ibex 2.6.27-7-generic #1 SMP Fri Oct 10 03:55:01 UTC 2008 x86_64 GNU/Linux
```

:lolflag:

---

### Post by Nullack on 2008-10-10
Testing is coming along fine for me so far

---

### Post by OutOfReach on 2008-10-10
I got it here. It's all good.

---

### Post by autocrosser on 2008-10-10
Looks good here--using the 177.80 driver also--all golden!!

---

### Post by loomsen on 2008-10-10
Same here, running Intrepid since Alpha 6, didnt experience any problems so far. Well, except my ALSA seems to lack sth since the last update--- But I think I should resolv.conf this until tomorrow evening ;)
```
docter[~] uname -a
Linux doc-laptop 2.6.27-7-generic #1 SMP Fri Oct 10 03:55:01 UTC 2008 x86_64 GNU/Linux
docter[~] 

```
Driver 177.80 here too.

And, what kinda impressed me, you don't need fakeargb for conky anymore. It will now work in gnome without any fake-transparence. 
But, on the other hand, I'm not able to set my fonts up correctly anyhow. 
I use to check full subpixel-smoothing as the very first configuration ever since, but it just won't stay checked here, nor did gconf-editor keep this settings.
Any ideas?

---

### Post by jerrylamos on 2008-10-10
No better, no worse on this IBM Thinkpad R31.  I installed it by booting from the initial Beta install image in recovery mode, then Fix Broken Packages updated & upgraded tons including 2.6.27-7.  

Compiz is still broken altogether, daily build 20081010 won't install, Firefox fonts get polluted, Launchpad bugs are entered for the biggies.

Jerry

---

### Post by gtdaqua on 2008-10-11
2.6.27-5,6,7 are throwing the same ata2.00 "hard resetting the link" error and exits it initramfs prompt. Only 2.6.27-4,3 works for me.

---

### Post by gtdaqua on 2008-10-11
2.6.27-5,6,7 are throwing the same ata2.00 "hard resetting the link" error and exits it initramfs prompt. Only 2.6.27-4,3 works for me.

---

### Post by Victormd on 2008-10-11
For me everything is working great! Only thing was that I had to use Nvidia driver version 173. Ver 177 didn't like the screensaver on my comp.

---

### Post by tron^qld on 2008-10-11
Just updated to 27-7 and found my wired connection won't establish, searches for an IP (I run DHCP here at home) and I am running a RTL8101E/RTL8102E chipset. Any ideas or should I be bringing this up in launch pad.

I am running an MSI Wind U100 802.11 b/g

PS I am having to go back to the 27-4 Kernel to get here...

Thanks
tron^qld

---

### Post by davidyu on 2008-10-11
Wireless still NG to connect after upgrade to 2.6.27-7.
So I have revert to 7.6.27-4

My environment:
Thinkpad T40
Atheros wireless

New update on 10/18,
Now my Atheros wireless works now.
What I do ?
1. At first, Deactive my Atheros driver from /System/Administration/Hardware Drivers
2. Then reboot the Ubuntu
3. re-active Atheros driver.

---

### Post by mycoted on 2008-10-13
2.6.27-7 fails on boot for me, appears to hang when checking wireless card. reverted to 2.6.27-6 which is fine.  (Gateway laptop)

---

### Post by TheFinePrint on 2008-10-13
Using -5 to be able to boot with LUKS-setup (unable to enter password, and unable to read keyfile from usb).

---

### Post by David D. on 2008-10-13
All except the Broadcom wifi is working on my HP laptop (AMD64) with Kernel 2.6.27-7.  This kernel does not detect it, and there is no selection for the driver in Hardware Drivers.

The Broadcom is detected and works with Kernel 2.6.27-6.

Is it a good assumption that this will be fixed by the time the final 8.10 is distributed?

---

### Post by philinux on 2008-10-13
> **David D. said:**
> All except the Broadcom wifi is working on my HP laptop (AMD64) with Kernel 2.6.27-7.  This kernel does not detect it, and there is no selection for the driver in Hardware Drivers.

The Broadcom is detected and works with Kernel 2.6.27-6.

Is it a good assumption that this will be fixed by the time the final 8.10 is distributed?

It might if you or someone with the same wifi card raises a bug report at launchpad.

---

### Post by David D. on 2008-10-13
I have submitted bug report number 282691 on this issue.

---

### Post by mycoted on 2008-10-13
mine is Ok and working with the latest updates now

---

### Post by ol3ears on 2008-10-14
27-7-generic Fails to boot for me. Hangs on 'loading hardware drivers'. 27-4 boots most of the time (though I have nospash, highres=off and nohz=off). Tried these with 27-7 and still no joy

AMD quad core 9550 with gigabyte MA790X-DS4 motherboard, nvidia GEForce 7900GT/GTO graphics card and a tv card - i386 build.

edit: which log do you look at to see why previous boot attempts failed?

---

### Post by Slug71 on 2008-10-14
Im guessing there will probably be a .27-8 before Kernel freeze in a couple of days. Hopefully that will most of the problems some of you are having with .27-7.

---

### Post by plun on 2008-10-14
> **ol3ears said:**
> 
AMD quad core 9550 with gigabyte MA790X-DS4 motherboard, nvidia GEForce 7900GT/GTO graphics card and a tv card - i386 build.

edit: which log do you look at to see why previous boot attempts failed?

TV cards can be a real "killer"....  are you running latest BIOS ?

This is the wiki for kernel bugs

[https://wiki.ubuntu.com/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeamBugPolicies)

---

### Post by ol3ears on 2008-10-16
Thanks for your suggestions - the most recent set of Ubuntu updates appear to have fixed the problem. Gnome now seems to run faster as well :-)

---

### Post by Hideaki on 2008-10-16
I would be nice to have an official fix to this issue: [http://ubuntuforums.org/showthread.php?t=849395](http://ubuntuforums.org/showthread.php?t=849395)

With Ubuntu 8.10. Right now, ASUS G1Sn users and people with similar laptops need to recompile their kernel to get the nVidia driver working.

---

